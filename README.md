# Emotion Recognition ER

Emotion recognition is the process of identifying human emotions using AI. This project seeks to recognise emotions from speech clips (audio + video). Generally, the technology works best at this task if it uses **multiple modalities**, for this reason we implemented a two-stream model to analyze facial expressions from video and voice tone from audio. These tasks are called **Speech Emotion Recognition (SER)** and **Facial Emotion Recognition (FER)** respectively.

In this project we trained the models on speech clips of [RAVDESS](https://zenodo.org/record/1188976#.Y-9hqHbMK38) dataset which contains 8 emotion classes: neutral, calm, happy, sad, angry, fearful, surprise and disgust (7 used).

**More details** about the processing and architecture in `Slides_Emotion-Recognition.pdf`. Dimostrative video and deployed model in the `DEMO` folder.

## Repo structure
```
Emotion-Recognition_SER-FER_RAVDESS
├───Datasets
│   ├───RAVDESS
│   ├───RAVDESS_audio
│   ├───RAVDESS_frames
│   ├───RAVDESS_frames_black
│   └───RAVDESS_frames_face_BW
├───DEMO
│   ├───Examples
│   ├───ER DEMO.mp4
│   └───ER_FullClip_DEMO.ipynb
├───Models
│   ├───Audio Stream
│   └───Video Stream
├───Other
│   └───haarcascade_frontalface_default.xml
├───Plots
├───ER_AudioStream_1D.ipynb
├───ER_AudioStream_2D.ipynb
├───ER_FullClip_Test.ipynb
├───ER_VideoStream_FaceOnly.ipynb
├───ER_VideoStream_FramesExtraction.ipynb
├───ER_VideoStream_FullFrame.ipynb
├───ER_VideoStream_Test.ipynb
├───Slides_Emotion-Recognition.pdf
├───README.md
└───requirements.txt
```

## Execution schema
**To classify emotions** (using our trained model):
1. Copy your clips in `DEMO/Examples`
2. Run `ER_FullClip_DEMO.ipynb` in DEMO folder

**To replicate this project** (training and inference):
1. Download the speech clips of [RAVDESS](https://zenodo.org/record/1188976#.Y-9hqHbMK38) dataset and save it in `Datasets/RAVDESS` folder
2. Train video and audio models
    1. Video Stream: extract frames with `ER_VideoStream_FramesExtraction.ipynb` (multiple type of frames are generated -> best are "224x224 only faces BW"), train model with `ER_VideoStream_FullFrame.ipynb` and `ER_VideoStream_FaceOnly.ipynb` (depending on the frames generated) and test the results with `ER_VideoStream_Test.ipynb`
    2. Audio Stream: use `ER_AudioStream_1D.ipynb` and `ER_AudioStream_2D.ipynb` to train models (2D works better)
3. Use `ER_FullClip_Test.ipynb` to assess global performance
4. Use `ER_FullClip_DEMO.ipynb` in DEMO folder to classify videos with the trained models.