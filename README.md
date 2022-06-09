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

2. `Finetune the sentence transformer`: the whole sentence transformer is finetuned, without a classifier on top. The model is tested on a subset of 2000 documents. Observe from the following figures the importance of the hyperparameters for this model. In both the images the blu curve is obtained with ST-C.

The first figure is obtained with the trade-off selection technique. The orange curve is found with a manual ispection of hyperparameters, the green one with [W&B](https://wandb.ai/site) tool, the red one with some standard parameters traditionally used.

![Tradeoff_hyper](https://user-images.githubusercontent.com/89184723/172878398-00495294-006c-4883-ac6d-6af8abc980b4.jpg)

The second image reports the results obtained with the same hyperparameters but with the medoids selection technique.

![Medoids_hyper](https://user-images.githubusercontent.com/89184723/172878384-d14885a5-4262-45a4-ba5a-13c5a5e8ebd9.jpg)
