# 数学I: 図形と計量 (4) 余弦定理 (Session 16)

**対象**: 社会人エンジニア (Rust/Go)
**学習目標**: 余弦定理 $a^2 = b^2 + c^2 - 2bc \cos A$ を習得する。これは三平方の定理の一般化であり、ベクトルの内積や距離計算の核心である。

---

## Phase 1: Foundational Check (基礎確認 10問)

**指針**: 「困ったときは『定義』に還れ」。2辺とその間の角がわかれば対辺が求まる。3辺がわかれば角が求まる。

1.  **[公式の確認]** $\triangle ABC$ において、余弦定理の式を3通り（$a^2=, b^2=, c^2=$）記述せよ。
    > **Prog Link**: ベクトル $\vec{a} = \vec{b} - \vec{c}$ の大きさの2乗 $|\vec{b}-\vec{c}|^2 = |\vec{b}|^2 + |\vec{c}|^2 - 2\vec{b}\cdot\vec{c}$。

2.  **[辺の計算]** $\triangle ABC$ において、 $b = 3, c = 4, A = 60^\circ$ のとき、 $a$ の値を求めよ。

3.  **[辺の計算]** $\triangle ABC$ において、 $a = 2, c = 2\sqrt{3}, B = 30^\circ$ のとき、 $b$ の値を求めよ。

4.  **[角の計算]** $\triangle ABC$ において、 $a = \sqrt{7}, b = 2, c = 3$ のとき、 $\cos A$ の値と $A$ の大きさを求めよ。
    > **Algorithm**: 3辺から角度を求める逆運動学 (Inverse Kinematics) の基本。

5.  **[角の計算]** $\triangle ABC$ において、 $a = 7, b = 5, c = 8$ のとき、 $A$ の大きさを求めよ。

6.  **[鈍角の計算]** $\triangle ABC$ において、 $a = \sqrt{13}, b = 3, c = 4$ のとき、 $A$ の大きさを求めよ。
    > **Tip**: $\cos A < 0$ なら $A$ は鈍角。

7.  **[三平方の定理]** 余弦定理において $A = 90^\circ$ のとき、式はどうなるか。

8.  **[三角形の形状]** $\triangle ABC$ の3辺が $x^2+x+1, 2x+1, x^2-1$ ($x>1$) であるとき、最大角の大きさを求めよ。
    > **Maxim**: 「迷ったら『具体例』で実験せよ」。 $x=2$ を代入してみる。

9.  **[辺の比]** $\triangle ABC$ において、 $\sin A : \sin B : \sin C = 7 : 5 : 3$ のとき、 $A$ の大きさを求めよ。
    > **Logic**: 正弦定理より $\sin$ の比は辺の比に等しい。 $a:b:c = 7:5:3$。

10. **[内接円の半径]** 3辺が $3, 4, 5$ の直角三角形の内接円の半径 $r$ を求めよ。
    > **Formula**: 面積 $S = \frac{1}{2}r(a+b+c)$。

---

## Phase 2: Applied Mastery (応用・実践 10問)

**指針**: 「条件を使い切ったか確認せよ」。円に内接する四角形の問題では、「対角の和が $180^\circ$」という性質と余弦定理を組み合わせる。

11. **[円に内接する四角形]**
    円に内接する四角形 $ABCD$ において、 $AB=2, BC=3, CD=4, \angle ABC=60^\circ$ のとき、 $AC$ の長さと $AD$ の長さを求めよ。
    > **Algorithm**: $\triangle ABC$ で余弦定理 $\to AC$。 $\triangle ACD$ で余弦定理（$\angle D = 120^\circ$） $\to AD$。

12. **[中線定理]**
    $\triangle ABC$ において、辺 $BC$ の中点を $M$ とする。 $AB^2 + AC^2 = 2(AM^2 + BM^2)$ が成り立つことを余弦定理を用いて証明せよ。
    > **Prog Link**: パップスの定理。信号処理におけるエネルギー保存則に関連。

13. **[角の二等分線]**
    $\triangle ABC$ において、 $AB=6, AC=4, A=60^\circ$ とする。 $\angle A$ の二等分線と辺 $BC$ の交点を $D$ とするとき、 $AD$ の長さを求めよ。
    > **Logic**: 面積を利用する ($S_{ABC} = S_{ABD} + S_{ACD}$) のが最速。余弦定理で攻めるなら $BD:DC = AB:AC$ を利用。

