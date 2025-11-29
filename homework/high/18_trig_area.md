# 数学I: 図形と計量 (6) 三角形の面積 (Session 18)

**対象**: 社会人エンジニア (Rust/Go)
**学習目標**: 三角形の面積公式 $S = \frac{1}{2}bc \sin A$ を習得する。また、内接円の半径やヘロンの公式との関連を理解し、ポリゴンの面積計算に応用する。

---

## Phase 1: Foundational Check (基礎確認 10問)

**指針**: 「困ったときは『定義』に還れ」。底辺 $\times$ 高さ $\div 2$ の「高さ」が $b \sin A$ である。

1.  **[基本公式]** $\triangle ABC$ において、 $b=4, c=5, A=30^\circ$ のとき、面積 $S$ を求めよ。
    > **Prog Link**: 外積 (Cross Product) の大きさの半分。 $|\vec{b} \times \vec{c}| / 2$。

2.  **[基本公式]** $\triangle ABC$ において、 $a=6, b=3, C=135^\circ$ のとき、面積 $S$ を求めよ。

3.  **[基本公式]** $\triangle ABC$ において、 $a=2, c=2\sqrt{3}, B=120^\circ$ のとき、面積 $S$ を求めよ。

4.  **[逆算]** $\triangle ABC$ において、 $b=4, c=5, S=5$ のとき、 $\sin A$ の値を求めよ。

5.  **[逆算]** 前問において、 $A$ が鋭角のとき、 $A$ の大きさを求めよ。

6.  **[ヘロンの公式]** 3辺の長さが $3, 4, 5$ の三角形の面積をヘロンの公式を用いて求めよ。 $s = (3+4+5)/2$。

7.  **[ヘロンの公式]** 3辺の長さが $5, 6, 7$ の三角形の面積を求めよ。
    > **Algorithm**: $S = \sqrt{s(s-a)(s-b)(s-c)}$。数値計算ライブラリの実装。

8.  **[内接円の半径]** 3辺が $5, 6, 7$ の三角形の内接円の半径 $r$ を求めよ。
    > **Formula**: $S = \frac{1}{2}r(a+b+c)$。

9.  **[平行四辺形]** 隣り合う2辺の長さが $3, 5$ で、その間の角が $60^\circ$ である平行四辺形の面積を求めよ。
    > **Prog Link**: 行列式の絶対値（2x2行列）。

10. **[正多角形]** 半径 2 の円に内接する正六角形の面積を求めよ。
    > **Visualization**: 6つの正三角形に分割する。

---

## Phase 2: Applied Mastery (応用・実践 10問)

**指針**: 「条件を使い切ったか確認せよ」。面積公式は「長さ」と「角度」をつなぐ強力なハブである。

11. **[面積の最大値]**
    周の長さが 20 の二等辺三角形 ($AB=AC$) の面積が最大になるとき、その形状はどのような三角形か。
    > **Logic**: 底辺 $2x$、等辺 $10-x$。ヘロンの公式で $x$ の関数として最大化。

12. **[四角形の面積]**
    円に内接する四角形 $ABCD$ において、 $AB=2, BC=3, CD=4, DA=3$ のとき、この四角形の面積を求めよ。
    > **Algorithm**: 対角線 $AC$ で2つの三角形に分割。 $\angle B + \angle D = 180^\circ$ を利用。

13. **[四角形の面積（一般）]**
    対角線の長さが $p, q$ で、そのなす角が $\theta$ である四角形の面積 $S$ は $S = \frac{1}{2}pq \sin \theta$ で表されることを証明せよ。
    > **Prog Link**: 任意の四角形メッシュの面積計算。

14. **[内接円と外接円]**
    3辺が $7, 8, 9$ の三角形の外接円の半径 $R$ と内接円の半径 $r$ を求めよ。
    > **Step**: ヘロン $\to S \to r$。 $S = abc/4R \to R$。

