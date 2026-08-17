**Movie Recommender System — Hybrid Collaborative Filtering**

**Overview:** Built a full-stack movie recommendation engine on the MovieLens 100K dataset (943 users, 1,682 movies), progressing from user-based collaborative filtering through matrix factorization and knowledge-based recommenders, culminating in an adaptive hybrid system.

###Part 1: User-Based Collaborative Filtering
- Constructed user-item rating matrix and analyzed sparsity
- **Model 1 (KNN baseline):** Similarity computed on co-rated items only; predictions via weighted average of k most similar users (positive similarity only)
- **Model 2 (Cluster-based KNN):** Applied K-means clustering with K-means++ initialization to group users, using cluster-mates as the neighbor pool for prediction, with fallback handling for sparse clusters
- Evaluated both models via RMSE across different k/cluster values

**Part 2: Matrix Factorization*
- Implemented SVD-based collaborative filtering (`TruncatedSVD` / `scipy.sparse.linalg.svds`)
- Compared RMSE and computational cost vs. number of latent factors, benchmarked against best Part 1 model

**Part 3: Knowledge-Based Recommender**
- Built a preference elicitation interface (genre, release year range, minimum rating, runtime)
- Content-based scoring combining genre overlap (50%), year match (30%), and rating threshold (20%)
- Generated top-3 recommendations per profile with human-readable explanations

**Part 4: Hybrid System**
- Adaptive weighting based on user rating history:
  - New users → knowledge-based only
  - <5 ratings → KB 80% / CF 20%
  - 5–20 ratings → CF 60% / KB 40%
  - \>20 ratings → CF 80% / KB 20%
- Normalized and combined CF/KB scores with fallback handling for method failures

**Part 5: Evaluation**
- Comparative performance analysis across all methods, discussion of scalability, failure modes, and potential improvements

**Tech stack:** Python, Pandas, NumPy, SciPy (sparse matrices, SVD), scikit-learn (KNN, K-means, TruncatedSVD)

**Documents**




[View the Project Question in Document format](Collaborative Filtering Assignment.pdf)

[View the Project in Document format - Part 1](docs/ML2_Prj1_Part1_Setup_CF_KNN.pdf)
[View the Project in Document format - Part 2](docs/ML2_Prj1_Part2_cluster_knn.pdf)
[View the Project in Document format - Part 3](docs/ML2_Prj1_Part3_svd_matrix_factorization.pdf)
[View the Project in Document format - Part 4](docs/ML2_Prj1_Part4_knowledge_based.pdf)
[View the Project in Document format - Part 5](docs/ML2_Prj1_Part5_hybrid_integration.pdf)
[View the Project in Document format - Part 6](docs/ML2_Prj1_Part6_Final_Report_Notebook.pdf)




------------------------------------------------------------------------------
Important Note:
------------------------------------------------------------------------------
This is the order of the notebooks
* data_and_knn.ipynb
* 02_cluster_knn.ipynb
* 03_svd_matrix_factorization.ipynb
* 04_knowledge_based.ipynb
* 05_hybrid_integration.ipynb
* Final_Report_Notebook

The data is present in the "data" folder

------------------------------------------------------------------------------

