Sentiment Analysis of Tokopedia App Reviews 🇬🇧📱
This project performs web scraping of Tokopedia app reviews from the Google Play Store and builds sentiment analysis models using various machine learning and deep learning approaches.

📁 Project Structure

scraping.ipynbNotebook for scraping review data from the Google Play Store using google-play-scraper.

sentiment_model.ipynbNotebook containing:  

Data exploration  
Automatic sentiment labeling based on ratings  
Text preprocessing  
Implementation and evaluation of three model schemes:  
TF-IDF + SVM  
Word2Vec + Random Forest  
LSTM (Deep Learning)






🛠️ Technologies & Libraries

Python  
pandas, numpy, re, string  
nltk (stopwords)  
scikit-learn  
gensim (Word2Vec)  
tensorflow / Keras (LSTM)  
google-play-scraper


🔍 Steps
1. Scraping Tokopedia Reviews
Using google_play_scraper to fetch up to 10,000 user reviews for the Tokopedia app from the Google Play Store (Indonesia localization).
from google_play_scraper import reviews
# Output is saved in data_tokopedia_reviews.csv

2. Preprocessing & Labeling

Remove unnecessary characters, numbers, punctuation, and stopwords.  
Sentiment labels are assigned based on ratings:  
⭐ 1–2 → Negative  
⭐ 3 → Neutral  
⭐ 4–5 → Positive



3. Model Schemes
✅ Scheme 1: TF-IDF + SVM

TF-IDF vectorization  
Linear Support Vector Classifier (SVM)  
Evaluation: Accuracy & classification report (scikit-learn)

🌳 Scheme 2: Word2Vec + Random Forest

Word embedding using Word2Vec (gensim)  
Each review is represented as the average of word vectors  
Classification model: Random Forest

🧠 Scheme 3: LSTM (Deep Learning)

Tokenization and sequence padding  
Architecture: LSTM + Bidirectional + Dropout  
Final activation: Softmax for three classes


📈 Example Results
TF-IDF + SVM Accuracy: 0.989
Word2Vec + RF Accuracy: 0.989
LSTM Accuracy: 0.9905

Results may vary depending on the dataset and random state.

🧪 Example Inference
# TF-IDF + SVM
"This product is very disappointing and does not match the description" → Prediction: NEGATIVE

# Word2Vec + RF
"Fast and friendly service" → Prediction: POSITIVE

# LSTM
"This product is really cool" → Prediction: POSITIVE


📌 Notes

The dataset is dynamic and depends on the latest reviews.  
LSTM is suitable for large-scale data but requires longer training time.  
Word2Vec is effective for generating reusable embeddings for other projects.


📂 Output

data_tokopedia_reviews.csv: Dataset from scraping  
Inference models are available at the end of each scheme notebook


📄 License
This project is created for educational and research purposes.Data is publicly sourced from the Google Play Store. Use responsibly.