15. **[角の二等分線]**
    $\triangle ABC$ において、 $AB=4, AC=3, A=60^\circ$ とする。 $\angle A$ の二等分線の長さを面積法を用いて求めよ。

16. **[空間図形の表面積]**
    底面が1辺 $a$ の正方形、高さが $h$ の正四角錐の側面積を求めよ。

17. **[座標法]**
    3点 $O(0, 0), A(x_1, y_1), B(x_2, y_2)$ を頂点とする三角形の面積が $S = \frac{1}{2}|x_1 y_2 - x_2 y_1|$ であることを、三角比を用いて導け。
    > **Prog Link**: 外積の $z$ 成分。多角形の面積公式（Shoelace Formula）の基礎。

18. **[中線の長さ]**
    $\triangle ABC$ の面積が $6\sqrt{3}$ で、 $AB=4, AC=6$ のとき、中線 $AM$ の長さを求めよ。ただし $A$ は鋭角とする。
    > **Logic**: 面積から $\sin A \to \cos A$。余弦定理で $BC$。中線定理で $AM$。

19. **[面積比]**
    $\triangle ABC$ の辺 $BC$ を $1:2$ に内分する点を $D$、辺 $CA$ を $2:3$ に内分する点を $E$、辺 $AB$ を $3:1$ に内分する点を $F$ とする。 $\triangle DEF$ と $\triangle ABC$ の面積比を求めよ。
    > **Algorithm**: 全体から3つの隅の三角形 ($\triangle AFE, \triangle BDF, \triangle CED$) を引く。

20. **[極限]** (発展)
    半径 $R$ の円に外接する正 $n$ 角形の面積 $T_n$ を求めよ。また、 $n \to \infty$ のとき $T_n$ はどうなるか。

---

## 解答と解説

### Phase 1

1.  **$5$**
    *   $S = \frac{1}{2} \cdot 4 \cdot 5 \cdot \frac{1}{2} = 5$。
2.  **$9\sqrt{2}/2$**
    *   $S = \frac{1}{2} \cdot 6 \cdot 3 \cdot \frac{1}{\sqrt{2}} = \frac{9\sqrt{2}}{2}$。
3.  **$3$**
    *   $S = \frac{1}{2} \cdot 2 \cdot 2\sqrt{3} \cdot \frac{\sqrt{3}}{2} = 3$。
4.  **$1/2$**
    *   $5 = \frac{1}{2} \cdot 4 \cdot 5 \sin A = 10 \sin A \Rightarrow \sin A = 1/2$。
5.  **$30^\circ$**
6.  **$6$**
    *   $s = 6$。 $S = \sqrt{6 \cdot 3 \cdot 2 \cdot 1} = 6$。
7.  **$6\sqrt{6}$**
    *   $s = 9$。 $S = \sqrt{9 \cdot 4 \cdot 3 \cdot 2} = 3 \cdot 2 \sqrt{6} = 6\sqrt{6}$。
8.  **$2\sqrt{6}/3$**
    *   $6\sqrt{6} = \frac{1}{2}r(18) = 9r \Rightarrow r = \frac{2\sqrt{6}}{3}$。
9.  **$15\sqrt{3}/2$**
    *   $3 \cdot 5 \sin 60^\circ = 15\sqrt{3}/2$。
10. **$6\sqrt{3}$**
    *   $6 \times (\frac{1}{2} \cdot 2 \cdot 2 \sin 60^\circ) = 6\sqrt{3}$。

### Phase 2

11. **正三角形**
    *   ヘロンの公式 $s=10$。 $S = \sqrt{10(10-2x)(10-(10-x))^2} = \sqrt{10(10-2x)x^2}$。
    *   $f(x) = 10x^2 - 2x^3$ を最大化。 $x=10/3$。
    *   3辺は $20/3, 20/3, 20/3$。正三角形。
