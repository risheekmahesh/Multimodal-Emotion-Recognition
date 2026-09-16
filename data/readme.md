# RAVDESS Dataset

This project uses the **RAVDESS (Ryerson Audio-Visual Database of Emotional Speech and Song)** dataset for multimodal emotion recognition.

The dataset contains emotional speech recordings from **24 actors**, with each recording representing one of eight emotion categories.

## Dataset Structure

The dataset is organized into 24 actor folders:

- `Actor_01`
- `Actor_02`
- `Actor_03`
- `Actor_04`
- `Actor_05`
- `Actor_06`
- `Actor_07`
- `Actor_08`
- `Actor_09`
- `Actor_10`
- `Actor_11`
- `Actor_12`
- `Actor_13`
- `Actor_14`
- `Actor_15`
- `Actor_16`
- `Actor_17`
- `Actor_18`
- `Actor_19`
- `Actor_20`
- `Actor_21`
- `Actor_22`
- `Actor_23`
- `Actor_24`

Each actor folder contains `.wav` audio recordings.

## Emotion Classes

The RAVDESS dataset contains the following eight emotion classes:

| Code | Emotion |
|------|---------|
| 01 | Neutral |
| 02 | Calm |
| 03 | Happy |
| 04 | Sad |
| 05 | Angry |
| 06 | Fearful |
| 07 | Disgust |
| 08 | Surprised |

## Use in This Project

The RAVDESS audio recordings are used as the primary input for the multimodal emotion recognition system.

The audio data is processed through the following pipeline:

**Audio → Preprocessing → Mel Spectrogram → CNN → Audio Emotion Prediction**

The same audio recordings are also passed through **Whisper** to generate transcripts:

**Audio → Whisper → Transcript → Text Processing → LSTM → Text Emotion Prediction**

The predictions from the audio and text models are then combined using **late fusion** to produce the final emotion prediction.

## Dataset Location

The original RAVDESS audio dataset is **not included in this GitHub repository** because of its large size.

For running the project locally, the dataset should be placed in:

```text
data/
└── RAVDESS/
    ├── Actor_01/
    ├── Actor_02/
    ├── Actor_03/
    ├── Actor_04/
    ├── Actor_05/
    ├── Actor_06/
    ├── Actor_07/
    ├── Actor_08/
    ├── Actor_09/
    ├── Actor_10/
    ├── Actor_11/
    ├── Actor_12/
    ├── Actor_13/
    ├── Actor_14/
    ├── Actor_15/
    ├── Actor_16/
    ├── Actor_17/
    ├── Actor_18/
    ├── Actor_19/
    ├── Actor_20/
    ├── Actor_21/
    ├── Actor_22/
    ├── Actor_23/
    └── Actor_24/
