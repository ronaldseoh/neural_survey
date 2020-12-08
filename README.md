# Neural Survey

This repository contains the codes used to produce the results from the paper *Neural Survey: Efficient End-to-End Opinion Retrieval with BERT-based Embeddings*.

## Prerequisites

Before running any notebooks in this repository, please install the required packages using `pip`:

```bash
pip install -r requirements.txt
```

If you are using [Google Colab](https://colab.research.google.com) to execute the codes, commands for package installations are already added to the notebooks. However, you need to mount your Google Drive folders for proper functionality of our codes.

In addition, the dataset files from the SemEval 2014 Task 4 workshop need to be downloaded. Please download the [training data](http://metashare.ilsp.gr:8080/repository/browse/semeval-2014-absa-train-data-v20-annotation-guidelines/683b709298b811e3a0e2842b2b6a04d7c7a19307f18a4940beef6a6143f937f0/) and [test data](http://metashare.ilsp.gr:8080/repository/browse/semeval-2014-absa-test-data-gold-annotations/b98d11cec18211e38229842b2b6a04d77591d40acd7542b7af823a54fb03a155/) and store them in `data/SemEval2014_Task4`.

## Notebook Descriptions

All the notebooks are used to produce our main results found in Table 2. **It is recommended to run the notebooks in the order in which they appear below:**

### BM25

- `01_create_pyserini_index.ipynb`: Use this to generate Pyserini collections, test queries, and relevance judgements out of the SemEval test datasets.
- `02_run_bm25.ipynb`: Produce the query results with BM25.

### Data

- `create_dataset.ipynb`: Generate training data for the Siamese network using contrastive and online contrastive loss function.
- `create_dataset_partially_correct_cosine.ipynb`: Generate training data for the Siamese network using cosine loss function.
- `create_dataset_partially_correct_softmax.ipynb`: Generate training data for the Siamese network using softmax loss function.

### Siamese

- `sentence_bert_contrastive.ipynb`: Train the Siamese network with contrastive loss function, and perform k-NN search to generate query results.
- `sentence_bert_online_contrastive.ipynb`: Train the Siamese network with online contrastive loss function, and perform k-NN search to generate query results.
- `sentence_bert_cosine.ipynb`: Train the Siamese network with cosine loss function, and perform k-NN search to generate query results.
- `sentence_bert_softmax.ipynb`: Train the Siamese network with softmax loss function, and perform k-NN search to generate query results.

### Merge

- `merge.ipynb`: Merge the query results from BM25 and Siamese.

**NOTE**: All the evaluation metrics are calculated using [`trec_eval`](https://github.com/usnistgov/trec_eval). You can obtain your copy from the link.

## License

`neural_survey` is licensed under Apache 2.0 license. Please check `LICENSE`.