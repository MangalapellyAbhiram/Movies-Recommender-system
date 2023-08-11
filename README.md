# Movies-Recommender-system
**Dataset**
The dataset used for this project is the TMDB 5000 Movie Dataset, which contains information about 5000 movies from The Movie Database (TMDB).The dataset consists of two files: tmdb_5000_movies.csv and tmdb_5000_credits.csv. The first file contains metadata such as movie title, genres, keywords, budget, revenue, popularity, vote count, vote average, release date, runtime, and overview. The second file contains cast and crew information such as actor name, character name, director name, and producer name.

**Approach**
The approach used for this project is to create a movie similarity matrix based on the movie features, such as genres, keywords, cast, crew, and overview. The idea is to represent each movie as a vector of features, and then compute the cosine similarity between any two movies based on their feature vectors. Cosine similarity is a measure of how similar two vectors are in terms of their orientation, regardless of their magnitude. The higher the cosine similarity, the more similar the movies are.

To create the feature vectors, the following steps are performed:

1)The genres and keywords columns are converted from JSON format to a list of strings.

2)The cast and crew columns are merged with the movies dataframe using the movie_id column as the key.

3)The top three actors, the director, and the producer are extracted from the cast and crew columns and added as new columns to the movies dataframe.

4)The overview column is cleaned by removing stopwords, punctuation, and numbers using NLTK library.

5)The TF-IDF (term frequency-inverse document frequency) matrix is computed for the overview column using Scikit-learn library. TF-IDF is a way of weighting words based on how frequently they appear in a document and how rare they are across all documents. This helps to capture the importance and uniqueness of words in each movie overview.

6)The genres, keywords, cast, crew columns are concatenated into a single column called soup, which contains all the relevant features for each movie.

7)The count matrix is computed for the soup column using Scikit-learn library. Count matrix is a way of counting how many times each word appears in each document. This helps to capture the frequency of features for each movie.

8)The feature vectors are created by combining the TF-IDF matrix and the count matrix using Scikit-learn library. This results in a sparse matrix where each row represents a movie and each column represents a feature.

9)The cosine similarity matrix is computed for the feature vectors using Scikit-learn library. This results in a square matrix where each cell represents the similarity score between two movies.
