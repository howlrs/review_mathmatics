# 数学I: 図形と計量 (1) 三角比の定義 (Session 13)

**対象**: 社会人エンジニア (Rust/Go)
**学習目標**: 直角三角形における三角比 ($\sin, \cos, \tan$) の定義を理解し、相互関係の公式を使いこなす。これらは2D/3Dグラフィックス、ベクトル解析、信号処理の基礎となる。

---

## Phase 1: Foundational Check (基礎確認 10問)

**指針**: 「困ったときは『定義』に還れ」。直角三角形の辺の比（斜辺、対辺、隣辺）を正確に把握せよ。

1.  **[定義]** 右の図（直角三角形 ABC, $\angle C = 90^\circ$）において、 $\sin A, \cos A, \tan A$ を辺の長さ $a, b, c$ ($a=BC, b=AC, c=AB$) を用いて表せ。
    > **Prog Link**: 単位円上の座標 $(x, y) = (\cos \theta, \sin \theta)$。

2.  **[値の計算]** 直角三角形の3辺が $3, 4, 5$ （斜辺が5）のとき、小さい方の鋭角を $\theta$ とする。 $\sin \theta, \cos \theta, \tan \theta$ の値を求めよ。

3.  **[有名角]** $\sin 30^\circ, \cos 30^\circ, \tan 30^\circ$ の値を答えよ。

4.  **[有名角]** $\sin 45^\circ, \cos 45^\circ, \tan 45^\circ$ の値を答えよ。
    > **Prog Link**: $\sqrt{2}/2 \approx 0.707$。正規化された対角線ベクトル。

5.  **[有名角]** $\sin 60^\circ, \cos 60^\circ, \tan 60^\circ$ の値を答えよ。

6.  **[相互関係]** $\tan A$ を $\sin A, \cos A$ を用いて表せ。
    > **Prog Link**: スロープ（勾配）の計算。 $\Delta y / \Delta x$。

7.  **[相互関係]** $\sin^2 A + \cos^2 A$ の値を答えよ。
    > **Prog Link**: 単位円の方程式 $x^2 + y^2 = 1$。ベクトルの正規化 (Normalization) の基礎。

8.  **[相互関係]** $1 + \tan^2 A$ を $\cos A$ を用いて表せ。

9.  **[余角の公式]** $\sin(90^\circ - A)$ は何に等しいか。
    > **Prog Link**: 直交座標系の回転。 $x$ 軸と $y$ 軸の入れ替え。

10. **[近似値]** $\tan 1^\circ$ はおよそどのような値か。次の中から選べ。
    (a) $0.017$ (b) $0.5$ (c) $1.0$
    > **Tip**: $\theta$ が小さいとき $\tan \theta \approx \theta$ (ラジアン)。 $1^\circ \approx 0.017$ rad。

---

## Phase 2: Applied Mastery (応用・実践 10問)

**指針**: 「条件を使い切ったか確認せよ」。相互関係の式を変形し、未知の値を導き出せ。

11. **[相互関係の利用]**
    $A$ が鋭角で、 $\sin A = \frac{3}{5}$ のとき、 $\cos A, \tan A$ の値を求めよ。
    > **Algorithm**: $\sin^2 A + \cos^2 A = 1$ に代入して $\cos A$ を解く（正の値）。その後 $\tan A$ を計算。

12. **[相互関係の利用]**
    $A$ が鋭角で、 $\tan A = 2$ のとき、 $\cos A, \sin A$ の値を求めよ。
    > **Maxim**: 「複雑な問題は『素因数分解』せよ」。 $1+\tan^2 A = 1/\cos^2 A$ を利用する。

13. **[式の値]**
    $\sin A + \cos A = \frac{1}{2}$ のとき、 $\sin A \cos A$ の値を求めよ。
    > **Tip**: 両辺を2乗する。 $(\sin A + \cos A)^2 = 1 + 2\sin A \cos A$。

14. **[式の値]**
    前問のとき、 $\tan A + \frac{1}{\tan A}$ の値を求めよ。
    > **Logic**: 通分すると $\frac{\sin^2 A + \cos^2 A}{\sin A \cos A}$ になる。

15. **[測量への応用]**
    ある地点から塔の先端を見上げた角度（仰角）が $30^\circ$ であった。塔に向かって水平に $10\text{m}$ 進んだ地点で見上げると $45^\circ$ であった。塔の高さを求めよ。目の高さは無視する。
    > **Prog Link**: 三角測量 (Triangulation)。GPSや3Dスキャナの原理。

