# NLP with Deep Learning - Term Project

## Big Five Personality Recognition using LUKE on RealPersonaChat

### プロジェクト概要

日本語対話データ（RealPersonaChat）を用いて、Big Five性格特性を予測する回帰モデルを構築します。

### データセット

- **RealPersonaChat**: 日本語対話コーパス
  - 対話数: 14,000件
  - 話者数: 233名
  - Big Five性格特性スコア付き（1-7スケール）

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

1. **ノートブックを開く**
   ```
   https://colab.research.google.com/github/wa-ko/Natural-Language-Processing-with-Deep-Learning/blob/main/projects/PersonalityRecognition_RealPersonaChat.ipynb
   ```

2. **GPU有効化**
   - ランタイム → ランタイムのタイプを変更 → T4 GPU

3. **セルを順番に実行**
   - セクション1: 環境セットアップ
   - セクション2: データ読み込み（GitHubから自動取得）
   - セクション3-9: 前処理、モデル構築、学習、評価、可視化

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
