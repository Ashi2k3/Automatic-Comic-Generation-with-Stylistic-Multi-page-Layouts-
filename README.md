# Automatic-Comic-Generation-with-Stylistic-Multi-page-Layouts
A real-time video-to-comic conversion project using CycleGAN, Flask, and Docker. Converts RGB video into comic-style frames from a YouTube link
Methodology
Our project consists of the following core modules:

Subtitle Generation
Create a subtitle file for the input video using Whisper model
Keyframe Extraction
Frame Sampling: Samples frames at a set frequency from videos.
Feature Extraction: Utilizes deep learning models like GoogLeNet v1 to extract features from frames.
Highlightness Score Calculation: Deep Summarization Network (DSN) computes scores to identify keyframes.
Dialogue Grouping: Groups frames based on dialogues to select significant keyframes.
Panel Layout Generation
Calculates the Region of Interest of a frame
Selects a page layout template
Crops frame to be accomodated into template
Balloon Generation & Placement
Analysis of emotions in subtitles determines speech balloon shape.
Balloon placement involves using the "Dlib" face-detector library to detect characters' mouth positions in frames and placing at regions with relatively lesser ROI.
Cartoonization
Applies style transfer algorithms to enhance keyframes visually, mimicking traditional comics.
Read the project report for detailed explanations

Pre-requisites
Python
Install Pytorch
Install dlib
Install ffmpeg
All dependencies mentioned in requirements.txt to be installed. (pip install -r requirements.txt)
Running the project
If you are not using a GPU, head over to backend/keyframes/keyframes.py and set gpu=False(At exactly 2 locations)
You can head over to backend/subtitles/subs.py and change the Whisper model used. (Check supported models here)
Run the flask server: python -m flask --app app run
Open the localhost link on your browser (Eg:http://127.0.0.1:5000)
Running with docker
You can run this project using docker with the following commands:
docker pull reubendinny/cinecomic
docker run --name cinecomic -d -p5000:5000 -e WHISPER_MODEL=small cinecomic
Copy the frames folder and the output folder to a common folder
Open the page.html file in the output folder to view the comic
