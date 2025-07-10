# クイズ：ResNet と ResNeXt の基礎

これまでに学んだ ResNet と ResNeXt の概念について、理解度を確認するための簡単なクイズです。各質問に答えてみましょう。

---

### 質問 1

深層ネットワークにおいて、層を深くしていくと、学習時に勾配が非常に小さくなり、初期の層の重みがほとんど更新されなくなる現象は何と呼ばれますか？

A. 勾配爆発問題 (Exploding Gradient Problem)
B. 勾配消失問題 (Vanishing Gradient Problem)
C. 過学習 (Overfitting)
D. 性能の劣化問題 (Degradation Problem)

<details>
<summary>解答を見る</summary>
<p><b>B. 勾配消失問題 (Vanishing Gradient Problem)</b></p>
<p>勾配消失問題は、深いネットワークで勾配が0に近づき、学習が停滞する現象です。</p>
</details>

---

### 質問 2

ResNetが深層ネットワークの学習を可能にした、入力 $x$ を層の出力に直接加算する構造は何と呼ばれますか？

A. ボトルネックブロック (Bottleneck Block)
B. インセプションモジュール (Inception Module)
C. 残差ブロック (Residual Block)
D. 注意機構 (Attention Mechanism)

<details>
<summary>解答を見る</summary>
<p><b>C. 残差ブロック (Residual Block)</b></p>
<p>残差ブロックは、スキップコネクションを用いて入力信号を直接次の層に伝えることで、勾配消失や性能の劣化を防ぎます。</p>
</details>

---

### 質問 3

ResNetの残差ブロックにおいて、もしある層が何も情報を追加する必要がない（恒等写像で十分）と判断した場合、学習すべき残差関数 $F(x)$ は理想的にどのような値に近づくことを目指しますか？

A. $F(x) = x$
B. $F(x) = 1$
C. $F(x) = 0$
D. $F(x) = -x$

<details>
<summary>解答を見る</summary>
<p><b>C. $F(x) = 0$</b></p>
<p>残差ブロックは $H(x) = F(x) + x$ で表されます。もし $H(x) = x$ (恒等写像) で十分な場合、 $F(x)$ は $0$ を学習すればよく、これは比較的容易です。</p>
</details>

---

### 質問 4

ResNeXtの主要なアイデアであり、複数の並列パスを持ち、それぞれのパスで異なる変換を行い、それらの結果を集約する概念は何と呼ばれますか？

A. グループ化畳み込み (Grouped Convolution)
B. 恒等写像 (Identity Mapping)
C. 集約された変換 (Aggregated Transformations)
D. 自己注意 (Self-Attention)

<details>
<summary>解答を見る</summary>
<p><b>C. 集約された変換 (Aggregated Transformations)</b></p>
<p>ResNeXtは、この集約された変換の概念に基づき、複数の並列ブランチで特徴を学習し、それらを集約します。</p>
</details>

---

### 質問 5

ResNeXtにおいて、並列するブランチの数を表し、モデルの表現能力に大きく寄与する重要なハイパーパラメータは何と呼ばれますか？

A. 深さ (Depth)
B. 幅 (Width)
C. カーディナリティ (Cardinality)
D. ストライド (Stride)

<details>
<summary>解答を見る</summary>
<p><b>C. カーディナリティ (Cardinality)</b></p>
<p>カーディナリティを増やすことで、パラメータ数を大幅に増やすことなく、モデルの表現能力と精度を向上させることができるとされています。</p>
</details>

---

これで、ResNetとResNeXtの基礎に関するクイズは終わりです。

次のセクションでは、より詳細な理論に踏み込んでいきます。

---