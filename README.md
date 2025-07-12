# Overview
Experimented 3 approaches for semantic text similarity task in which given 2 sentences, need to assign a similarity score from range 0 to 5 with higher score implying higher semantic similarity
## Approach - 1 
1. Used doc2vec to create non-contextual embeddings for sentence1 and sentence2
2. Created an ml pipeline utilizing sklearn's polynomialfeatures to increase feature size and help model learn non-linear relationships, followed by a linear regression model

## Approach - 2
1. Used roberta-base-v2 to create contextual embeddings for sentence1 and sentence2
2. Utilized linear regression to predict similarity score

## Approach - 3
1. Finetuned roberta-base-v2 model by adding pooling and dense layers and training them along with the last layer of roberta

# Comparison
Compared approaches based on spearman correlation between predicted scores and ground truths. Finetuning roberta results in best performance

| Approach | Training set spearman correlation | Dev set spearman correlation | Test set spearman correlation |
| --- | --- | --- | --- |
| Approach-1 | 0.504 | 0.418 | 0.304 |
| Approach-2 | 0.391 | 0.157 | 0.271 |
| Approach-3 | 0.809 | 0.831 | 0.815 |
