---
Parent MOC: "[[Human Language Technology (HLT)]]"
tags:
  - HLT
  - ERC
---
# Emotion Recognition in Conversation (ERC)

1. [[Lexicons for Sentiment, Affect, and Connotation]]
	1. [[Affective meaning]]
	2. [[Tassonomie delle emozioni]]
	3. [[Affect Lexicon]]
		1. [[Affect Lexicon - Lessici binari]]
		2. [[Affect Lexicon - Lessici dimensionali (VAD)]]
		3. [[Affect Lexicon - Lessici categoriali]]
	4. [[Tecniche Semi-supervised per Affect Lexicon]]
	5. [[Tecniche supervisionate per Affect Lexicon]]
## Papers  📒
1.  [Paper ERC](https://arxiv.org/abs/1905.02947)
2. [BiosERC](https://link.springer.com/chapter/10.1007/978-3-031-72344-5_19)
3. [Transformer-based with self-distillation](https://arxiv.org/pdf/2310.20494v1)

### Datasets
1. [IEMOCAP](https://www.kaggle.com/datasets/dejolilandry/iemocapfullrelease)
2. [MELD](https://www.kaggle.com/datasets/zaber666/meld-dataset)
3. [DailyDialog](https://www.kaggle.com/datasets/thedevastator/dailydialog-multi-turn-dialog-with-intention-and)

### Libraries and Models
1. [RoBERTa](https://huggingface.co/docs/transformers/model_doc/roberta)
2. [Hugging Face](https://huggingface.co/)
3. [NLTK](https://www.nltk.org/)
4. [BiosERC](https://huggingface.co/phuongnm94/BiosERC/blob/main/README.md?code=true#L2)

#### Modelli famosi usati in ERC:

- **DialogRNN** (con RNN e attenzione)
    
- **BERT-based models** (fine-tuned su ERC datasets)
    
- **DialogueGCN** (Graph + Transformer)
    
- **EmoBERTa** (RoBERTa + ERC-specific tuning)