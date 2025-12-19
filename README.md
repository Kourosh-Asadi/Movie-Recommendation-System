# Movie Recommendation System

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.5-green?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.24-blue?logo=numpy&logoColor=white)](https://numpy.org/)

This repository contains a Jupyter Notebook implementation of a movie recommendation system using collaborative filtering and content-based filtering techniques. The project demonstrates data preprocessing, feature engineering, and recommendation algorithms applied to real-world movie rating data. It is designed to showcase skills in machine learning, data analysis, and Python programming, suitable for academic and research purposes.

## Project Overview

The goal of this project is to build a recommendation engine that suggests movies to users based on their preferences and historical ratings. Two primary approaches are implemented:
- **Content-Based Filtering**: Recommends movies similar to those the user has liked, based on features like genres and release year.
- **Collaborative Filtering**: Uses user-item interactions (ratings) to find similarities between users or items and generate personalized recommendations.

The system processes user input (e.g., preferred genres) and outputs a list of top recommended movies, ranked by a weighted average recommendation score.

This work highlights proficiency in handling large datasets, implementing recommendation algorithms, and evaluating model performance—skills relevant to research in recommender systems, machine learning, and data science.

## Dataset

The dataset is sourced from the [MovieLens](https://grouplens.org/datasets/movielens/) collection (small version for demonstration):
- **movies.csv**: Contains movie metadata, including `movieId`, `title`, and `genres` (e.g., "Adventure|Animation|Children|Comedy|Fantasy").
- **ratings.csv**: Includes user ratings, with columns `userId`, `movieId`, `rating` (scale: 0.5–5.0), and `timestamp`.

Key statistics:
- ~9,700 movies
- ~100,000 ratings from ~600 users

Data preprocessing steps include:
- Extracting release years from titles using regular expressions.
- One-hot encoding genres for feature representation.
- Handling missing values and filtering low-rated movies.

## Features

- **Data Cleaning**: Regex-based extraction of years, genre splitting, and creation of binary genre columns.
- **User Input Handling**: Allows users to specify preferences (e.g., genres) via a simple interface.
- **Recommendation Algorithms**:
  - Content-based: Computes similarity using cosine distance on genre vectors.
  - Collaborative: Calculates weighted averages based on user ratings and item popularity (using formulas like IMDb's weighted rating: \( v = \frac{R \cdot v + C \cdot m}{v + m} \), where \( R \) is average rating, \( v \) votes, \( m \) minimum votes, \( C \) mean vote across dataset).
- **Output**: Top 20 recommended movies with titles, genres, years, and scores (filtered for scores > 3.5).

## Installation

To run this project locally:

1. Clone the repository:
   ```
   git clone https://github.com/your-username/movie-recommendation-system.git
   cd movie-recommendation-system
   ```

2. Install dependencies using pip (Python 3.11 recommended):
   ```
   pip install -r requirements.txt
   ```
   (If `requirements.txt` is not present, install manually: `pip install pandas numpy jupyter`)

3. Launch Jupyter Notebook:
   ```
   jupyter notebook REC_SYS_MOVIE.ipynb
   ```

## Usage

1. Open `REC_SYS_MOVIE.ipynb` in Jupyter.
2. Run cells sequentially to load data, preprocess, and build the model.
3. Input user preferences (e.g., genres like "Adventure|Comedy") when prompted.
4. View recommendations in the output cells, including a sorted DataFrame of top movies.

Example output:
| movieId | title                          | genres                  | year | weightedAverageRecommendationScore |
|---------|--------------------------------|-------------------------|------|------------------------------------|
| 140265 | George Carlin: Jammin' in New York | [Comedy]               | 1992 | 5.0                                |
| 1956   | Ordinary People                | [Drama]                | 1980 | 5.0                                |
| ...    | ...                            | ...                    | ...  | ...                                |

## Methodology

1. **Data Loading and Preprocessing**:
   - Load CSVs using Pandas.
   - Extract years with regex: `mdf['year'] = mdf.title.str.extract('(\\(\\d\\d\\d\\d\\))', expand=False)`.
   - Split genres into lists and one-hot encode for similarity computation.

2. **Content-Based Recommendation**:
   - Create a genre matrix.
   - Compute cosine similarity between movies.
   - Recommend based on user-liked movies.

3. **Collaborative Filtering**:
   - Build a user-item rating matrix.
   - Calculate weighted averages to handle sparsity and bias.
   - Filter and sort recommendations (>3.5 score).

4. **Evaluation**:
   - Qualitative: Comparison of recommendations from both methods shows overlap in high-quality suggestions.
   - Potential extensions: RMSE for quantitative evaluation (not implemented here).

This implementation draws from standard recommender system literature, emphasizing scalability and interpretability.

## Results

- The system effectively recommends movies aligned with user preferences.
- Content-based excels in genre matching; collaborative captures user similarities.
- Example: For a user preferring comedies, top picks include classics like "Toy Story" and high-rated outliers like "George Carlin: Jammin' in New York".

Limitations: Cold-start problem for new users/items; scalability for larger datasets could be improved with Spark or matrix factorization (e.g., SVD).

## Conclusion

This project serves as a practical demonstration of building end-to-end recommendation systems, integrating data engineering and machine learning. It is extensible for advanced techniques like neural collaborative filtering or hybrid models. For academic applications, it underscores experience in Python-based ML workflows and algorithmic problem-solving.

If you're an academic reviewer, feel free to contact me for discussions on enhancements or collaborations.


## About the Author

Kourosh Asadi is a 3rd-semester Bachelor's student in Computer Engineering at Tehran Azad university south branch. His primary interests include machine learning, data science, and artificial intelligence applications, with a focus on recommender systems and practical implementations of ML algorithms.

This movie recommendation system project was developed as part of self-study to deepen understanding of collaborative and content-based filtering techniques. It demonstrates hands-on experience with data preprocessing, feature engineering, and building end-to-end ML pipelines using Python.

## References

- GroupLens Research. (2018). MovieLens Dataset. https://grouplens.org/datasets/movielens/
- Koren, Y., et al. (2009). Matrix Factorization Techniques for Recommender Systems. IEEE Computer.
- Inspired by tutorials on Towards Data Science and Kaggle kernels on recommendation systems.

---

This README is licensed under [MIT License](LICENSE). For questions, open an issue or email Kouroshasadi244@gmail.com
