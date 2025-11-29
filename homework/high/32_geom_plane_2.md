# 数学A: 図形の性質 (2) チェバ・メネラウスの定理 (Session 32)

**対象**: 社会人エンジニア (Rust/Go)
**学習目標**: チェバの定理とメネラウスの定理を習得し、線分の比を自在に計算できるようにする。これらはベクトル解析や重心座標系（Barycentric Coordinates）の基礎となる。

---

## Phase 1: Foundational Check (基礎確認 10問)

**指針**: 「困ったときは『定義』に還れ」。一筆書きのルート（頂点→分点→頂点...）を意識せよ。

1.  **[チェバの定理]** $\triangle ABC$ の3頂点と点 $O$ を結ぶ直線が対辺と交わる点を $P, Q, R$ とするとき、成り立つ等式を記述せよ。
    > **Formula**: $\frac{AR}{RB} \cdot \frac{BP}{PC} \cdot \frac{CQ}{QA} = 1$。

2.  **[メネラウスの定理]** $\triangle ABC$ の辺 $AB, AC$ と交わり、辺 $BC$ の延長と交わる直線があるとき、分点 $R, Q, P$ について成り立つ等式を記述せよ。
    > **Formula**: $\frac{AR}{RB} \cdot \frac{BP}{PC} \cdot \frac{CQ}{QA} = 1$ （外分が含まれる点に注意）。

3.  **[比の計算]** $\triangle ABC$ において、 $AR:RB = 2:1, BP:PC = 3:2$ のとき、チェバの定理を用いて $CQ:QA$ を求めよ。

4.  **[比の計算]** $\triangle ABC$ において、 $AR:RB = 1:2, BP:PC = 4:3$ （外分）のとき、メネラウスの定理を用いて $CQ:QA$ を求めよ。

5.  **[内分と外分]** 線分 $AB$ を $2:1$ に内分する点 $P$ と、 $2:1$ に外分する点 $Q$ の位置関係を図示せよ。

6.  **[重心とチェバ]** 重心の場合、チェバの定理の式はどうなるか。
    > **Logic**: 中点なので比はすべて $1:1$。 $1 \cdot 1 \cdot 1 = 1$。

7.  **[内心とチェバ]** 内心の場合、チェバの定理は成り立つか。
    > **Logic**: 成り立つ（角の二等分線は1点で交わるため）。

8.  **[面積比]** 高さの等しい2つの三角形の面積比は何の比に等しいか。
    > **Math**: 底辺の比。

9.  **[逆定理]** チェバの定理の逆「式が成り立てば、3直線は1点で交わる」は成り立つか。

10. **[プログラミング]** 線分 $AB$ を $t : 1-t$ に内分する点 $P$ の座標をベクトル $\vec{A}, \vec{B}$ で表せ。
    > **Formula**: $(1-t)\vec{A} + t\vec{B}$。線形補間 (Lerp)。

---

## Phase 2: Applied Mastery (応用・実践 10問)

**指針**: 「条件を使い切ったか確認せよ」。メネラウスの定理は「キツネ（三角形と串刺し線）」を見つけるのがコツである。

11. **[チェバの定理]**
    $\triangle ABC$ の内部に点 $O$ がある。直線 $AO, BO, CO$ が対辺と交わる点を $P, Q, R$ とする。 $AR:RB=3:2, AQ:QC=2:1$ のとき、 $BP:PC$ を求めよ。

12. **[メネラウスの定理]**
    $\triangle ABC$ の辺 $AB$ を $2:1$ に内分する点を $R$、辺 $AC$ を $3:2$ に内分する点を $Q$ とする。直線 $RQ$ と辺 $BC$ の延長との交点を $P$ とするとき、 $BP:PC$ を求めよ。

13. **[面積比の利用]**
    $\triangle ABC$ において、 $AR:RB=2:3, AQ:QC=3:2$ とする。直線 $BQ$ と $CR$ の交点を $O$ とし、直線 $AO$ と $BC$ の交点を $P$ とする。
    (1) $BP:PC$ を求めよ。
    (2) $\triangle OBC : \triangle ABC$ を求めよ。
    > **Algorithm**: (1) チェバの定理。 (2) メネラウスの定理で $AO:OP$ を求め、面積比に変換。

14. **[外分点の利用]**
    $\triangle ABC$ の $\angle A$ の外角の二等分線が辺 $BC$ の延長と交わる点を $D$ とする。 $AB=6, AC=4$ のとき、 $BD:DC$ を求めよ。
    > **Formula**: $AB:AC$ （外分）。

