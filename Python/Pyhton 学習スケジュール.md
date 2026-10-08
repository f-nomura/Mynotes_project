## 前半：Python基礎からNumPy・画像処理の土台作り（1〜4週目）
| 週・曜日      | 学習内容          | 空で書けるようにする重要コード                                                    |
| --------- | ------------- | ------------------------------------------------------------------ |
| **1週 月**  | 変数、データ型、if文   | if x % 2 == 0: print("Even")                                       |
| **1週 火**  | for文、リスト内包表記  | squares = [i**2 for i in range(10)]                                |
| **1週 水**  | 関数の定義         | def process(x, y=1): return x + y                                  |
| **1週 木**  | クラスの基礎        | class Model:	def __init__(self): self.name = "CNN"                 |
| **1週 金**  | メソッドとクラスの活用   | def forward(self, x):   return x * 2                               |
| **1週 土**  | **総復習**       | 上記を組み合わせた自作クラスの実装                                                  |
| **2週 月**  | ファイルの読み書き     | with open('data.txt', 'r') as f:  text = f.read()                  |
| **2週 火**  | JSONの操作       | import json with open('config.json', 'r') as f: cfg = json.load(f) |
| **2週 水**  | モジュールのインポート   | from my_module import my_func                                      |
| **2週 木**  | 例外処理          | try:1 / 0 except ZeroDivisionError: print("Error")                 |
| **2週 金**  | パス操作（pathlib） | from pathlib import Path paths = list(Path('.').glob('*.png'))     |
| **2週 土**  | **総復習**       | 複数ファイルの読み込みとテキスト処理                                                 |
| **3週 月**  | NumPy配列の作成    | import numpy as np arr = np.zeros((3, 3))                          |
| **3週 火**  | インデックスとスライス   | crop = img[10:50, 20:60]                                           |
| **3週 水**  | ブロードキャスト      | arr_centered = arr - np.mean(arr)                                  |
| **3週 木**  | 行列の積          | out = np.dot(W, x) + b                                             |
| **3週 金**  | 次元操作          | arr = arr.reshape(1, -1)                                           |
| **3週 土**  | **総復習**       | for文を使わない行列計算の実装                                                   |
| **4週 月**  | 集約関数（axisの理解） | max_val = np.max(arr, axis=1)                                      |
| **4週 火**  | 画像のShape確認    | H, W, C = img.shape                                                |
| **4週 水**  | 画像の反転（スライス）   | img_flipped = img[:, ::-1, :]                                      |
| **4週 木**  | パディング処理       | np.pad(img, ((1,1), (1,1)), 'constant')                            |
| **4週 金**  | 画像の正規化        | img_norm = (img - img.min()) / (img.max() - img.min())             |
| **4週 土**  | **総復習**       | 画像の読み込みから正規化までの配列操作                                                |

## 後半：PyTorchの実践と論文実装への橋渡し（5〜8週目）


