# 数学I: データの分析 (4) プロジェクト学習 (Session 22)

**対象**: 社会人エンジニア (Rust/Go)
**学習目標**: これまでに学んだ統計・分散・相関の知識を総動員し、実際のエンジニアリング課題（サーバーログ分析）を解決する。プログラミング言語 (Rust/Go) を用いて大量のデータを処理し、意思決定に役立つ知見を導き出す。

---

## Project Overview: Server Latency Analysis

あなたはWebサービスのバックエンドエンジニアである。
最近、ユーザーから「夜間にアクセスが遅くなる」という報告を受けている。
Webサーバーのアクセスログ（CSV形式）を解析し、レスポンスタイムの傾向と、同時接続数との相関を調査せよ。

### Dataset Specification

以下の形式のCSVデータが与えられる（仮想的に生成せよ）。

```csv
timestamp,response_time_ms,concurrent_users
2023-10-01T00:00:00Z,120,50
2023-10-01T00:01:00Z,135,55
...
```

*   **データ点数**: 1440点（1分ごとの計測、24時間分）
*   **response_time_ms**: レスポンスタイム（ミリ秒）。正規分布に従うランダムノイズを含む。
*   **concurrent_users**: 同時接続数。日中は多く、夜間は少ない（あるいはその逆）トレンドを持つ。

---

## Phase 1: Data Generation & Loading (データ生成と読み込み)

**課題 1. [データ生成]**
Rust または Go を用いて、テストデータを生成するプログラムを作成せよ。
*   `concurrent_users`: 時間帯（0時〜23時）に応じて正弦波状に変化させる（例: $50 + 40 \sin(\dots)$）。
*   `response_time_ms`: `concurrent_users` に比例するベース値に、ランダムなノイズ（平均0、標準偏差20の正規分布など）を加える。
*   生成したデータを `server_logs.csv` として保存せよ。

**課題 2. [データ読み込み]**
保存したCSVファイルを読み込み、構造体の配列（またはスライス/ベクタ）に格納するプログラムを作成せよ。
*   Rust: `struct LogRecord { timestamp: String, response_time: f64, users: i32 }`
*   Go: `type LogRecord struct { ... }`

---

## Phase 2: Statistical Analysis (統計分析)

**課題 3. [基本統計量]**
読み込んだデータについて、`response_time_ms` の以下の値を計算せよ。
1.  平均値 (Mean)
2.  中央値 (Median)
3.  最大値 (Max) / 最小値 (Min)

**課題 4. [分散と標準偏差]**
`response_time_ms` の分散 (Variance) と標準偏差 (Standard Deviation) を計算せよ。
*   公式 $\frac{1}{n} \sum (x_i - \bar{x})^2$ を用いて実装すること。

**課題 5. [外れ値の検出]**
平均値から標準偏差の2倍以上離れている ($|x - \bar{x}| > 2s$) データ点を「外れ値 (Outlier)」として抽出し、そのタイムスタンプと値をリストアップせよ。
*   これは「異常検知 (Anomaly Detection)」の最も単純なアルゴリズムである。

---

## Phase 3: Correlation & Visualization (相関と可視化)

**課題 6. [共分散と相関係数]**
`response_time_ms` ($y$) と `concurrent_users` ($x$) の共分散 $s_{xy}$ と相関係数 $r$ を計算せよ。
*   $r$ の値から、両者の間にどのような関係があると言えるか考察せよ。

**課題 7. [回帰直線]**
`concurrent_users` から `response_time_ms` を予測する回帰直線 $y = ax + b$ の傾き $a$ と切片 $b$ を求めよ。
*   $a = r \frac{s_y}{s_x}$
*   $b = \bar{y} - a \bar{x}$

**課題 8. [可視化（オプション）]**
計算結果をグラフにプロットせよ。
*   横軸: `concurrent_users`, 縦軸: `response_time_ms` の散布図。
*   回帰直線を重ねて表示する。
*   (ASCIIアートでのプロットや、gnuplot/Pythonへのデータ出力でも可)

---

## Phase 4: Engineering Decision (エンジニアリング判断)

**課題 9. [ボトルネックの特定]**
相関係数が高い場合、レスポンスタイムの悪化原因は同時接続数の増加にあると推測できる。
もし相関係数が低い（$|r| < 0.2$ など）にもかかわらず、特定の時間帯だけレスポンスが遅い場合、どのような原因が考えられるか。3つ以上挙げよ。
（例: バックグラウンドでのバッチ処理、DBのバックアップ、外部APIの遅延など）

**課題 10. [改善提案]**
回帰分析の結果、同時接続数が 100 を超えるとレスポンスタイムが許容範囲（例: 200ms）を超えることが予測されたとする。
エンジニアとしてどのような対策をとるべきか。スケーリング（Scale-up / Scale-out）、キャッシュ、非同期処理などの観点から論ぜよ。

---

## 解答と解説（実装ヒント）

### 課題 1 (Rust Example)
```rust
use rand::Rng;
use rand_distr::{Normal, Distribution};
use std::fs::File;
use std::io::Write;

fn main() -> std::io::Result<()> {
    let mut file = File::create("server_logs.csv")?;
    writeln!(file, "timestamp,response_time_ms,concurrent_users")?;

    let normal = Normal::new(0.0, 20.0).unwrap();
    let mut rng = rand::thread_rng();

    for i in 0..1440 { // 24 hours * 60 mins
        let t = i as f64;
        // Users: 50 + 40 * sin(time)
        let users = (50.0 + 40.0 * (t * 2.0 * std::f64::consts::PI / 1440.0).sin()) as i32;
        // Response: Base 100 + 2 * users + Noise
        let noise = normal.sample(&mut rng);
        let response = 100.0 + 2.0 * (users as f64) + noise;
        
        writeln!(file, "2023-10-01T{:02}:{:02}:00Z,{:.2},{}", i/60, i%60, response, users)?;
    }
    Ok(())
}
```

### 課題 6 (相関係数)
*   強い正の相関（$r > 0.7$）が期待される設定である。
*   これにより、「ユーザー数が増えると重くなる」という仮説がデータから裏付けられる。

### 課題 9 (ボトルネック)
*   **Cron Jobs**: 定期実行される重い処理（ログローテーション、集計）。
*   **Cold Start**: サーバーレス環境での起動遅延。
*   **Network Latency**: 外部サービスとの通信経路の問題。
*   **Garbage Collection**: 特定のタイミングで発生するStop-the-world。

### 課題 10 (改善提案)
*   **Scale-out**: サーバー台数を増やし、ロードバランサで負荷分散する。
*   **Caching**: Redis等を導入し、DB負荷を減らす。
*   **Asynchronous**: 重い処理をメッセージキュー（Kafka/SQS）に逃がす。
*   **Indexing**: DBのクエリを最適化する。

