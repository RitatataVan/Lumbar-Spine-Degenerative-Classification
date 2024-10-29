# RSNA 2024 Lumbar Spine Degenerative Classification

![LLM](https://github.com/user-attachments/assets/be8f32cc-da26-4866-9d14-caf121cc2192)

## Objective
The aim is to build a model to aid in the detection and classification of degenerative spine conditions using lumbar spine MR images.
The challenge focused on the classification of five lumbar spine degenerative conditions: Left Neural Foraminal Narrowing, Right Neural Foraminal Narrowing, Left Subarticular Stenosis, Right Subarticular Stenosis, and Spinal Canal Stenosis. It provided severity scores (Normal/Mild, Moderate, or Severe) for each of the five conditions across the intervertebral disc levels L1/L2, L2/L3, L3/L4, L4/L5, and L5/S1.

## Data
Knowledge Corpus：https://www.kaggle.com/datasets/mbanaei/all-paraphs-parsed-expanded <br>
https://www.kaggle.com/datasets/mbanaei/stem-wiki-cohere-no-emb <br>
https://www.kaggle.com/datasets/jjinho/wikipedia-20230701 <br>
Samples：https://www.kaggle.com/datasets/cdeotte/60k-data-with-context-v2 <br>
https://www.kaggle.com/datasets/cdeotte/40k-data-with-context-v2 <br>
https://www.kaggle.com/datasets/cdeotte/99k-data-with-context-v2 <br>

## Resources
Gte-base: https://huggingface.co/thenlper/gte-base <br>
Faiss: https://github.com/facebookresearch/faiss <br>
deberta-v3-large: https://huggingface.co/microsoft/deberta-v3-large <br>

## Methods
-	Built a **LangChain** pipeline to generate multiple-choice questions from Wikipedia text using GPT-3.5.
-	Generated embeddings for texts using **gte-base** model and created indexes with Faiss (Facebook AI Similarity Search) for efficient querying.
-	Performed semantic similarity search using Inner Product (IP) similarity to retrieve Top 10 relevant texts, leveraging the results as external knowledge for context-based generation.
-	Fine-tuned **DeBERTa-v3-large** model from Hugging Face to predict question answers, incorporating **RAG**.