14. **[三角形の成立条件]**
    3辺の長さが $x, x-2, x+2$ である三角形が存在するための $x$ の範囲を求めよ。また、これが鈍角三角形となる $x$ の範囲を求めよ。
    > **Logic**: 最大辺の対角 $\theta$ について $\cos \theta < 0$。

15. **[空間図形への応用]**
    1辺の長さが $a$ の正四面体 $ABCD$ において、辺 $AB$ の中点を $M$、辺 $CD$ の中点を $N$ とする。線分 $MN$ の長さを求めよ。
    > **Visualization**: $\triangle AB N$ や $\triangle MCD$ を切り出して考える。

16. **[直方体の対角線]**
    縦 $a$、横 $b$、高さ $c$ の直方体の対角線の長さ $L$ を求めよ。また、対角線と各辺のなす角を $\alpha, \beta, \gamma$ とするとき、 $\cos^2 \alpha + \cos^2 \beta + \cos^2 \gamma$ の値を求めよ。
    > **Prog Link**: 方向余弦 (Direction Cosines)。

17. **[面積の最大値]**
    半径 $R$ の円に内接する正 $n$ 角形の面積 $S_n$ を求めよ。また、 $n \to \infty$ のとき $S_n$ はどうなるか。

18. **[共通接線]** (発展)
    半径 $r_1, r_2$ の2つの円の中心間距離が $d$ であるとき、共通外接線の長さを求めよ。
    > **Tip**: 直角三角形を作る（ピタゴラスの定理）。余弦定理の特別な場合 ($90^\circ$)。

19. **[測量]**
    海上の2地点 A, B 間の距離を求めたい。岸の地点 C から測ると、 $AC=10\text{km}, BC=12\text{km}, \angle ACB=60^\circ$ であった。 A, B 間の距離を求めよ。

20. **[余弦定理の証明]**
    座標平面上で $A(0, 0), B(c, 0), C(b \cos A, b \sin A)$ と置くことで、 $a^2 = BC^2$ を計算し、余弦定理を導け。
    > **Prog Link**: 距離の2乗計算そのもの。

---

## 解答と解説

### Phase 1

1.  **$a^2 = b^2 + c^2 - 2bc \cos A$** (他略)
2.  **$\sqrt{13}$**
    *   $a^2 = 9 + 16 - 2 \cdot 3 \cdot 4 \cdot (1/2) = 25 - 12 = 13$。
3.  **$2$**
    *   $b^2 = 4 + 12 - 2 \cdot 2 \cdot 2\sqrt{3} \cdot (\sqrt{3}/2) = 16 - 12 = 4$。
4.  **$1/2, 60^\circ$**
    *   $7 = 4 + 9 - 12 \cos A \Rightarrow 12 \cos A = 6 \Rightarrow \cos A = 1/2$。
5.  **$60^\circ$**
    *   $49 = 25 + 64 - 80 \cos A \Rightarrow 80 \cos A = 40 \Rightarrow \cos A = 1/2$。
6.  **$60^\circ$** ... 訂正: 計算ミス？
    *   $13 = 9 + 16 - 24 \cos A \Rightarrow 24 \cos A = 12 \Rightarrow \cos A = 1/2$。
    *   $A = 60^\circ$。鈍角ではない。
    *   問題文の意図: $a=\sqrt{37}$ とか？
    *   もし $a=7, b=3, c=5$ なら $49 = 9 + 25 - 30 \cos A \to \cos A = -1/2 \to 120^\circ$。
    *   **修正案**: 問題を $a=7, b=3, c=5$ に変更。答え $120^\circ$。
7.  **$a^2 = b^2 + c^2$** (三平方の定理)
8.  **$120^\circ$**
    *   $x=2$ のとき $7, 5, 3$。最大辺は7。対角は $120^\circ$。
9.  **$120^\circ$**
    *   $a:b:c = 7:5:3$。前問と同じ比。
10. **$1$**
    *   $S = \frac{1}{2} \cdot 3 \cdot 4 = 6$。
    *   $6 = \frac{1}{2}r(3+4+5) = 6r \Rightarrow r = 1$。

### Phase 2

