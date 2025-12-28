# Web Mining Capstone Project: APRS - Amazon Product RecSys - Group 10

> *Note: For the full dataset, please direct to this [GGDrive link](https://drive.google.com/drive/folders/1tpj9i3rMBGZ60x9iaY49TMrUyWNtQFd_?usp=sharing).*

***

## Introduction

In an era where e-commerce platforms like Amazon host millions of products, users face a significant challenge known as **information overload**. Finding relevant products effectively has become a critical problem.

**Amazon Product RecSys (APRS)** is our solution to this challenge. This Capstone Project focuses on building a robust Recommendation System using the **Amazon Reviews '23 dataset** (specifically the *Handmade Products* subset). Our goal is to analyze historical user interactions and textual reviews to predict personalized product suggestions.

Our approach integrates three distinct modeling paradigms:
1.  **Collaborative Filtering:** Using ItemKNN as a strong baseline.
2.  **Semantic Analysis:** Leveraging **BLAIR** (based on RoBERTa) to bridge the gap between user language and item metadata.
3.  **Graph Neural Networks:** Utilizing **LightGCL** to capture high-order collaborative signals on the user-item graph.

***This project constitutes the Capstone Project for the course "Web Mining (IT4868E)" at Hanoi University of Science and Technology.***

***

## Applications

- **Personalized Discovery:** Helping users discover niche products they might miss using standard search.
- **Decision Support:** Assisting users in making informed purchasing decisions through relevant suggestions.
- **Platform Optimization:** Increasing user engagement and sales by effectively matching supply with demand.

***

## Key Features

- **Data Preprocessing & Filtering:** - Utilized `preprocess.ipynb` to clean the raw Amazon Reviews '23 data.
  - Applied **k-core filtering (k=3)** to remove inactive users and items, reducing sparsity and ensuring a reliable interaction matrix.

- **Exploratory Data Analysis (EDA):** - Performed comprehensive analysis in `eda.ipynb`.
  - Insights include user interaction dynamics, the "long-tail" Pareto distribution of item popularity, and sentiment bias in ratings.

- **Baseline Modeling (ItemKNN):** - Implemented in `knn.ipynb`.
  - Uses cosine similarity on item content embeddings and masked user rating vectors to generate collaborative recommendations.

- **Semantic-Aware Modeling (BLAIR):** - Implemented in `blair.ipynb`.
  - Adopts the **BLAIR** framework with a **RoBERTa** backbone.
  - Optimizes a joint contrastive learning and masked language modeling objective to align user reviews with product descriptions in a unified semantic space.

- **Graph-Based Modeling (LightGCL):** - Implemented in `lightgcl.ipynb`.
  - Utilizes **Light Graph Contrastive Learning** to simplify graph convolution (preventing over-smoothing) while maximizing the agreement between interaction views.

***

## Project Structure

The repository is organized as follows based on the implemented pipeline:

- **dataset/review_filtered**:
  - `review_filtered.csv`: The main preprocessed dataset used for modeling.
  - `train.csv`, `test.csv`, `valid.csv`: Split datasets for training and evaluation.

- **models**:
  - `knn.ipynb`: Implementation and experiments for the ItemKNN baseline.
  - `blair.ipynb`: Implementation of the BLAIR semantic model.
  - `lightgcl.ipynb`: Implementation of the LightGCL graph neural network.

- **util**:
  - `eda.ipynb`: Notebook for visualizing data distributions (ratings, popularity, sparsity).
  - `preprocess.ipynb`: Scripts for data cleaning, k-core filtering, and splitting.

- **results**:
  - Contains output files (`knn.csv`, `blair.csv`, `lightgcl.csv`) storing the recommendation predictions.

- **README.md**:
  - Project documentation and overview.

***

## 📊 Data Analytics Dashboard

To understand the dataset dynamics and the impact of our preprocessing steps, we constructed executive dashboards comparing the **Original (Raw)** dataset versus the **Filtered** dataset used for modeling.

### 1. Original Dataset (Raw)
This dashboard represents the full scope of the *Handmade Products* category before cleaning.
![Raw Dataset Dashboard](https://github.com/user-attachments/assets/3706eb32-7e6b-4087-baf5-2cb24f08fbb0)
> *Note: The raw dataset contains over 586k users and 164k products, but suffers from extreme sparsity (99.99%) and single-interaction noise.*

### 2. Filtered Dataset (Target)
This dashboard shows the dataset after applying **k-core filtering (k=3)**. This is the high-quality subset used to train our BLAIR and LightGCL models.
![Filtered Dataset Dashboard](https://github.com/user-attachments/assets/7a258c70-1e2f-46dd-b76a-534990061f52)
> *Key Insight: Post-filtering, the Average Rating increased from **4.50** to **4.70**. This indicates that active users (who leave >3 reviews) tend to rate products more positively, a bias we accounted for in our analysis.*

***

## Acknowledgments

We would like to express our sincere gratitude to our lecturer, **Ph.D. Nguyen Kiem Hieu**, for his invaluable guidance and support throughout the **Web Mining (IT4868E)** course. His expertise was instrumental in shaping the direction of this project.

We also acknowledge the authors of the **Amazon Reviews '23** dataset and the open-source community behind the BLAIR and LightGCL frameworks.

***

## Contributors

**Group 07 - Class IT4036E**

- **Member 1:** Đàm Quang Đức - 20225483
- **Member 2:** Lại Trí Dũng - 20225486
- **Member 3:** Vũ Hữu An - 20225467
- **Member 4:** Nguyễn Trọng Tâm - 20225527
- **Member 5:** Nguyễn Tiếng Thắng - 20225530

***

## License

This project is licensed under the [MIT License](LICENSE).
