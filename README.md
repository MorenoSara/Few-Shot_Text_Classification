# Few-Shot Text Classification
This project is developed during the internship at [LINKS Foundation](https://linksfoundation.com/en/)

Few-shot text classification is a fundamental NLP task in which a model aims to classify text into a large number of categories, given only a few training examples per category.

---
# Zero-shot Text classification
The first addressed task is zero-shot text classification. The underlying idea is to use `sentence-transformers`, in particular the [all-mpnet-base-v2](https://huggingface.co/sentence-transformers/all-mpnet-base-v2), to encode both the documents and all possible labels. Then, each document is associated with the label that has the nearest representation to the one of the document.

---
# Few-shot Text Classification
Two different approaches are proposed.
1. `Train a classifier on top of the freezed sentence transformer`. For the examples selection several techniques have been tested; 

![final_plot_results](https://user-images.githubusercontent.com/89184723/172801005-1a345d96-f4d5-4eee-9363-3493e7fe9245.jpg)
  
The best results are obtained selecting the centroids within all the domains, having balanced distributions. However, this solution needs a labeled training data. The only technique that do not involeves labels for the selection of the examples is the one that uses the clusters among the whole training data, irrispectively of the labels. This techniques lead to an unbalanced distribution among classes, however, execpt for low number of shots, the performances achieved with this fashon of selection are comparable to those obtained considering the labels.

2. `Finetune the sentence transformer`: the whole sentence transformer is finetuned, without a classifier on top.
