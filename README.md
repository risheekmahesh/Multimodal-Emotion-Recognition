# multimodal-emotion-recognition
Multimodal Emotion Recognition using Audio CNN, Whisper Transcripts, and Text RNN with Late Fusion techniques.
# Multimodal Emotion Recognition

A deep learning-based **Multimodal Emotion Recognition** system that combines **audio and textual information** from speech to classify human emotions.

The project uses **CNNs for audio features**, **OpenAI Whisper for speech-to-text transcription**, and an **LSTM-based text model**, followed by **late fusion** to combine the predictions from both modalities.

---

##  Project Overview

This project focuses on recognizing emotions from speech by utilizing two complementary modalities:

* 🎵 **Audio:** Mel Spectrograms extracted from speech recordings and classified using a CNN.
* 📝 **Text:** Speech transcripts generated using Whisper and processed using an LSTM network.
* 🔗 **Multimodal Fusion:** Predictions from the audio and text models are combined using a late-fusion approach.

The system is trained and evaluated using the **RAVDESS Emotional Speech Audio Dataset**.

---

##  Objectives

The main objectives of this project are:

* Perform emotion classification from audio spectrograms using CNN.
* Generate speech transcripts using OpenAI Whisper.
* Process textual data using tokenization and sequence padding.
* Build an LSTM-based text emotion classifier.
* Combine audio and text predictions using multimodal late fusion.
* Compare the performance of:

  * Audio-only model
  * Text-only model
  * Multimodal model

---

##  Dataset

### RAVDESS Emotional Speech Audio

The **Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)** is used for training and evaluating the models.

The dataset contains emotional speech recordings from multiple actors representing different emotional states.

### Emotion Classes

| Label | Emotion   |
| ----: | --------- |
|    01 | Neutral   |
|    02 | Calm      |
|    03 | Happy     |
|    04 | Sad       |
|    05 | Angry     |
|    06 | Fearful   |
|    07 | Disgust   |
|    08 | Surprised |

---

##  System Architecture

The overall pipeline consists of three major stages:

```text
                    RAVDESS Audio
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
        Audio Processing       Whisper ASR
              │                     │
              ▼                     ▼
       Mel Spectrogram          Transcript
              │                     │
              ▼                     ▼
          Audio CNN             Text LSTM
              │                     │
              ▼                     ▼
       Audio Prediction       Text Prediction
              │                     │
              └──────────┬──────────┘
                         │
                         ▼
                  Late Fusion
                         │
                         ▼
                Final Emotion
                   Prediction
```

---

##  Audio Processing

The audio modality is processed using **Librosa**.

The pipeline includes:

1. Loading the audio files.
2. Resampling the audio.
3. Extracting Mel Spectrograms.
4. Converting the spectrograms into suitable input tensors.
5. Feeding the spectrograms into a CNN.
6. Predicting the emotion from the audio representation.

### Audio Model

A **Convolutional Neural Network (CNN)** is used to learn spatial patterns from Mel Spectrograms.

The CNN learns characteristics such as:

* Frequency patterns
* Temporal patterns
* Spectral characteristics
* Energy distribution

---

##  Speech Transcription

The speech recordings are converted into text using **OpenAI Whisper**.

```text
Audio → Whisper → Transcript
```

The generated transcripts are then used as input to the text-based emotion recognition model.

---

##  Text Processing

The transcripts are processed before being passed to the LSTM model.

The preprocessing pipeline includes:

* Tokenization
* Vocabulary creation
* Conversion of words into integer sequences
* Sequence padding
* Preparation of input tensors

Example:

```text
Speech
   ↓
Whisper
   ↓
Text Transcript
   ↓
Tokenization
   ↓
Integer Sequence
   ↓
Padding
   ↓
LSTM
```

---

##  Text Model

An **LSTM (Long Short-Term Memory)** network is used to process the textual information.

The LSTM is useful for capturing sequential relationships between words in the transcript.

The text model produces an emotion prediction based on the linguistic information present in the speech.

---

## Multimodal Late Fusion

The audio and text models independently produce emotion predictions.

These predictions are then combined using **late fusion**.

```text
Audio CNN ──────► Audio Prediction ──┐
                                    │
                                    ▼
                              Late Fusion
                                    │
                                    ▼
                            Final Prediction
                                    ▲
                                    │
Text LSTM ───────► Text Prediction ─┘
```

This allows the system to utilize information from both:

* **How something is said** → Audio
* **What is being said** → Text

---

## Model Comparison

The project evaluates three different approaches:

| Model      | Input              | Purpose                               |
| ---------- | ------------------ | ------------------------------------- |
| Audio-only | Mel Spectrogram    | Evaluate acoustic emotion information |
| Text-only  | Whisper Transcript | Evaluate linguistic information       |
| Multimodal | Audio + Text       | Combine both modalities               |

Performance can be compared using metrics such as:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## Dataset Challenges

Some challenges associated with the dataset and task include:

* Relatively small dataset size.
* Similar acoustic characteristics between certain emotions.
* Emotion overlap between classes.
* Short and repetitive speech transcripts.
* Transcription errors for emotionally expressive speech.
* Potential class imbalance depending on the selected subset and preprocessing pipeline.

---

##  Technologies Used

* **Python**
* **TensorFlow / Keras**
* **Librosa**
* **OpenAI Whisper**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Seaborn**

---

##  Project Structure

```text
multimodal-emotion-recognition/
│
├── data/
│   └── RAVDESS/
│
├── notebooks/
│   └── multimodal_emotion_recognition.ipynb
│
├── models/
│   ├── audio_model/
│   └── text_model/
│
├── outputs/
│   ├── plots/
│   └── results/
│
├── README.md
└── requirements.txt
```

---

##  Workflow

```text
1. Load RAVDESS Dataset
          ↓
2. Preprocess Audio
          ↓
3. Generate Mel Spectrograms
          ↓
4. Train Audio CNN
          ↓
5. Generate Whisper Transcripts
          ↓
6. Tokenize and Pad Text
          ↓
7. Train Text LSTM
          ↓
8. Generate Audio + Text Predictions
          ↓
9. Perform Late Fusion
          ↓
10. Evaluate Multimodal Model
```

---

##  Future Improvements

Possible improvements include:

* Using pretrained audio encoders.
* Using transformer-based text classifiers instead of LSTM.
* Fine-tuning Whisper for emotional speech.
* Experimenting with early, intermediate, and late fusion.
* Data augmentation for audio.
* Using pretrained language models such as BERT.
* Increasing the size and diversity of the training dataset.
* Performing speaker-independent evaluation.

---
This project is intended for educational and research purposes.
