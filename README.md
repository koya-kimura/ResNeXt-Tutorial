# ResNeXt-Learning-Repo: 初学者のためのResNeXt学習リポジトリ

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

このリポジトリは、**ResNetを既に学び、ResNeXtの基本構造と実装の感覚を掴みたい初学者**の方を対象とした学習コンテンツです。深層学習フレームワークとしてPyTorchを使用し、ResNeXtの理論的背景から実践的な実装までを段階的に学ぶことができます。

## 🚀 学習目標

* **ResNetとResNeXtの主要な違い**を理解する。
* **ResNeXtの核となる概念（Aggregated Transformations, Cardinality）**を理解する。
* PyTorchを用いて**ResNeXtのミニマルな実装**を体験し、その構造をコードレベルで理解する。
* 実装したモデルを用いて**簡単なデータセットでの学習・評価**を行い、動くモデルによる成功体験を得る。

## 📚 コンテンツ

本リポジトリは以下の主要なセクションで構成されています。

* **`docs/`**: 各学習セクションの解説ドキュメントと理解度確認クイズ。
    * **`01_Introduction/`**: ResNetの基礎とResNeXtの導入。
    * **`02_Theory/`**: ResNeXtの主要な理論的概念の解説。
    * **`03_Implementation/`**: ResNeXtの実装に関する解説。
* **`scripts/`**: Jupyter Notebook形式の実行可能なコード例。
    * **`ResNeXt_Example.ipynb`**: ResNeXtモデルの簡易的な実装、学習、評価を行う統合ノートブック。
* **`assets/`**: 解説ドキュメント内で使用される画像などのリソース。
* **`memo/`**: 個人的なメモや一時ファイルを保存するためのフォルダ。（Git管理対象外）

### 学習パス

1.  **`docs/01_Introduction/`** から学習を始め、ResNetの復習とResNeXtの導入部分を理解しましょう。
2.  **`docs/02_Theory/`** でResNeXtの核心であるAggregated TransformationsとCardinalityについて深く学びます。
3.  **`docs/03_Implementation/01_Environment_Setup.md`** を参考に環境を構築します。
4.  **`docs/03_Implementation/02_ResNeXt_Implementation_and_Explanation.md`** を読みながら、**`scripts/ResNeXt_Example.ipynb`** のコードを実行し、実装の理解を深めます。
5.  各セクションの学習後には、対応する **`Quiz_*.md`** ファイルで理解度を確認しましょう。

## 💻 実行環境

本リポジトリのコードは、Google Colaboratory (Colab) での実行を強く推奨します。必要なライブラリは `requirements.txt` に記載されており、Colab環境であれば簡単にセットアップできます。

### 環境構築手順 (Colabの場合)

1.  Google Colabで新しいノートブックを開きます。
2.  以下のコマンドを実行し、リポジトリをクローンします。

    ```bash
    !git clone [https://github.com/your-username/ResNeXt-Learning-Repo.git](https://github.com/your-username/ResNeXt-Learning-Repo.git)
    %cd ResNeXt-Learning-Repo
    ```
    （`https://github.com/your-username/ResNeXt-Learning-Repo.git` はご自身のGitHubリポジトリURLに置き換えてください。）

3.  必要なライブラリをインストールします。

    ```bash
    !pip install -r requirements.txt
    ```

4.  **`scripts/ResNeXt_Example.ipynb`** を開き、上から順にセルを実行して動作を確認してください。

### 環境構築手順 (ローカルPCの場合)

1.  Python 3.8以上の環境があることを確認してください。
2.  リポジトリをクローンします。

    ```bash
    git clone [https://github.com/your-username/ResNeXt-Learning-Repo.git](https://github.com/your-username/ResNeXt-Learning-Repo.git)
    cd ResNeXt-Learning-Repo
    ```
    （`https://github.com/your-username/ResNeXt-Learning-Repo.git` はご自身のGitHubリポジトリURLに置き換えてください。）

3.  仮想環境の作成とアクティベート (推奨):

    ```bash
    python -m venv venv
    # Windows
    .\venv\Scripts\activate
    # macOS/Linux
    source venv/bin/activate
    ```

4.  必要なライブラリをインストールします。

    ```bash
    pip install -r requirements.txt
    ```

5.  Jupyter Notebookを起動し、`scripts/ResNeXt_Example.ipynb` を開きます。

    ```bash
    jupyter notebook
    ```

## 🛠️ 技術スタック

* Python 3.x
* PyTorch
* torchvision
* NumPy
* Pillow
* Matplotlib
* Jupyter Notebook

## 🤝 貢献

このリポジトリは学習者の助けとなることを目的としています。誤りや改善点、新しいコンテンツの提案などがあれば、IssueやPull Requestでお気軽にご連絡ください。

## 📄 ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細については [LICENSE](LICENSE) ファイルをご覧ください。

---