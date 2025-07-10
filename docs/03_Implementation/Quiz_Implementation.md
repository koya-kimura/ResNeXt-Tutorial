# クイズ：ResNeXtの実装

これまでに学んだResNeXtの実装に関する概念について、理解度を確認するための簡単なクイズです。各質問に答えてみましょう。

---

### 質問 1

`scripts/ResNeXt_Example.ipynb` のセル3で、PyTorchのモデルをデバイス（GPUまたはCPU）に移動するために使用されるメソッドは何ですか？

A. `model.to_device(device)`
B. `model.move(device)`
C. `model.cuda()`
D. `model.to(device)`

<details>
<summary>解答を見る</summary>
<p><b>D. `model.to(device)`</b></p>
<p>PyTorchでは、モデルやテンソルを指定されたデバイスに移動するために `to()` メソッドを使用します。</p>
</details>

---

### 質問 2

CIFAR-10データセットをロードする際、`torchvision.datasets.CIFAR10` の `transform` 引数に渡す目的で定義される `transforms.Compose` の最初のステップとして、PIL ImageやNumPy配列をPyTorch Tensorに変換する関数は何ですか？

A. `transforms.Normalize()`
B. `transforms.Resize()`
C. `transforms.ToTensor()`
D. `transforms.CenterCrop()`

<details>
<summary>解答を見る</summary>
<p><b>C. `transforms.ToTensor()`</b></p>
<p>画像データをPyTorchモデルが扱えるテンソル形式に変換するために、`ToTensor()` が最初に適用されます。</p>
</details>

---

### 質問 3

ResNeXtモデルの最終層 (`model.fc`) は、ImageNetの1000クラス分類用に設計されています。これをCIFAR-10の10クラス分類に合わせるために、どのように変更しますか？

A. `model.fc = nn.Softmax(dim=1)`
B. `model.fc = nn.Linear(num_classes, num_ftrs)`
C. `model.fc = nn.Linear(model.fc.in_features, 10)`
D. `model.fc.out_features = 10`

<details>
<summary>解答を見る</summary>
<p><b>C. `model.fc = nn.Linear(model.fc.in_features, 10)`</b></p>
<p>既存の全結合層の入力特徴量数（`in_features`）をそのままに、出力特徴量数をターゲットクラス数（10）に設定した新しい `nn.Linear` 層で置き換えます。</p>
</details>

---

### 質問 4

モデルの学習中に、過学習を防ぎ、推論時にモデルの出力を安定させるために、バリデーションフェーズでモデルをどのようなモードに設定する必要がありますか？

A. `model.train()`
B. `model.eval()`
C. `model.optimize()`
D. `model.freeze()`

<details>
<summary>解答を見る</summary>
<p><b>B. `model.eval()`</b></p>
<p>評価モードに設定することで、Dropout層が無効になり、Batch Normalization層は学習済みの平均と分散を使用するようになります。</p>
</details>

---

### 質問 5

推論時（`model.eval()`）に、計算グラフの構築と勾配計算を無効化することで、メモリ使用量を節約し、推論速度を向上させるために使用されるPyTorchのコンテキストマネージャーは何ですか？

A. `with torch.set_grad_enabled(False):`
B. `with torch.no_grad():`
C. `with torch.inference_mode():`
D. `with torch.disable_grad():`

<details>
<summary>解答を見る</summary>
<p><b>B. `with torch.no_grad():`</b></p>
<p>このコンテキストマネージャーは、そのブロック内のすべての計算で勾配計算を無効にします。</p>
</details>

---

これで、ResNeXtの実装に関するクイズは終わりです。

全てのコンテンツ生成が完了しました。

---