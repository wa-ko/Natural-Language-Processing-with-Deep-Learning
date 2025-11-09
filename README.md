# NLP with Deep Learning - Term Project

## Big Five Personality Recognition using LUKE on RealPersonaChat

### プロジェクト概要

日本語対話データ（RealPersonaChat）を用いて、Big Five性格特性を予測する回帰モデルを構築します。

### データセット

- **RealPersonaChat**: 日本語対話コーパス
  - 対話数: 14,000件（全データ使用）
  - 話者数: 233名
  - Big Five性格特性スコア付き（1-7スケール）
  - モノローグサンプル: 約27,000件（推定）

### モデル

- **LUKE (Language Understanding with Knowledge-based Embeddings)**
  - モデル: `studio-ousia/luke-japanese-base`
  - タスク: 回帰（Big Five 5特性の同時予測）
  - 設定: モノローグ（話者の発話のみ）

### 評価指標

**回帰指標:**
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- Pearson相関係数
- Spearman相関係数

**分類指標（中央値二値化）:**
- Accuracy
- Balanced Accuracy
- Precision, Recall, F1

### Google Colabでの実行方法

#### 初回実行（フル実行）

1. **ノートブックを開く**
   ```
   https://colab.research.google.com/github/wa-ko/Natural-Language-Processing-with-Deep-Learning/blob/main/projects/PersonalityRecognition_RealPersonaChat.ipynb
   ```

2. **GPU有効化**
   - ランタイム → ランタイムのタイプを変更 → T4 GPU

3. **Google Driveをマウント**
   - セル2を実行してGoogle Driveに接続（データキャッシュ用）

4. **セルを順番に実行**
   - セル1-3: ライブラリインポート
   - **セル4-5: キャッシュ管理（手動実行専用 - 通常はスキップ）**
   - セル6-18: データ読み込み、前処理、モデル構築
     - **注意**: 初回データ読み込みは30-40分かかります（14,000対話）
     - 2回目以降はキャッシュから5秒で読み込み
   - セル18: 前処理済みデータを自動保存（次回から高速再開可能）
   - セル21: 学習ループ実行（約20-30分）

#### キャッシュ管理（重要）

**セル4: キャッシュ削除機能**
- **Run Allでは実行されません**（手動実行専用）
- 古いキャッシュファイル（例：1,000対話版）を削除する場合に使用
- 使い方：
  1. セル4を**個別に**手動実行
  2. キャッシュファイル一覧が表示される
  3. 削除したいファイル番号を入力（例：`1,2` または `all`）
  4. Enterキーでキャンセル

**キャッシュ削除が必要な場合：**
- データ量を変更した場合（1,000→14,000対話など）
- データが破損した疑いがある場合
- 古いキャッシュが残っている場合

#### 学習ループで落ちた場合の高速再開（推奨）

学習中にメモリエラーなどで落ちた場合、以下の手順で時間を大幅に節約できます：

1. **ランタイムを再起動**
   - ランタイム → セッションを管理 → すべて終了
   - ランタイム → ランタイムのタイプを変更 → T4 GPU

2. **最小限のセルのみ実行**
   - セル1-3: ライブラリインポート（30秒）
   - セル20: キャッシュから復元（30秒）
   - セル21: 学習ループ実行

**メリット:** データ読み込み・前処理（5-10分）をスキップ可能！

### ファイル構成

```
.
├── projects/
│   └── PersonalityRecognition_RealPersonaChat.ipynb  # メインノートブック
├── maaterial/
│   ├── RealPersonaChat.pdf
│   └── Enhancing Personality Recognition in Dialogue...pdf
└── README.md
```

### 参考文献

- Yamashita et al. (2023). "RealPersonaChat: A Realistic Persona Chat Corpus with Interlocutors' Own Personalities"
- Fu et al. (2024). "Enhancing Personality Recognition in Dialogue by Data Augmentation and Heterogeneous Conversational Graph Networks"

### 発表予定

- 日時: 2024年11月25日（火）または28日（金）
- 形式: Zoom発表

---

**License**: CC-BY-SA 4.0 (RealPersonaChat dataset)
