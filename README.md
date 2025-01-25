# Active_Learning_in_NLP_using_Small_Text_Technique

# What is Small-Text? 🎯

Small-Text is a Python library that enables active learning—a method where a model intelligently selects the most informative samples to label from a pool of unlabeled data. This approach is particularly useful when:

• You have limited labeled data.

• Labeling new data is expensive or time-consuming.

By reducing the amount of labeled data required, Small-Text makes machine learning projects more efficient! 🚀


# Library Setup 🛠️

• Essential libraries like small-text, datasets, sklearn, and visualization tools (seaborn, matplotlib) are imported.

• Warnings and logs are suppressed to keep the output clean and focused.

 
# Data Loading 📚

• The IMDB dataset (movie reviews) is loaded using the 🤗 datasets library.

   • Train Set: Used for active learning.
   
   • Test Set: Used for evaluating performance.
   
• The text column (reviews) and label column (sentiment: 0 for negative, 1 for positive) are extracted.



# Text Representation ✍️

• A TF-IDF Vectorizer converts text data into numerical features for the machine learning model.

• Features: Limited to the top 5000 most important words/phrases.

• N-grams: Includes single words, pairs of words (bigrams), and triples (trigrams) to capture context.

# Dataset Preparation 🔢

• The SklearnDataset class from small-text is used to prepare datasets for training and testing.

• The vectorizer transforms raw text into feature vectors, while target_labels defines the number of classes.




# Model Initialization 🧠

• Logistic Regression is selected as the machine learning model due to its simplicity and efficiency for binary classification tasks.

• The model is wrapped using the SklearnClassifierFactory, making it compatible with the small-text library.

# Query Strategy 📈

• The PredictionEntropy query strategy is chosen.

• This strategy selects the most uncertain samples for labeling, where the model struggles to make confident predictions.

• It ensures that labeling efforts focus on the most informative data points.


# Active Learner Initialization 🏁

• The Pool-Based Active Learner is initialized with:

  • The Logistic Regression model.
  • The PredictionEntropy strategy.
  • A balanced random initialization of 200 samples, ensuring diverse labeled data to start training.


# Evaluation Function 🧪

• A function is defined to compute the weighted F1-score, a metric that balances precision and recall across classes.

• The model's performance is evaluated on both:

  • Training set: To measure how well the model learns.
  
  • Test set: To measure generalization to unseen data.



# Active Learning Loop 🔄 
• 50 Iterations are performed to iteratively improve the model:
  1.Querying: The model selects 20 samples for labeling in each iteration.
  2.Updating: The newly labeled samples are added to the training data, and the model is retrained.
  3.Evaluating: The performance is assessed, and F1-scores are recorded.


# Visualization 📊

• A line plot and scatter plot visualize how the F1-score evolves over iterations.
• The chart shows:
  • X-axis: Query iteration number.
  • Y-axis: Classification F1-score.
• Seaborn styling ensures a clean and professional appearance.



#  Why Active Learning Matters! ✨
## Smart Labeling 💡 
Focus only on important samples for labeling, saving time and resources.

## Incremental Improvement 📈
Observe consistent performance gains as the model learns with fewer labeled samples.

## NLP Applications 💻

This method is perfect for tasks like sentiment analysis, text classification, and more!

With Small-Text, you can build smarter, faster, and more efficient NLP models. 🚀✨