| 週・曜日 | 学習内容 | 空で書けるようにする重要コード |
|---|---|---|
| **5週 月** | Matplotlib（ロス描画） | import matplotlib.pyplot as plt plt.plot(loss); plt.show() |
| **5週 火** | Matplotlib（複数画像） | fig, axes = plt.subplots(1, 2) axes[0].imshow(img) |
| **5週 水** | Pillow（画像読込・リサイズ） | from PIL import Image img = Image.open('a.jpg').resize((224, 224)) |
| **5週 木** | OpenCV（色変換） | import cv2 img = cv2.cvtColor(cv2.imread('a.jpg'), cv2.COLOR_BGR2RGB) |
| **5週 金** | OpenCV（描画処理） | cv2.rectangle(img, (x1, y1), (x2, y2), (255,0,0), 2) |
| **5週 土** | **総復習** | OpenCV/Pillowで読み込みMatplotlibで表示 |
| **6週 月** | Tensorとデバイス転送 | import torch device = "cuda" if torch.cuda.is_available() else "cpu" x = torch.randn(3, 3).to(device) |
| **6週 火** | Autograd（自動微分） | x.requires_grad = True y = x ** 2; y.backward() |
| **6週 水** | 線形層と活性化関数 | import torch.nn as nn layer = nn.Sequential(nn.Linear(10, 5), nn.ReLU()) |
| **6週 木** | Datasetクラスの必須構造 | class MyData(Dataset): def __len__(self): return len(self.data) def __getitem__(self, i): return self.data[i] |
| **6週 金** | DataLoaderの設定 | from torch.utils.data import DataLoader loader = DataLoader(dataset, batch_size=32, shuffle=True) |
| **6週 土** | **総復習** | DatasetからDataLoaderへ渡す一連の流れ |
| **7週 月** | 畳み込み層（Conv2d） | nn.Conv2d(in_channels=3, out_channels=16, kernel_size=3, padding=1) |
| **7週 火** | CNNクラスの必須構造 | class Net(nn.Module):  def __init__(self): super().__init__() def forward(self, x): return x |
| **7週 水** | 損失関数とオプティマイザ | criterion = nn.CrossEntropyLoss() opt = torch.optim.Adam(model.parameters(), lr=1e-3) |
| **7週 木** | **学習ループの5ステップ**（※絶対暗記） | opt.zero_grad() out = model(x) loss = criterion(out, y) loss.backward() opt.step() |
| **7週 金** | 推論とモデル保存 | with torch.no_grad(): out = model(x) torch.save(model.state_dict(), 'model.pth') |
| **7週 土** | **総復習** | CNN定義〜学習ループの一気貫通 |
| **8週 月** | ResBlock（残差接続） | out = self.relu(self.conv(x) + x) |
| **8週 火** | 次元（Shape）のデバッグ | assert out.shape == (batch, channels, H, W) |
| **8週 水** | ダミーデータでの結合テスト | model = Net(); x = torch.randn(2, 3, 224, 224) print(model(x).shape) |
| **8週 木** | 論文用Datasetの実装 | （ターゲット論文に合わせた前処理・拡張の実装） |
| **8週 金** | 学習ループの調整 | （スケジューラ等の組み込み） |
| **8週 土** | **総復習** | 論文アーキテクチャのフルスクラッチ再現 |


## 追加スケジュール：Kaggle初提出・戦闘力向上（9〜12週目）

平日は「1日45〜60分で完結するタスク」、土曜日は「ノートブックを一気通貫で動かす日」として設計しています。

### 9週目：PandasとScikit-learnによるデータハンドリング
画像データそのものではなく、画像の「パス」や「正解ラベル」が書かれたCSVファイルを自在に扱う週です。

| 曜日 | 学習内容 | 空で書けるようにする重要コード（暗記） |
|---|---|---|
| **月** | PandasによるCSV読み込みと確認 | `import pandas as pd`<br>`df = pd.read_csv('train.csv')`<br>`print(df.shape, df.columns)` |
| **火** | 条件抽出と特定の列の操作 | `img_paths = df['image_id'].apply(lambda x: f"images/{x}.jpg").values` |
| **水** | データの分割（Train / Val） | `from sklearn.model_selection import train_test_split`<br>`train_df, val_df = train_test_split(df, test_size=0.2, random_state=42)` |
| **木** | DataFrame型からDatasetへの結合 | `class KaggleDataset(Dataset):`<br>`    def __init__(self, df): self.df = df`<br>`    def __getitem__(self, i): return self.df.iloc[i]['label']` |
| **金** | テストデータの読み込みと推論準備 | `test_df = pd.read_csv('test.csv')`<br>`preds_list = []` |
| **土** | **総復習：CSV読み込み〜データ分割** | CSVを読み込み、8:2に分割して、それぞれのShapeを確認するまでの一連の流れ。 |
| **日** | 予備日・リファクタリング | データの欠損値（NaN）の有無を確認する処理などを復習。 |

### 10週目：Kaggle標準の学習・推論パイプライン構築
7週目で学んだPyTorchの学習ループに、Pandasとtqdm（進捗バー）を組み込み、本格的な「訓練・検証・推論」の流れを固定します。

| 曜日 | 学習内容 | 空で書けるようにする重要コード（暗記） |
|---|---|---|
| **月** | tqdmによるループの可視化 | `from tqdm import tqdm`<br>`for images, labels in tqdm(dataloader, desc="Train"):` |
| **火** | 各エポックでのLoss・精度の記録 | `epoch_loss += loss.item()`<br>`epoch_preds.extend(out.argmax(dim=1).cpu().numpy())` |
| **水** | 検証（Validation）フェーズの追加 | `model.eval()`<br>`with torch.no_grad():`<br>`    val_out = model(val_images)` |
| **木** | テストデータに対する推論の実行 | `model.eval()`<br>`with torch.no_grad():`<br>`    preds = model(test_images).softmax(dim=1)[:, 1].numpy()` |
| **金** | 提出用CSV（Submission）の作成 | `sub = pd.read_csv('sample_submission.csv')`<br>`sub['label'] = test_preds`<br>`sub.to_csv('submission.csv', index=False)` |
| **土** | **総復習：提出コードの全結合テスト** | ダミーのCSVと画像を用意し、学習、検証、推論、提出ファイル出力までエラーなしで回す。 |
| **日** | 予備日・リファクタリング | `index=False` を忘れていないかなど、提出用CSVのフォーマットを厳格にチェック。 |

