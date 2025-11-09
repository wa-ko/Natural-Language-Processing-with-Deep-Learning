# Big Five Personality Recognition using LUKE on RealPersonaChat

## Overview

This project implements Big Five personality trait prediction using the LUKE (Language Understanding with Knowledge-based Embeddings) model on the RealPersonaChat dataset.

## Dataset

- **Source**: [RealPersonaChat](https://github.com/nu-dialogue/real-persona-chat)
- **Size**: 14,000 dialogues from 233 speakers
- **Labels**: Big Five personality traits (1-7 scale)
  - Openness
  - Conscientiousness
  - Extraversion
  - Agreeableness
  - Neuroticism

## Model

- **Base Model**: `studio-ousia/luke-japanese-base`
- **Architecture**: LUKE encoder + 5 regression heads (one per trait)
- **Task**: Multi-output regression

## Requirements

- Python 3.8+
- PyTorch
- Transformers
- scikit-learn
- Google Colab with T4 GPU (recommended)

## Usage

### Google Colab (Recommended)

1. Open the notebook in Google Colab:
   ```
   https://colab.research.google.com/github/wa-ko/Natural-Language-Processing-with-Deep-Learning/blob/main/projects/PersonalityRecognition_RealPersonaChat.ipynb
   ```

2. Enable GPU:
   - Runtime → Change runtime type → T4 GPU

3. Execute all cells in order

### Local Execution

```bash
# Install dependencies
pip install torch transformers scikit-learn pandas numpy matplotlib seaborn tqdm

# Run the notebook
jupyter notebook projects/PersonalityRecognition_RealPersonaChat.ipynb
```

## Configuration

### Data Loading

- **Full dataset**: Set `num_dialogues = 14000` (30-40 minutes download)
- **Quick test**: Set `num_dialogues = 1000` (2-3 minutes download)

### Training Parameters

- Batch size: 4
- Gradient accumulation: 8 (effective batch size: 32)
- Learning rate: 1e-5
- Max epochs: 20
- Early stopping patience: 5

## Evaluation Metrics

### Regression Metrics
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- Pearson correlation
- Spearman correlation

### Classification Metrics (High/Low by median)
- Accuracy
- Balanced Accuracy
- Precision, Recall, F1

## Expected Results

The model should achieve comparable performance to the baseline:
- **Target**: ~60.4% balanced accuracy (Fu et al. 2024)

## References

- Yamashita et al. (2023). "RealPersonaChat: A Realistic Persona Chat Corpus with Interlocutors' Own Personalities"
- Fu et al. (2024). "Enhancing Personality Recognition in Dialogue by Data Augmentation and Heterogeneous Conversational Graph Networks"

## License

This project uses the RealPersonaChat dataset, which is licensed under CC-BY-SA 4.0.