12. **$2\sqrt{30}$** ... 訂正
    *   $\cos B$ を求める。 $AC^2 = 4+9-12\cos B = 13-12\cos B$。
    *   $AC^2 = 16+9-24\cos(180-B) = 25+24\cos B$。
    *   $13-12\cos B = 25+24\cos B \Rightarrow 36\cos B = -12 \Rightarrow \cos B = -1/3$。
    *   $\sin B = 2\sqrt{2}/3$。
    *   $S = \frac{1}{2} \cdot 2 \cdot 3 \sin B + \frac{1}{2} \cdot 4 \cdot 3 \sin B = 3\sin B + 6\sin B = 9\sin B$。
    *   $9 \cdot (2\sqrt{2}/3) = 6\sqrt{2}$。
    *   (計算ミス確認: $S_{ABC} = 3 \sin B$, $S_{ACD} = 6 \sin B$。合計 $9 \sin B$。OK。
    *   答え: $6\sqrt{2}$。
    *   解説修正: **$6\sqrt{2}$**)
13. **証明**
    *   対角線の交点で4つの三角形に分割し、和をとる。
14. **$R=21\sqrt{5}/10, r=\sqrt{5}$**
    *   $s=12$。 $S = \sqrt{12 \cdot 5 \cdot 4 \cdot 3} = \sqrt{720} = 12\sqrt{5}$。
    *   $12\sqrt{5} = 12r \Rightarrow r = \sqrt{5}$。
    *   $R = 7 \cdot 8 \cdot 9 / (4 \cdot 12\sqrt{5}) = 504 / 48\sqrt{5} = 21/2\sqrt{5} = 21\sqrt{5}/10$。
15. **$12\sqrt{3}/7$**
    *   $S = 3\sqrt{3}$。
    *   $3\sqrt{3} = \frac{1}{2}x(4+3)\sin 30^\circ = \frac{7}{4}x$。
    *   $x = 12\sqrt{3}/7$。
16. **$a\sqrt{4h^2+a^2}$**
    *   側面の三角形の高さ $l = \sqrt{h^2 + (a/2)^2} = \frac{1}{2}\sqrt{4h^2+a^2}$。
    *   側面積 $4 \times \frac{1}{2} a l = 2al = a\sqrt{4h^2+a^2}$。
17. **導出**
    *   $S = \frac{1}{2}OA \cdot OB \sin \theta$。
    *   $S^2 = \frac{1}{4} |\vec{a}|^2 |\vec{b}|^2 (1-\cos^2 \theta) = \frac{1}{4} (|\vec{a}|^2 |\vec{b}|^2 - (\vec{a}\cdot\vec{b})^2)$。
    *   ラグランジュの恒等式より $(x_1 y_2 - x_2 y_1)^2$ になる。
18. **$\sqrt{19}$**
    *   $6\sqrt{3} = \frac{1}{2} \cdot 4 \cdot 6 \sin A \Rightarrow 12 \sin A = 6\sqrt{3} \Rightarrow \sin A = \sqrt{3}/2$。
    *   $A=60^\circ$ (鋭角)。
    *   $BC^2 = 16+36-24 = 28$。
    *   $16+36 = 2(AM^2 + 7) \Rightarrow 52 = 2AM^2 + 14 \Rightarrow 2AM^2 = 38 \Rightarrow AM = \sqrt{19}$。
19. **$17/60$** ... 訂正
    *   $S_{AFE} = \frac{3}{4} \cdot \frac{2}{5} S = \frac{3}{10} S$。
    *   $S_{BDF} = \frac{1}{3} \cdot \frac{1}{4} S = \frac{1}{12} S$。
    *   $S_{CED} = \frac{2}{3} \cdot \frac{3}{5} S = \frac{2}{5} S$。
    *   $S_{DEF} = S - (\frac{3}{10} + \frac{1}{12} + \frac{2}{5}) S = S - \frac{18+5+24}{60} S = S - \frac{47}{60} S = \frac{13}{60} S$。
    *   答え: $13:60$。
20. **$nR^2 \tan(\pi/n)$**
    *   $n \to \infty$ で $\pi R^2$ (円の面積)。