15. **[ベクトルと比]**
    $\triangle OAB$ において、 $OA$ を $2:1$ に内分する点を $C$、 $OB$ を $3:2$ に内分する点を $D$ とする。 $AD$ と $BC$ の交点を $P$ とするとき、 $\vec{OP}$ を $\vec{OA}, \vec{OB}$ で表せ。
    > **Method**: メネラウスの定理で比を求めてからベクトル計算、またはベクトル方程式の連立。

16. **[重心座標系]** (発展)
    点 $P$ が $\triangle ABC$ の内部にあり、 $\triangle PBC : \triangle PCA : \triangle PAB = u : v : w$ であるとき、 $\vec{P}$ を $u, v, w$ と $\vec{A}, \vec{B}, \vec{C}$ で表せ。
    > **Formula**: $(u\vec{A} + v\vec{B} + w\vec{C}) / (u+v+w)$。

17. **[デザルグの定理]** (発展)
    射影幾何学におけるデザルグの定理と、メネラウスの定理の関係について簡単に述べよ。

18. **[3次元への拡張]**
    四面体においてもチェバの定理のような関係式は成り立つか。
    > **Logic**: 成り立つ（4つの面それぞれ、あるいは体積比として）。

19. **[プログラミング: 交点計算]**
    2直線 $AB$ と $CD$ の交点を求める際、外積を利用して $t : 1-t$ の比を求めるアルゴリズムを記述せよ。
    > **Algorithm**: $\vec{AC}$ と $\vec{CD}$ の外積、 $\vec{AB}$ と $\vec{CD}$ の外積の比を利用。

20. **[UIレイアウト]**
    画面上の矩形領域を $2:1$ に分割し、その左側をさらに $3:2$ に分割する...といったレイアウト計算は、線分の内分計算の繰り返しである。これを再帰的に行うデータ構造を何というか。
    > **Term**: 木構造 (Quadtree, BSP Tree など)。

---

## 解答と解説

### Phase 1

1.  **$\frac{AR}{RB} \cdot \frac{BP}{PC} \cdot \frac{CQ}{QA} = 1$**
2.  **$\frac{AR}{RB} \cdot \frac{BP}{PC} \cdot \frac{CQ}{QA} = 1$**
3.  **1:3**
    *   $(2/1) \cdot (3/2) \cdot (CQ/QA) = 1 \Rightarrow 3 \cdot (CQ/QA) = 1 \Rightarrow CQ:QA = 1:3$。
4.  **3:2**
    *   $(1/2) \cdot (4/3) \cdot (CQ/QA) = 1 \Rightarrow (2/3) \cdot (CQ/QA) = 1 \Rightarrow CQ:QA = 3:2$。
5.  **図示**
    *   $P$ は $AB$ の内部（A寄りではない、B寄り）。 $AP:PB=2:1$。
    *   $Q$ は $B$ の外側。 $AQ:QB=2:1$。
6.  **$1 \cdot 1 \cdot 1 = 1$**
7.  **成り立つ**
8.  **底辺の比**
9.  **成り立つ**
10. **$(1-t)\vec{A} + t\vec{B}$**

### Phase 2

11. **1:3**
    *   $(3/2) \cdot (BP/PC) \cdot (2/1) = 1 \Rightarrow 3 \cdot (BP/PC) = 1 \Rightarrow BP:PC = 1:3$。
12. **9:1**
    *   $\triangle ABQ$ と直線 $R-C-P$ でメネラウス... ではなく、 $\triangle ABC$ と直線 $R-Q-P$。
    *   $AR/RB \cdot BP/PC \cdot CQ/QA = 1$。
    *   $(2/1) \cdot (BP/PC) \cdot (2/3) = 1$ ... 注意: $Q$ は $AC$ を $3:2$ に内分。 $CQ/QA = 2/3$。
    *   $(4/3) \cdot (BP/PC) = 1 \Rightarrow BP:PC = 3:4$。
    *   ... 図を描いて確認。 $R(2:1), Q(3:2)$。
    *   $P$ は $BC$ の延長上。
    *   $AR/RB \times BP/PC \times CQ/QA = 1$。
    *   $2/1 \times BP/PC \times 2/3 = 1 \Rightarrow BP/PC = 3/4$。
    *   つまり $BP:PC = 3:4$。 $P$ は $BC$ を $3:4$ に外分する点（$B$ の左側）。
    *   (計算ミス確認: $Q$ は $A$ から $3$, $C$ から $2$。 $CQ/QA = 2/3$。正しい。
    *   答え: 3:4 (外分)。
    *   解説修正: **3:4**)
