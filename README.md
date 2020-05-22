# Speech Emotion Analyzer

Deep learning project to identify emotions from audio clips. The models folder contains the trained model and the jupyter notebook. Django framework is used to create a web interface to interact with the model.

Dataset: The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS) dataset: https://zenodo.org/record/1188976

# How does this work?

For this task, 4948 samples are used from the RAVDESS dataset (see below to know more about the data).

The samples come from:

- Audio-only files;

- Video + audio files: Audio from each file is extracted using the script **Mp4ToWav.py** that you can find in the models directory.

The classes its trying to predict are the following: (0 = neutral, 1 = calm, 2 = happy, 3 = sad, 4 = angry, 5 = fearful, 6 = disgust, 7 = surprised)

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

# About the RAVDESS dataset

**Download**

The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS) can be downloaded free of charge at https://zenodo.org/record/1188976.

**Construction and Validation**

Construction and validation of the RAVDESS is described in our paper: Livingstone SR, Russo FA (2018) The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS): A dynamic, multimodal set of facial and vocal expressions in North American English. PLoS ONE 13(5): e0196391. https://doi.org/10.1371/journal.pone.0196391.

The RAVDESS contains 7356 files. Each file was rated 10 times on emotional validity, intensity, and genuineness. Ratings were provided by 247 individuals who were characteristic of untrained adult research participants from North America. A further set of 72 participants provided test-retest data. High levels of emotional validity, interrater reliability, and test-retest intrarater reliability were reported. Validation data is open-access, and can be downloaded along with our paper from PLOS ONE.

**Description**

The dataset contains the complete set of 7356 RAVDESS files (total size: 24.8 GB). Each of the 24 actors consists of three modality formats: Audio-only (16bit, 48kHz .wav), Audio-Video (720p H.264, AAC 48kHz, .mp4), and Video-only (no sound).  Note, there are no song files for Actor_18.

**License information**

“The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)” by Livingstone & Russo is licensed under CC BY-NA-SC 4.0.

**File naming convention**

Each of the 7356 RAVDESS files has a unique filename. The filename consists of a 7-part numerical identifier (e.g., 02-01-06-01-02-01-12.mp4). These identifiers define the stimulus characteristics:

Filename identifiers

- Modality (01 = full-AV, 02 = video-only, 03 = audio-only).
- Vocal channel (01 = speech, 02 = song).
- Emotion (01 = neutral, 02 = calm, 03 = happy, 04 = sad, 05 = angry, 06 = fearful, 07 = disgust, 08 = surprised).
- Emotional intensity (01 = normal, 02 = strong). NOTE: There is no strong intensity for the ‘neutral’ emotion.
- Statement (01 = “Kids are talking by the door”, 02 = “Dogs are sitting by the door”).
- Repetition (01 = 1st repetition, 02 = 2nd repetition).
- Actor (01 to 24. Odd numbered actors are male, even numbered actors are female).

**Filename example: 02-01-06-01-02-01-12.mp4**

- Video-only (02)
- Speech (01)
- Fearful (06)
- Normal intensity (01)
- Statement “dogs” (02)
- 1st Repetition (01)
- 12th Actor (12)
- Female, as the actor ID number is even.

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/Rajanpandey/"><img src="https://avatars.githubusercontent.com/u/1500684?v=3" width="100px;" alt=""/><br /><sub><b>Kent C. Dodds</b></sub></a><br /><a href="#question-kentcdodds" title="Answering Questions">💬</a> <a href="https://github.com/all-contributors/all-contributors/commits?author=kentcdodds" title="Documentation">📖</a> <a href="https://github.com/all-contributors/all-contributors/pulls?q=is%3Apr+reviewed-by%3Akentcdodds" title="Reviewed Pull Requests">👀</a> <a href="#talk-kentcdodds" title="Talks">📢</a></td>
    <td align="center"><a href="https://github.com/jfmengels"><img src="https://avatars.githubusercontent.com/u/3869412?v=3" width="100px;" alt=""/><br /><sub><b>Jeroen Engels</b></sub></a><br /><a href="https://github.com/all-contributors/all-contributors/commits?author=jfmengels" title="Documentation">📖</a> <a href="https://github.com/all-contributors/all-contributors/pulls?q=is%3Apr+reviewed-by%3Ajfmengels" title="Reviewed Pull Requests">👀</a> <a href="#tool-jfmengels" title="Tools">🔧</a></td>
    <td align="center"><a href="https://jakebolam.com"><img src="https://avatars2.githubusercontent.com/u/3534236?v=4" width="100px;" alt=""/><br /><sub><b>Jake Bolam</b></sub></a><br /><a href="https://github.com/all-contributors/all-contributors/commits?author=jakebolam" title="Documentation">📖</a> <a href="#tool-jakebolam" title="Tools">🔧</a> <a href="#infra-jakebolam" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a> <a href="#maintenance-jakebolam" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/tbenning"><img src="https://avatars2.githubusercontent.com/u/7265547?v=4" width="100px;" alt=""/><br /><sub><b>tbenning</b></sub></a><br /><a href="#design-tbenning" title="Design">🎨</a> <a href="#maintenance-tbenning" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://sinchang.me"><img src="https://avatars0.githubusercontent.com/u/3297859?v=4" width="100px;" alt=""/><br /><sub><b>Jeff Wen</b></sub></a><br /><a href="#maintenance-sinchang" title="Maintenance">🚧</a></td>
    <td align="center"><a href="http://maxcubing.wordpress.com"><img src="https://avatars0.githubusercontent.com/u/8260834?v=4" width="100px;" alt=""/><br /><sub><b>Maximilian Berkmann</b></sub></a><br /><a href="#translation-Berkmann18" title="Translation">🌍</a> <a href="https://github.com/all-contributors/all-contributors/commits?author=Berkmann18" title="Documentation">📖</a> <a href="#maintenance-Berkmann18" title="Maintenance">🚧</a></td>
    <td align="center"><a href="http://matheu.srv.br"><img src="https://avatars0.githubusercontent.com/u/23284276?v=4" width="100px;" alt=""/><br /><sub><b>Matheus Rocha Vieira</b></sub></a><br /><a href="#translation-MatheusRV" title="Translation">🌍</a> <a href="https://github.com/all-contributors/all-contributors/commits?author=MatheusRV" title="Code">💻</a> <a href="https://github.com/all-contributors/all-contributors/commits?author=MatheusRV" title="Documentation">📖</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->
