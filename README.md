# Emotion Recognition ER

Emotion recognition is the process of identifying human emotions using AI. This project seeks to recognise emotions from speech clips (audio + video). Generally, the technology works best at this task if it uses **multiple modalities**, for this reason we implemented a two-stream model to analyze facial expressions from video and voice tone from audio. These tasks are called **Speech Emotion Recognition (SER)** and **Facial Emotion Recognition (FER)** respectively.

In this project we trained the models on speech clips of [RAVDESS](https://zenodo.org/record/1188976#.Y-9hqHbMK38) dataset which contains 8 emotion classes: neutral, calm, happy, sad, angry, fearful, surprise and disgust (7 used).

**More details** about the processing and architecture in `Project_Slides.pdf`. Dimostrative video and deployed model in the `DEMO` folder.

![Screenshot 2023-03-02 170340](https://user-images.githubusercontent.com/94122042/222483497-e4c6038c-60dd-42a0-853c-22e873bb231c.png)

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
├───StreamAudio_1D.ipynb
├───StreamAudio_2D.ipynb
├───FullClip_Test.ipynb
├───StreamVideo_FaceOnly.ipynb
├───StreamVideo_FramesExtraction.ipynb
├───StreamVideo_FullFrame.ipynb
├───StreamVideo_Test.ipynb
├───Project_Slides.pdf
├───README.md
├───LICENSE.md
└───requirements.txt
```

## Execution schema
**To classify emotions** (using our trained model):
1. Copy your clips in `DEMO/Examples`
2. Run `ER_FullClip_DEMO.ipynb` in DEMO folder

**To replicate this project** (training and inference):
1. Download the speech clips of [RAVDESS](https://zenodo.org/record/1188976#.Y-9hqHbMK38) dataset and save it in `Datasets/RAVDESS` folder
2. Train video and audio models
    1. Video Stream: extract frames with `StreamVideo_FramesExtraction.ipynb` (multiple type of frames are generated -> best are "224x224 only faces BW"), train model with `StreamVideo_FullFrame.ipynb` and `StreamVideo_FaceOnly.ipynb` (depending on the frames generated) and test the results with `StreamVideo_Test.ipynb`
    2. Audio Stream: use `StreamAudio_1D.ipynb` and `StreamAudio_2D.ipynb` to train models (2D works better)
3. Use `FullClip_Test.ipynb` to assess global performance
4. Use `ER_FullClip_DEMO.ipynb` in DEMO folder to classify videos with the trained models.

## DEMO
https://user-images.githubusercontent.com/94122042/219646582-0849650c-1d62-458f-8bef-5fd1273108b1.mp4

