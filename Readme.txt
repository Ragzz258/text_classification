The task was to build a text classification model using the Hugging Face library to classify a dataset of text into one of multiple categories.
BBC news dataset was used which contained news articles and texts labeled as their respective category i.e (business, entertainment, politics, sport and tech)

The dataset was initially in the form of folders named as the category and they contained txt files of texts hence it was coverted to csv format dataset which had columns (text and label)
All text were cleaned and now dataset was partially ready for the model.

I selected pretrained model 'BERT'(base-uncased) for this task

texts were tokenised using 'AutoTokenizer' and labels were encoded according to model
this data was split into training and validation data then using 'pyarrow' converted them to required format, now completely ready for the model.

From transformers library imported 'AutoModelForSequenceClassification' to get our model
and set prameters for 'Trainer' to custom train the above model

defined a predict function as we can't directly use model.predict()
Evaluated the model using sklearn.metrics to get F1 score, precission , recall, accuray
which inturn are all same i.e 0.9865 as it is a classification model and micro averaging was used to calculate these metrics.

here are few sample predictions:

	1. text: 'In 1904 the International Association of Football (FIFA) was formed.'
	   prediction : {'class': 'sport', 'probability': 0.99110377}
	
	2. text: 'stock market had a big loss due to russia ukraine war'
	   prediction : {'class': 'business', 'probability': 0.9997402

	3. text: 'Indian governmemt holds an election to appoint prime minister'
	   prediction : {'class': 'politics', 'probability': 0.9384233}

	4. text: 'creed 3 was an excellent movie'
	   prediction : {'class': 'entertainment', 'probability': 0.9995809}

	5. text: 'chatgpt is a new ai tool everyone is going crazy about it'
	   prediction : {'class': 'tech', 'probability': 0.9993667}



