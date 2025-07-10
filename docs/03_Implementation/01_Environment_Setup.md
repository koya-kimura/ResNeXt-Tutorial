# 環境構築ガイド：ResNeXtモデルの実行準備

このドキュメントでは、`scripts/ResNeXt_Example.ipynb` を含むResNeXtモデルの学習と評価に必要な開発環境のセットアップ方法を解説します。Pythonのバージョン管理、必要なライブラリのインストール、そしてGPU（CUDA/MPS）環境の準備について説明します。

## 1\. 推奨される環境

  * OS: Windows, macOS, Linux (いずれも可)
  * Python: 3.9 - 3.11 (推奨は 3.10 または 3.11)
  * パッケージ管理: `conda` (Miniconda/Anaconda) または `venv` (Python標準)
  * GPU: NVIDIA GPU (CUDA対応) または Apple Silicon Mac (MPS対応) を強く推奨

## 2\. Python環境のセットアップ (conda または venv)

仮想環境を使用することで、プロジェクトごとに依存関係を分離し、環境の衝突を防ぐことができます。

### オプション A: `conda` を使用する場合 (推奨)

`conda` は、Pythonパッケージだけでなく、システムレベルのライブラリも管理できるため、特にGPU環境のセットアップにおいて強力です。

1.  **Miniconda または Anaconda のインストール**:
    公式ウェブサイトからお使いのOSに合ったインストーラーをダウンロードし、指示に従ってインストールしてください。

      * [Miniconda 公式サイト](https://docs.conda.io/en/latest/miniconda.html)
      * [Anaconda 公式サイト](https://www.anaconda.com/products/distribution)

2.  **新しい仮想環境の作成**:
    ターミナルまたはAnaconda Promptを開き、以下のコマンドを実行します。ここではPython 3.10で `resnext_env` という名前の環境を作成します。

    ```bash
    conda create -n resnext_env python=3.10
    ```

3.  **仮想環境のアクティベート**:

    ```bash
    conda activate resnext_env
    ```

    (環境を終了する場合は `conda deactivate` を実行します。)

### オプション B: `venv` を使用する場合 (Python標準)

`venv` はPythonに標準で含まれているため、追加のインストールは不要です。

1.  **プロジェクトディレクトリへの移動**:
    まず、このリポジトリのルートディレクトリに移動します。

    ```bash
    cd path/to/ResNeXt-Learning-Repo
    ```

2.  **仮想環境の作成**:
    以下のコマンドを実行して、`venv` という名前の仮想環境を作成します。

    ```bash
    python3 -m venv venv
    ```

3.  **仮想環境のアクティベート**:

      * **macOS / Linux**:
        ```bash
        source venv/bin/activate
        ```
      * **Windows (Command Prompt)**:
        ```bash
        venv\Scripts\activate.bat
        ```
      * **Windows (PowerShell)**:
        ```bash
        venv\Scripts\Activate.ps1
        ```

    (環境を終了する場合は `deactivate` を実行します。)

## 3\. 必要なライブラリのインストール

仮想環境をアクティベートした状態で、このリポジトリの `requirements.txt` ファイルに記載されているすべてのライブラリをインストールします。

```bash
pip install -r requirements.txt
```

これにより、PyTorch, torchvision, matplotlib, numpy, tqdm, torchinfo などの必要なライブラリがインストールされます。

## 4\. GPU環境のセットアップ (PyTorch)

GPUを使用することで、モデルの学習速度を劇的に向上させることができます。

### オプション A: NVIDIA GPU (CUDA) を使用する場合

NVIDIA GPUを使用する場合、CUDA ToolkitとcuDNNが正しくインストールされている必要があります。`requirements.txt` にはCPU版のPyTorchが指定されている可能性があるため、GPU版を明示的にインストールし直すことを推奨します。

1.  **CUDA Toolkitの確認**:
    お使いのNVIDIA GPUに対応するCUDA Toolkitのバージョンを確認してください。通常、PyTorchの公式ウェブサイトで推奨されるバージョンが示されています。

2.  **PyTorchのGPU版インストール**:
    PyTorchの公式ウェブサイト ([pytorch.org](https://pytorch.org/get-started/locally/)) にアクセスし、お使いの環境（OS, pip/conda, CUDAバージョン）に合わせたインストールコマンドをコピーして実行します。

    **例 (conda, CUDA 11.8の場合):**

    ```bash
    conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
    ```

    **例 (pip, CUDA 11.8の場合):**

    ```bash
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
    ```

    (既にCPU版がインストールされている場合、`pip install --upgrade` を使用するか、一度アンインストールしてから再インストールしてください。)

3.  **インストール確認**:
    Pythonインタープリタで以下のコマンドを実行し、`True` が返されれば成功です。

    ```python
    import torch
    print(torch.cuda.is_available())
    ```

### オプション B: Apple Silicon Mac (MPS) を使用する場合

Apple Silicon (M1/M2/M3チップなど) を搭載したMacでは、Metal Performance Shaders (MPS) を利用してGPUアクセラレーションを行うことができます。

1.  **PyTorchのMPS対応版インストール**:
    `requirements.txt` でインストールされるPyTorchは通常MPSに対応していますが、念のため最新版をインストールすることをお勧めします。

    ```bash
    pip install --upgrade torch torchvision torchaudio
    ```

2.  **インストール確認**:
    Pythonインタープリタで以下のコマンドを実行し、`True` が返されれば成功です。

    ```python
    import torch
    print(torch.backends.mps.is_available())
    print(torch.backends.mps.is_built())
    ```

## 5\. Jupyter Notebook/Lab のインストールと起動

`scripts/ResNeXt_Example.ipynb` を実行するためには、Jupyter環境が必要です。

1.  **Jupyter のインストール**:
    仮想環境がアクティベートされた状態で、以下のコマンドを実行します。

    ```bash
    pip install jupyter notebook # または pip install jupyter lab
    ```

2.  **Jupyter Notebook/Lab の起動**:
    リポジトリのルートディレクトリに移動し、以下のコマンドを実行します。

    ```bash
    jupyter notebook # または jupyter lab
    ```

    これにより、ウェブブラウザでJupyterインターフェースが開き、`scripts/ResNeXt_Example.ipynb` を選択して実行できるようになります。

これで、ResNeXtモデルの学習と評価を行うための環境が整いました。