16. **[余角の利用]**
    $\sin^2 20^\circ + \sin^2 70^\circ$ の値を求めよ。

17. **[方程式の解]**
    $0^\circ \le \theta \le 90^\circ$ のとき、方程式 $2\cos^2 \theta - \sin \theta - 1 = 0$ を解け。
    > **Algorithm**: $\cos^2 \theta = 1 - \sin^2 \theta$ を代入し、 $\sin \theta$ の二次方程式として解く。

18. **[不等式の解]**
    $0^\circ \le \theta \le 90^\circ$ のとき、不等式 $2\sin \theta < 1$ を満たす $\theta$ の範囲を求めよ。

19. **[最大・最小]**
    $y = \sin^2 \theta + \cos \theta$ ($0^\circ \le \theta \le 90^\circ$) の最大値と最小値を求めよ。
    > **Logic**: $\cos \theta = t$ と置換。 $0 \le t \le 1$ における二次関数の最適化問題。

20. **[立体図形への応用]** (発展)
    1辺の長さが $a$ の正四面体の高さを求めよ。
    > **Visualization**: 頂点から底面に下ろした垂線の足は、底面の正三角形の重心（外心）と一致する。

---

## 解答と解説

### Phase 1

1.  **$\sin A = a/c, \cos A = b/c, \tan A = a/b$**
2.  **$\sin \theta = 3/5, \cos \theta = 4/5, \tan \theta = 3/4$**
    *   小さい角の対辺は小さい辺 (3)。
3.  **$1/2, \sqrt{3}/2, 1/\sqrt{3}$**
4.  **$1/\sqrt{2}, 1/\sqrt{2}, 1$**
5.  **$\sqrt{3}/2, 1/2, \sqrt{3}$**
6.  **$\tan A = \frac{\sin A}{\cos A}$**
7.  **$1$**
8.  **$\frac{1}{\cos^2 A}$**
9.  **$\cos A$**
10. **(a) 0.017**

### Phase 2

11. **$\cos A = 4/5, \tan A = 3/4$**
    *   $\cos^2 A = 1 - (3/5)^2 = 16/25$。鋭角より $\cos A > 0$ なので $4/5$。
12. **$\cos A = 1/\sqrt{5}, \sin A = 2/\sqrt{5}$**
    *   $1 + 2^2 = 1/\cos^2 A \Rightarrow \cos^2 A = 1/5$。
    *   $\sin A = \tan A \cos A = 2/\sqrt{5}$。
13. **$-3/8$**
    *   $1 + 2\sin A \cos A = 1/4 \Rightarrow 2\sin A \cos A = -3/4$。
14. **$-8/3$**
    *   $\frac{1}{\sin A \cos A} = \frac{1}{-3/8} = -8/3$。
15. **$5(\sqrt{3}+1)$ m**
    *   高さ $h$。 $h/\tan 30^\circ - h/\tan 45^\circ = 10$。
    *   $\sqrt{3}h - h = 10 \Rightarrow h(\sqrt{3}-1) = 10$。
    *   $h = \frac{10}{\sqrt{3}-1} = 5(\sqrt{3}+1)$。
16. **$1$**
    *   $\sin 70^\circ = \cos 20^\circ$。 $\sin^2 20^\circ + \cos^2 20^\circ = 1$。
17. **$\theta = 30^\circ$**
    *   $2(1-\sin^2 \theta) - \sin \theta - 1 = 0$。
    *   $2\sin^2 \theta + \sin \theta - 1 = 0 \Rightarrow (2\sin \theta - 1)(\sin \theta + 1) = 0$。
    *   $\sin \theta = 1/2, -1$。範囲より $1/2$。
18. **$0^\circ \le \theta < 30^\circ$**
    *   $\sin \theta < 1/2$。
19. **最大値 $5/4$, 最小値 $1$**
    *   $y = (1-t^2) + t = -t^2 + t + 1 = -(t-1/2)^2 + 5/4$。
    *   $0 \le t \le 1$。頂点 $t=1/2$ で最大 $5/4$。
    *   端点 $t=0 \to 1, t=1 \to 1$。最小値 1。
20. **$\frac{\sqrt{6}}{3}a$**
    *   底面の重心までの距離は、中線の $2:1$ の点。
    *   中線長さ $\frac{\sqrt{3}}{2}a$。重心まで $\frac{\sqrt{3}}{3}a$。
    *   $h^2 + (\frac{\sqrt{3}}{3}a)^2 = a^2 \Rightarrow h^2 = a^2 - \frac{1}{3}a^2 = \frac{2}{3}a^2$。

