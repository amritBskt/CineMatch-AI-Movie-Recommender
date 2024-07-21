# CineMatch-AI-Movie-Recommender

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Model](#model)
- [Predictions](#predictions)
- [Contributing](#contributing)
- [License](#license)


## Overview

This project implements a content-based filtering recommender system using a neural network to recommend movies. The system leverages movie features like genres and titles to provide personalized recommendations, addressing the cold-start problem and enhancing user engagement on streaming platforms.


## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/amritBskt/CineMatch-AI-Movie-Recommender.git
    cd CineMatch-AI-Movie-Recommender
    ```

2. Create a virtual environment and activate it:
    ```bash
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Navigate to the `notebooks` directory:
    ```bash
    cd notebooks
    ```

2. Launch Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

3. Open and run the `CineMatch.ipynb` notebook to see the implementation and results.

## Dataset

The dataset used in this project is derived from the [MovieLens ml-latest-small](https://grouplens.org/datasets/movielens/latest/) dataset.

## Model

A neural network is implemented using TensorFlow to perform content-based filtering. The model is trained to predict user ratings based on movie features.

```python
model = tf.keras.Sequential([
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(64, activation='relu'),
    tf.keras.layers.Dense(1)
])

model.compile(optimizer='adam', loss='mse')
```

## Predictions

The notebook includes methods to generate personalized movie recommendations for both new and existing users and to identify similar movies.

```python
def predict_for_new_user(user_preferences):
    return model.predict(user_preferences)

def predict_for_existing_user(user_id):
    user_data = ratings[ratings['userId'] == user_id]
    return model.predict(user_data)

def find_similar_items(movie_id):
    movie_data = movies[movies['movieId'] == movie_id]
    return model.predict(movie_data)
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
