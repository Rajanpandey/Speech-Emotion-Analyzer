# Speech Emotion Analyzer

Deep learning project to identify emotions from audio clips. The models folder contains the trained model and the jupyter notebook. Django framework is used to create a web interface to interact with the model.

# Dataset

The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS) dataset: https://zenodo.org/record/1188976

Toronto emotional speech set (TESS) dataset: https://tspace.library.utoronto.ca/handle/1807/24487

# How does this work?

For this task, 5332 samples are used from the RAVDESS dataset and TESS dataset combined.
The samples include:

- 1440 speech files and 1012 Song files from **RAVDESS**. This dataset includes recordings of 24 professional actors (12 female, 12 male), vocalizing two lexically-matched statements in a neutral North American accent. Speech includes calm, happy, sad, angry, fearful, surprise, and disgust expressions, and song contains calm, happy, sad, angry, and fearful emotions. Each file was rated 10 times on emotional validity, intensity, and genuineness. Ratings were provided by 247 individuals who were characteristic of untrained adult research participants from North America. A further set of 72 participants provided test-retest data. High levels of emotional validity, interrater reliability, and test-retest intrarater reliability were reported. Validation data is open-access, and can be downloaded along with our paper from [PLoS ONE](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0196391).

- 2800 files from **TESS**. A set of 200 target words were spoken in the carrier phrase "Say the word _____' by two actresses (aged 26 and 64 years) and recordings were made of the set portraying each of seven emotions (anger, disgust, fear, happiness, pleasant surprise, sadness, and neutral). There are 2800 stimuli in total. Two actresses were recruited from the Toronto area. Both actresses speak English as their first language, are university educated, and have musical training. Audiometric testing indicated that both actresses have thresholds within the normal range.

The classes we are trying to predict are the following: (0 = neutral, 1 = calm, 2 = happy, 3 = sad, 4 = angry, 5 = fearful, 6 = disgust, 7 = surprised). This dataset is skewed as for the we do not have a calm class in TESS, hence there are less data for that particular class. This is evident when taking a look at the classification report.

# Actual metrics after the application of a Neural Network to this dataset

**Model summary**

![Link to loss](https://github.com/rajanpandey/Speech-Emotion-Analyzer/blob/master/gitmedia/modelSummary.png)

**Loss and accuracy plots**

![Link to loss](https://github.com/rajanpandey/Speech-Emotion-Analyzer/blob/master/gitmedia/loss.png)

![Link to accuracy](https://github.com/rajanpandey/Speech-Emotion-Analyzer/blob/master/gitmedia/accuracy.png)

**Classification report**

![Link do classification report](https://github.com/rajanpandey/Speech-Emotion-Analyzer/blob/master/gitmedia/classificationReportUpdated.png)

**Confusion matrix**

![Link do classification report](https://github.com/rajanpandey/Speech-Emotion-Analyzer/blob/master/gitmedia/confusionMatrix.png)

# How to run the project

1. Clone the repo: `https://github.com/Rajanpandey/Speech-Emotion-Analyzer.git`
2. `cd Speech-Emotion-Analyzer`
2. Install Python 3.7 x64 version
3. Upgrade pip to its latest version
4. Run `pip install -r requirements.txt`
5. Download and install PostgreSQL
6. In terminal, run the following commands:
```
psql -U <your_name>
CREATE DATABASE speechemotionanalyzer;

CREATE USER <your_name> WITH PASSWORD '<your_pwd>';

CREATE TABLE App_filemodel (
   id INT PRIMARY KEY NOT NULL,
   file TEXT NOT NULL,
   timestamp DATE NOT NULL,
   path TEXT NOT NULL
);

\c speechemotionanalyzer;

CREATE SCHEMA speechemotionanalyzer;

GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA speechemotionanalyzer TO <your_name>;

ALTER USER <your_name> CREATEDB;
```
7. In Settings.py, find DATABASES dictionary on line 149 and change USER and PASSWORD according to your Postgres application.
9. Run `python ./manage.py migrate `
10. Run `python manage.py runserver`
11. Visit http://127.0.0.1:8000/index/

**How to run the tests**

```python manage.py test```
