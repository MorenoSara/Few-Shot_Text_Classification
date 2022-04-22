# Few-Shot Text Classification
This project is developed during the internship at [LINKS Foundation](https://linksfoundation.com/en/)

Few-shot text classification is a fundamental NLP task in which a model aims to classify text into a large number of categories, given only a few training examples per category.

---
# Zero-shot Text classification
The first addressed task is zero-shot text classification. The underlying idea is to use `sentence-transformers`, in particular the [all-mpnet-base-v2](https://huggingface.co/sentence-transformers/all-mpnet-base-v2), to encode both the documents and all possible labels. Then, each document is associated with the label that has the nearest representation to the one of the document.
