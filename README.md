🎬 Movie Recommender System


Welcome to the Movie Recommender System, a Streamlit-based web application that suggests similar movies based on your selection. This project uses content-based filtering with precomputed similarity scores to recommend movies and display their posters interactively.


Features
-Select a movie from a dropdown
-Get 5 similar movie recommendations
-Movie posters fetched dynamically using TMDB API
-Built using cosine similarity on movie metadata

Simple and elegant UI powered by Streamlit

Tech Stack
Python 3
Streamlit – web app framework
Pandas & NumPy – data processing
Scikit-learn – cosine similarity
TMDB API – fetch movie posters

Project Structure

<img width="454" alt="image" src="https://github.com/user-attachments/assets/6a13d26e-7f12-4c2f-9c67-8bcb52021999" />


How the Recommendation Engine Works

To generate accurate recommendations, we used a content-based filtering approach that creates a "tag" for each movie. Here's how:

Data Preprocessing Steps

Merged datasets: Combined tmdb_5000_movies.csv and tmdb_5000_credits.csv using the title.

Selected meaningful columns:

['movie_id', 'title', 'overview', 'genres', 'keywords', 'cast', 'crew']

Transformed data:

Used ast.literal_eval() to parse stringified lists in genres, keywords, cast, and crew.

Extracted:
Top 3 cast members
Director from crew
Tokenized and split overview text

Cleaned tokens:
Removed spaces in names: "Sam Worthington" → SamWorthington
Converted everything to lowercase
Joined all data into a single tag column

Example tag:
wizard magic school fantasy emmawatson danielradcliffe rupertgrint chriscolumbus

Vectorization:
Used CountVectorizer(max_features=5000, stop_words='english') from scikit-learn to convert tags to numeric vectors

Similarity calculation:
Applied cosine similarity to find the top 5 most similar movies based on tag vectors


Setup Instructions
1. Clone the repo
git clone https://github.com/YourUsername/movie_recommender_system.git
cd movie_recommender_system

2. Install dependencies
pip install -r requirements.txt

3. Download or generate similarity.pkl
Due to GitHub’s file size limits, the file similarity.pkl (≈176MB) is not included in this repository.

You can either:

Recompute it using the notebook Movie_reccomender_system.ipynb, or
Once you have it, place it in the root folder.

4. Run the app
streamlit run app.py

How It Works
-The user selects a movie title from the dropdown.
-A cosine similarity matrix is used to find the top 5 most similar movies.
-The TMDB API fetches poster images based on each movie’s ID.
-Recommendations are displayed visually with titles and posters.

Example
If you select:
🎥 Harry Potter and the Goblet of Fire

<img width="605" alt="image" src="https://github.com/user-attachments/assets/3a1d6608-cf94-4c25-ac3f-a80a00b4dc52" />

Each with poster images fetched live!

TMDB API Key
This app uses TMDB (The Movie Database) API to fetch posters.
You must generate your own key:
Sign up at: https://www.themoviedb.org
Go to Settings → API → Create API Key
Add your API key in the fetch_poster() function in app.py
api_key = 'your_api_key_here'

Requirements
streamlit
pandas
numpy
scikit-learn
requests

TFuture Improvements
 Add movie genres and descriptions
 Use collaborative filtering (via surprise or implicit)
 Add search by keyword or actor
 Deploy on Render or Hugging Face Spaces

Contributing
Feel free to fork the repo and submit PRs to improve the recommendations, UI, or backend logic. Ypu can reach out to me over email-id: ps3246@drexel.edu