### 11週目：Kaggleの最重要技術「交差検証（Cross Validation）」
Kaggleで勝つ（上位に入る）ために絶対に必要な「K-Fold（交差検証）」を実装します。データを5つに分け、5つのモデルを作ってアンサンブル（平均）する、Kaggleの王道パターンです。

| 曜日 | 学習内容 | 空で書けるようにする重要コード（暗記） |
|---|---|---|
| **月** | StratifiedKFoldの概念と実装 | `from sklearn.model_selection import StratifiedKFold`<br>`skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)` |
| **火** | Foldごとのインデックス抽出 | `df['fold'] = -1`<br>`for fold, (trn_idx, val_idx) in enumerate(skf.split(df, df['label'])):`<br>`    df.loc[val_idx, 'fold'] = fold` |
| **水** | 特定のFoldのデータだけを抽出 | `trn_df = df[df['fold'] != current_fold].reset_index(drop=True)`<br>`val_df = df[df['fold'] == current_fold].reset_index(drop=True)` |
| **木** | 5つのモデルの重みの保存 | `torch.save(model.state_dict(), f'model_fold{fold}.pth')` |
| **金** | 5つのモデルの予測値の平均（アンサンブル） | `fold_preds += model(test_images) / 5` |
| **土** | **総復習：5-Foldパイプラインの構築** | データを5分割し、for文で「Fold 0」の学習がスタートするまでのデータ準備を空で書く。 |
| **日** | 予備日・リファクタリング | なぜ単純な分割ではなく「Stratified（層化）」を使うのか（正解ラベルの比率を保つため）を復習。 |

### 12週目：実戦コンペへのアタック（最初のSubmit）
Kaggleの「Digit Recognizer（手書き数字）」や「Cats vs Dogs（犬猫認識）」などの入門用画像コンペティション、あるいは過去の画像分類コンペのデータセットを使って、実際に提出を行います。

| 曜日 | 学習内容 | 意識するポイント |
|---|---|---|
| **月** | コンペデータのダウンロードと確認 | データの形式（画像フォルダか、CSVに画素値が入っているか）を確認する。 |
| **火** | Baselineモデル（最もシンプルな構造）の実装 | 凝ったことはせず、まずは1エポックだけ動くシンプルなコードを書く。 |
| **水** | ローカル環境（またはKaggle Notebook）でのデバッグ | パス違いのエラーや、メモリ不足（OOM）のエラーが出ないか1バッチだけ流す。 |
| **木** | 本番学習の実行と予測値の算出 | 実際に学習を回し、テストデータに対する予測値を計算する。 |
| **金** | 提出用ファイルの出力と形式チェック | `sample_submission.csv` と行数・列名が完全に一致しているか確認する。 |
| **土** | **【ゴール】Kaggleへの初Submit（提出）** | **コードを提出し、Leaderboard（順位表）に自分の名前とスコアが載る快感を味わう。** |
| **日** | スコアの確認と振り返り | 手元の検証データ（Validation）のスコアと、Kaggle上のスコアが連動しているか確認する。 |

## 毎日の戦闘力を支える「Kaggle特化型・絶対暗記コード」
1〜8週目のコードと合わせて、以下の**3つの塊**は、何も見ずに3分以内にタイピングできるようにしてください。

### 1. データ分割（Validationの構築）
手元で正確に実力を測るための「Stratified K-Fold」のインデックス割り当て。

```python
import pandas as pd
from sklearn.model_selection import StratifiedKFold

df = pd.read_csv('train.csv')
df['fold'] = -1

# 5分割、シャッフルあり、再現性のためのシード固定
skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)

# 正解ラベル（'label'列）の比率を維持したまま分割
for fold, (trn_idx, val_idx) in enumerate(skf.split(df, df['label'])):
    df.loc[val_idx, 'fold'] = fold


