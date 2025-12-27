# FINAL PROJECT
## COURSE: CSC17104 – PROGRAMMING FOR DATA SCIENCE

---

## 1. Project Overview
This project analyzes data from the **Goodreads Choice Awards (2011-2024)** to understand what makes a book successful. We explore how factors like **Author Reputation**, **Pricing**, **Format (Audiobooks)**, and **Genre** influence a book's popularity. Finally, we build a Machine Learning model to predict a book's commercial reach before it is released.

| **Group** | **19** |
| :--- | :--- |
| **Student 1:** | Châu Đình Phúc - 23127247 |
| **Student 2:** | Nguyễn Hiệp Thắng - 23127305 |
| **Class:** | 23KHDL |

---

## 2. Dataset Description
*   **Source:** [Goodreads Choice Awards 2011-2024 (Kaggle)](https://www.kaggle.com/datasets/krisbruurs/goodreads-choice-awards-2011-2024-books)
*   **Author:** Kris Bruurs
*   **License:** CC0: Public Domain (Free for educational use).
*   **Collection Method:** Web scraping using Python (Requests & BeautifulSoup).
*   **Size:** 5,283 Rows (Books) × 24 Columns (Features).

**Key Features:**
*   **Book Info:** Title, Author, Pages, Publication Year, Genres.
*   **Engagement:** Average Rating, Number of Ratings (Reach), Reviews, Votes.
*   **Author Stats:** Book Count, Follower Count.
*   **Financial:** Price (Includes missing values indicating Subscription/Bundles).

---

## 3. Research Questions
We formulated four key questions to guide our analysis:

### **Question 1: Price and Popularity**
*   **The Question:** Do books sold via **Subscription** services or **Bundles** get more attention than normal paid books? Is there a specific price range that works best?
*   **Motivation:** To determine if "Free/Subscription" models are the most effective way to gain readers, or if higher prices signal higher quality.

### **Question 2: Author Fame vs. Book Quality**
*   **The Question:** Does an **Author's Fame** (Followers) actually make a book successful? Does a huge audience lead to better ratings, or just *more* ratings?
*   **Motivation:** To separate the author's personal brand from the actual quality of the book.

### **Question 3: Changing Habits (Audiobooks & Genres)**
*   **The Question:** How does **Audiobooks** affect book length, and is it an important driver for a book's success? Which **Genres and Genre Combinations** are the most popular? Is there a benefit to combining multiple genres?
*   **Motivation:** To identify market trends and see if Audiobooks are now a "required" format for a bestseller.

### **Question 4: Predicting a Hit (Machine Learning)**
*   **The Question:** Can we build a model to predict how **Popular** (`num_ratings`) a book will be *before* it is released?
*   **Motivation:** To help publishers and authors estimate a book's potential success ("Niche" vs. "Blockbuster") using only metadata available pre-launch.

---

## 4. Key Findings Summary

### Question 1: Price and Popularity

**1. Do books available via subscription services and bundles achieve higher visibility?**
*   **Finding:** The results from the subscription services and bundle test methods are better, and more authors (about 31% of the author) are choosing the bundle option
*   **Conclusion:** Books avaiable via subscription services and bundles achieve higher visibility, especially the Bundle option

**2. Does a higher price leads to lower engagement? What is the best price**
*   **Finding:** Some users may be satisfied at higher prices, many others are not
*   **Conclusion:** The higher price lead to lower engagement. The author may consider choose the price in range 12-14$

### Question 2: Author Fame vs. Book Quality

**1. How does an author's reputation drive the reach and reception of a book?**
*   **Finding:** A strongly positive correlation between followers count and number of ratings
*   **Conclusion:** Books tend to sell more when the author is more famous

**2. Does a wider audience lead to lower average ratings because of broader scrutiny?**
*   **Finding:** No significant relationship between follower count and ratings
*   **Conclusion:** We not sure if a wider audience leads to lower average ratings due to broader scrutiny but the minimum ratings of the books have increased

### Question 3: Changing Habits (Audiobooks & Genres)

**1. The Audiobook Advantage**
*   **Impact on Length:** Books with an **Audiobook** format are, on average, **53.5 pages longer** than physical-only books, and is key driver in sustaining longer content (350+ pages).
*   **Impact on Success:** **Audiobook** format also drives success. Audiobooks achieve approximately **1.5x higher visibility** (ratings count) than non-audiobooks.
*   **Conclusion:** For authors, the Audiobook format is allow for more content in a book and is a driver of higher engagement.

**2. Genre Combination Advantage**
*   **Finding:** Combinations of genres often perform significantly better than individual genres alone. For example, while the top individual genre ("Fae") averages ~500,000 ratings, the combination **"Fae + Romantasy"** jumps to nearly **800,000 ratings**.
*   **Conclusion:** Combining certain genres can result in significantly higher popularity than sticking to a single category.

### Question 4: Predicting a Hit (Machine Learning)

**1. Model Performance**
*   **Result:** We successfully built a **Ridge Regression** model that predicts a book's commercial reach (log of ratings) with an **$R^2$ of 0.64**.
*   **Meaning:** The model can explain approximately **64%** of the variation in a book's success using *only* metadata available before release (Genre, Author info, Price, Format).

**2. Key Drivers of Success**
*   **Reputation is King:** The strongest predictor of success is **Author Follower Count** ($0.69$ correlation). Fame drives initial visibility more than any other factor.
*   **Distribution Strategy:** Books available via **Subscription** (Price 0) or **Bundles** (Price NA) have statistically higher reach than traditional retail books.
*   **Retail Sweet Spot:** For paid books, the **\$12–\$14** price range performs best, likely acting as a signal of "Premium Quality" compared to cheaper mass-market options.

---

## 5. Limitations

**Dataset Limitations**
*   **The "Good Book" Bias:** This dataset only contains books that were nominated for awards. We do not have data on books that failed or were never read.
*   **Consequence:** Our model is good at predicting the difference between a "Hit" and a "Mega-Hit," but it cannot learn what makes a book fail because it has never seen a "bad" book.

**Analysis Limitations**
*   **Too Many Genres:** There are over 450 unique genres. We could not analyze every single one or every possible combination (like triplets) because many combinations appear too rarely to be statistically significant.
*   **Simplification:** We had to focus on the Top 20 genres and Top 5 combinations. There may be hidden niche trends in the smaller genres that our analysis missed.

**Scope Limitations**
*   **No Financial Data:** Our goal was to predict commercial success, but we do not have access to actual **Sales Figures** or **Revenue**.
*   **The Proxy:** We used "Number of Ratings" as a substitute for sales. While this is a strong indicator of reach, it is not a perfect match for financial earnings.

---

## 6. Future Directions

**1. Get Real Financial Data**
*   **The Idea:** Currently, we assume that "More Ratings = More Money."
*   **The Next Step:** We would try to scrape or buy actual **Sales Figures** or **Revenue Data**. This would allow us to calculate the true financial value of a book.

**2. Analyze "Average" and "Bad" Books**
*   **The Idea:** Our dataset only has the "Good" (Award Nominees) books. We don't know what a "failure" looks like.
*   **The Next Step:** We would collect data on random, non-famous books from Amazon or Goodreads. By comparing "Winners" vs. "Non-Winners," we could train a much more powerful model that can predict if a book will flop or succeed.

**3. Deep Dive into Genre Relationships**
*   **The Idea:** We only looked at the Top 20 genres and simple pairs.
*   **The Next Step:** We would perform a **Network Analysis** on all 456 genres. This would help us visualize the complex web of sub-genres to find hidden, high-growth niches that are currently too small to see in a simple bar chart.

**4. Analyze Text (NLP)**
*   **The Idea:** We dropped the `title` column because they were text.
*   **The Next Step:** We would use **Natural Language Processing (NLP)**. Maybe the *words* in a title have an impact on readers that drives sales, regardless of the genre.

---

## 7. Individual Reflections

### **7.1 Student 1**

**Challenges & Difficulties:**
*   **Analyzing Data from Visualization:** Every chart or graph conveys specific information, choose which one to fit the current problem and analysis the trending, establishing relationships and extracting meaningful insights

**Learning & Growth:**
* **Result:** I can now effectively address several critical aspects: recognizing anomalies in the data can enhance the accuracy or evaluating different sets of data allows determine which group performs best based on the criteria established.

### **7.2 Student 2**

**Challenges & Difficulties:**
*   **Statistical Validation:** The biggest challenge was realizing I couldn't just look at a graph and say "this looks different." I had to learn specific statistical tests (like **Kruskal-Wallis** and **Mann-Whitney U**) to mathematically prove my observations were real.
*   **Handling Text Data:** The `genres` column was difficult because it had over 400 unique string values. I had to learn how to set a "threshold" to pick only the top genres so we could give the model enough information without confusing it with too many variables.
*   **Model Interpretation:** It was hard to understand what a "good" model actually looks like. I learned that a high accuracy score isn't enough; you need to look at the Feature Weights to make sure the model is learning the right things.

**Learning & Growth:**
*   **The Analytical Process:** I learned that Data Science is a strict process. You can't just jump to the answer. You have to define *why* you are asking the question, hypothesize the result, visualize it, statistically validate it, and *then* conclude.
*   **Surprise:** I was surprised by how much effort is needed just to answer one business question completely.
*   **Impact:** This project taught me that Data Science is much more complex than just fitting a model, it requires deep critical thinking at every step.

---

## 8. Project Structure

*   **`Data/`**: Contains all datasets used in the project.
    *   **`Raw/`**: Stores the original, unprocessed dataset (`final_books_data_2011_2024.csv`) and the parsed raw dataset (`parsed_books_data.tsv`).
    *   **`Processed/`**: Holds the cleaned, transformed, and split data files (`X_train.csv`, `y_train.csv`, etc.) generated after preprocessing, ready for modeling.

*   **`notebooks/`**: Contains the executable Jupyter Notebooks, organized chronologically and by task.
    *   **`00_parse_data.ipynb`**: Handles initial data loading, parsing, and cleaning of the raw CSV, preparing it for analysis.
    *   **`01_data_exploration.ipynb`**: Performs Exploratory Data Analysis (EDA) by answering key questions about the dataset's structure, quality, and initial patterns, including visualizations.

*   **`questions/`**: Contains Jupyter Notebooks dedicated to answering specific research questions, building upon the preprocessing and analysis steps.
    *   **`question1.ipynb`**: Models book popularity (e.g., `num_ratings`) using the processed data.
    *   **`question2.ipynb`**: Analyzes the impact of author reputation on book reach and quality.
    *   **`question3.ipynb`**: Investigates trends in book length, audiobook adoption, and genre popularity over time.
    *   **`question4_preprocessing.ipynb`**: Cleans, engineers features, handles missing values, splits the data into training, validation, and testing sets, and scales features.
    *   **`question4_modelling.ipynb`**: Implements and evaluates machine learning models (Linear Regression, Ridge, Lasso) using the preprocessed data, including hyperparameter tuning and final testing.

*   **`requirements.txt`**: Lists all necessary Python libraries for running the project.
*   **`README.md`**: This document, providing an overview, setup instructions, methodology, results, and reflection.

---
## 9. How to Run Instructions

### Step 1: Environment Setup
1.  **Clone or Download** this repository to your computer.
2.  **Create a Virtual Environment (Python 3.12)**:
    ```bash
    # Windows
    python -m venv venv
    
    # Mac/Linux
    python3.12 -m venv venv
    ```
3.  **Activate the Environment**:
    ```bash
    # Windows
    venv\Scripts\activate
    
    # Mac/Linux
    source venv/bin/activate
    ```
4.  **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

### Step 2: Data Parsing
You must run the parser first to convert the raw CSV into the clean TSV format used by all other notebooks.
*   Run **`Notebooks/00_parse_data.ipynb`**.

### Step 3: Exploratory Analysis
*   Run **`Notebooks/01_data_exploration.ipynb`** to see the general data analysis and visualization.

### Step 4: Research Questions
You can run the notebooks in the `Questions/` folder in any order, **EXCEPT for Question 4**.

*   **Question 1, 2, 3:** Run `Question1.ipynb`, `Question2.ipynb`, and `Question3.ipynb`.
*   **Question 4 (Machine Learning):** You **must** run them in this specific order:
    1.  First: `Questions/question4_preprocessing.ipynb` (to generate training files).
    2.  Second: `Questions/question4_modelling.ipynb` (to train and evaluate the model).

---

## 10. Dependencies List

The project requires the following Python libraries:

*   pandas
*   numpy
*   matplotlib
*   seaborn
*   scikit-learn
*   scipy