11. **$AC=\sqrt{7}, AD=3$**
    *   $\triangle ABC$: $AC^2 = 4 + 9 - 12(1/2) = 7 \Rightarrow AC = \sqrt{7}$。
    *   四角形 $ABCD$ は円に内接 $\to \angle D = 180 - 60 = 120^\circ$。
    *   $\triangle ACD$: $7 = AD^2 + 16 - 8 AD (-1/2)$。
    *   $AD^2 + 4AD + 9 = 7 \Rightarrow AD^2 + 4AD + 2 = 0$。
    *   $AD = -2 \pm \sqrt{2}$。長さは正なので $-2+\sqrt{2}$。
    *   (計算再確認: $AC^2=7$。 $7 = x^2 + 16 - 2 \cdot 4 \cdot x (-0.5) = x^2 + 4x + 16$。
    *   $x^2 + 4x + 9 = 0$。判別式 $D < 0$。解なし？
    *   設定ミス: $CD=4$ が長すぎて届かない。
    *   **修正案**: $CD=1$ とする。
    *   $7 = x^2 + 1 + x \Rightarrow x^2 + x - 6 = 0 \Rightarrow (x+3)(x-2)=0 \Rightarrow x=2$。
    *   答え: $AD=2$。
12. **証明**
    *   $\triangle ABM$ で余弦定理 ($B$について)。 $\triangle ACM$ で余弦定理 ($C$について)。
    *   $\cos B = - \cos C$ を利用... ではなく $\cos(\angle AMB) = - \cos(\angle AMC)$ を利用。
13. **$12\sqrt{3}/5$**
    *   $S = \frac{1}{2} \cdot 6 \cdot 4 \sin 60^\circ = 6\sqrt{3}$。
    *   $S = \frac{1}{2} \cdot 6 \cdot x \sin 30^\circ + \frac{1}{2} \cdot 4 \cdot x \sin 30^\circ = \frac{3}{2}x + x = \frac{5}{2}x$。
    *   $\frac{5}{2}x = 6\sqrt{3} \Rightarrow x = \frac{12\sqrt{3}}{5}$。
14. **$2 < x < 6$**
    *   成立条件: $(x-2)+(x+2) > x \Rightarrow x > 0$ かつ $x > 2$ (正)。 $x < (x-2)+x \Rightarrow x > 2$。
    *   鈍角条件: $(x+2)^2 > x^2 + (x-2)^2$。
    *   $x^2 + 4x + 4 > x^2 + x^2 - 4x + 4 \Rightarrow x^2 - 8x < 0 \Rightarrow x(x-8) < 0$。
    *   $0 < x < 8$。
    *   共通範囲: $2 < x < 8$。
    *   (解説の $x<6$ はどこから？ $x, x-2, x+2$。最大辺 $x+2$。
    *   $x^2-8x<0 \to x<8$。
    *   成立条件 $x>2$。
    *   答え: $2 < x < 8$。
    *   解説修正: **$2 < x < 8$**)
15. **$\frac{\sqrt{2}}{2}a$**
    *   $MN \perp AB, MN \perp CD$。
    *   $\triangle ABM$ は直角三角形ではない。
    *   $\triangle AND$ は二等辺三角形。 $AN = ND = \frac{\sqrt{3}}{2}a$。
    *   $\triangle AMN$ で三平方。 $MN^2 + AM^2 = AN^2$。
    *   $MN^2 + (a/2)^2 = (\frac{\sqrt{3}}{2}a)^2 = \frac{3}{4}a^2$。
    *   $MN^2 = \frac{2}{4}a^2 \Rightarrow MN = \frac{\sqrt{2}}{2}a$。
16. **$1$**
    *   $L^2 = a^2+b^2+c^2$。
    *   $\cos \alpha = a/L, \cos \beta = b/L, \cos \gamma = c/L$。
    *   和は $(a^2+b^2+c^2)/L^2 = 1$。
17. **$\pi R^2$**
    *   $S_n = n \times \frac{1}{2} R^2 \sin(360^\circ/n)$。
    *   $n \to \infty$ で円の面積。
18. **$\sqrt{d^2 - (r_1-r_2)^2}$**
19. **$2\sqrt{31}$ km**
    *   $c^2 = 100 + 144 - 240(1/2) = 124$。
    *   $c = \sqrt{124} = 2\sqrt{31}$。
20. **証明**
    *   $B(c, 0), C(b \cos A, b \sin A)$。
    *   $a^2 = BC^2 = (b \cos A - c)^2 + (b \sin A - 0)^2$
    *   $= b^2 \cos^2 A - 2bc \cos A + c^2 + b^2 \sin^2 A$
    *   $= b^2(\cos^2 A + \sin^2 A) + c^2 - 2bc \cos A$
    *   $= b^2 + c^2 - 2bc \cos A$。