13. **(1) 1:1, (2) 1:4**
    *   (1) チェバ: $(2/3) \cdot (BP/PC) \cdot (3/2) = 1 \Rightarrow BP:PC = 1:1$。
    *   (2) メネラウス ($\triangle ABP$ と直線 $R-O-C$):
    *   $AR/RB \cdot BC/CP \cdot PO/OA = 1$。
    *   $(2/3) \cdot (2/1) \cdot (PO/OA) = 1 \Rightarrow (4/3)(PO/OA) = 1 \Rightarrow PO:OA = 3:4$。
    *   $AO:OP = 4:3$。
    *   $\triangle OBC = \frac{OP}{AP} \triangle ABC = \frac{3}{7} \triangle ABC$ ... ではない。
    *   $P$ は中点。 $\triangle ABP = \triangle ACP = 1/2 \triangle ABC$。
    *   $\triangle OBP = (3/7) \triangle ABP = (3/14) \triangle ABC$。
    *   $\triangle OBC = \triangle OBP + \triangle OCP = 2 \times (3/14) = 3/7$。
    *   答え: $3:7$。
    *   (計算ミス確認: $PO/OA = 3/4$。全体 $AP$ は $7$。 $OP$ は $3$。
    *   高さの比は $3/7$。底辺 $BC$ 共通。
    *   よって面積比は $3:7$。
    *   解説修正: **3:7**)
14. **3:2**
    *   $BD:DC = AB:AC = 6:4 = 3:2$。
15. **$\vec{OP} = \frac{1}{2}\vec{OA} + \frac{1}{3}\vec{OB}$** ... 係数和 $\ne 1$ なので違う。
    *   $\vec{OP} = k \vec{OC} + (1-k) \vec{OB}$ ? 違う。
    *   メネラウスで比を出す。 $\triangle OAD$ と直線 $C-P-B$。
    *   $OC/CA \cdot AP/PD \cdot DO/OB$ ... $D$ は $OB$ 上。
    *   $OC/CA = 2/1$。 $DO/OB = 3/5$ (逆)。 $OD:DB=3:2 \to OD/OB=3/5$。
    *   $2/1 \cdot AP/PD \cdot 3/5$? 違う。直線は $C-P-B$。
    *   $\triangle OAD$ の辺 $OA, AD, DO$。
    *   交点 $C$ ($OA$), $P$ ($AD$), $B$ ($DO$延長)。
    *   $OC/CA \cdot AP/PD \cdot DB/BO = 1$。
    *   $(2/1) \cdot (AP/PD) \cdot (2/3) = 1 \Rightarrow AP:PD = 3:4$。
    *   $\vec{OP} = \frac{4\vec{OA} + 3\vec{OD}}{7} = \frac{4\vec{OA} + 3(3/5)\vec{OB}}{7} = \frac{4}{7}\vec{OA} + \frac{9}{35}\vec{OB}$。
    *   (検算: $C, P, B$ は一直線。 $\vec{OP} = s\vec{OC} + (1-s)\vec{OB} = s(2/3)\vec{OA} + (1-s)\vec{OB}$。
    *   係数比較: $4/7 = 2s/3 \to s=6/7$。 $1-s = 1/7$。
    *   $9/35 \ne 1/7$。計算ミス。
    *   $OD:DB=3:2$。 $\vec{OD} = 3/5 \vec{OB}$。
    *   $DB/BO$ は $2/3$ ではなく $2/5$ (長さの比) ではなく...
    *   $D, B, O$ の順。 $DB/BO = 2/5$。
    *   $2/1 \cdot AP/PD \cdot 2/5 = 1 \Rightarrow AP:PD = 5:4$。
    *   $\vec{OP} = \frac{4\vec{OA} + 5\vec{OD}}{9} = \frac{4}{9}\vec{OA} + \frac{5(3/5)}{9}\vec{OB} = \frac{4}{9}\vec{OA} + \frac{1}{3}\vec{OB}$。
    *   検算: $s=2/3 \cdot 9/4$?
    *   $4/9 = 2s/3 \to s=2/3$。 $1-s=1/3$。一致。
    *   答え: $\frac{4}{9}\vec{OA} + \frac{1}{3}\vec{OB}$。
    *   解説修正: **$\frac{4}{9}\vec{OA} + \frac{1}{3}\vec{OB}$**)
16. **解説**
    *   重心座標 (Barycentric Coordinate)。 $u\vec{A}+v\vec{B}+w\vec{C}$ ではなく、面積比に対応。
    *   $\vec{P} = \frac{u\vec{A} + v\vec{B} + w\vec{C}}{u+v+w}$。
17. **解説**
    *   メネラウスの定理はデザルグの定理の特別な場合（あるいは双対）と関連する。
18. **成り立つ**
19. **解説**
    *   $t = (\vec{CD} \times \vec{CA}) / (\vec{CD} \times \vec{AB})$ のような形式。
20. **木構造**

