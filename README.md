# Biomedical clustering evaluation

Work done for my [Bachelor's thesis](https://amslaurea.unibo.it/id/eprint/29686).

Evaluation of clustering algorithms on biomedical abstracts
using internal metrics (Silhouette, Calinski-Harabasz, Davies-Bouldin).

Different combinations of the following methods have been experimented.
| Step           | Methods |
|----------------|---------|
| Text embedding | Bag-of-words<br/>Word2vec<br/>GloVe<br/>fastText<br/>BioWordVec<br/>MiniLM<br/>BioBERT<br/>PubMedBERT
| Dimensionality reduction | PCA<br/>LSA<br/>NMF<br/>UMAP
| Clustering | K-means<br/>Bisecting k-means<br/>Agglomerative<br/>DBSCAN<br/>OPTICS<br/>HDBSCAN


## Dataset creation
The evaluation dataset is created using PubMed abstracts.
Each entry of the dataset contains articles related to a disease.

`pmids.json` contains the PMIDs of the articles of an already defined dataset.\
To fetch the actual abstracts, run:
```
python dataset_fetch.py --pmids=pmids.json --output=<output-path>
```

To create a custom dataset with different diseases, 
create a file with the wanted diseases (one per line) and run:
```
python dataset_pmids.py --diseases-list=<path-to-list> --output=<output-path>
```
The output contains the PMIDs of the dataset, which can be passed to `dataset_fetch.py`.


## Evaluation
To start the evaluation, run:
```
python eval.py --dataset=<path-to-dataset> --embedding=<embedding>
```
Available values of `<embedding>` are 
`bow`, `word2vec`, `glove`, `fasttext`, `biowordvec`, `minilm`, `biobert`, `pubmedbert`.
