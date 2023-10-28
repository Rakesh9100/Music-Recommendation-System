# <p align="center">🎵Music-Recommendation-System🎵</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<div id="top"></div>

<h2>Table of Contents🧾</h2>

- [Introduction📌](#introduction)
- [Technology Used🚀](#technology-used)
- [Dataset Used📊](#dataset-used)
- [Getting Started💥](#getting-started)
- [Model Architecture⭐](#model-architecture)
- [Image Processing and Training📈](#image-processing-and-training)
- [Current condition✨](#current-condition)
- [Project Components📊](#project-components)
- [Issue🤔](#issue)
- [Further Works💫](#further-works)
- [Contributing Guidelines📑](#contributing-guidelines)
- [Code Of Conduct📑](#code-of-conduct)
- [Project Admin⚡](#project-admin)
- [Contributing is fun🧡](#contributing-is-fun)
<br>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Introduction📌</h2>

A Music Recommendation System Project using Flask web app that recommends music based on our facial expressions using FER-2013 Dataset and Spotify API.
- Song recommendations using Real time expression detection.
- Song Playlists is fetched from Spotify using API.
- A simple Neumorphism UI for website.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Technology Used🚀</h2>

- Keras
- Tensorflow
- Spotipy
- Flask
- Tkinter (For testing)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Dataset Used📊</h2>

The dataset used for this project is the famous FER2013 dataset by Kaggle. Models trained on this dataset can classify 7 emotions. The dataset can be found <a href = "https://www.kaggle.com/msambare/fer2013">here</a>.

The emotion categories includes:
- 0 = Angry
- 1 = Disgust
- 2 = Fear
- 3 = Happy
- 4 = Sad
- 5 = Surprise
- 6 = Neutral

It should be noted that the dataset is highly imbalanced with happy class having maxiumum representation. This might be a factor resulting in okayish accuracy after training the data.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Getting Started💥</h2>

- Fork this Repository.
- Clone the forked repository in your local system.
```
git clone https://github.com/<your-github-username>/Music-Recommendation-System.git
```
- Open the project folder in any local editor like Visual Studio Code.
- Run `pip install -r requirements.txt` to install all the dependencies.
- In the file Spotipy.py, Enter your credentials generated by your Spotify Developer account in 'auth_manager'.<br>
`Note:-` This is only required if you want to update your recommendation playlists. Also uncomment import statement in `camera.py`.
- Run the main file `app.py` and give the camera permission if asked to detect the real time expressions.

<p align="right">(<a href="#top">back to top</a>)</p>

- Raise an issue if you find a bug or add a feature.
- Wait for the issue to be assigned and proceed only after the issue is assigned to you.
- Navigate to the project directory.
```
cd Click-The-Edible-Game
```
- Create a new branch for your feature.
```
git checkout -b <your_branch_name>
```
- Perfom your desired changes to the code base.
- Track and stage your changes.
```
# Track the changes
git status

# Add changes to Index
git add .
```
- Commit your changes.
```
git commit -m "your_commit_message"
```
- Push your committed changes to the remote repo.
```
git push origin <your_branch_name>
```
- Go to your forked repository on GitHub and click on `Compare & pull request`.
- Add an appropriate title and description to your pull request explaining your changes and efforts done.
- Click on `Create pull request`.
- Congrats! 🥳 You've made your first pull request to this project repo.
- Wait for your pull request to be reviewed and if required suggestions would be provided to improve it.
- Celebrate 🥳 your success after your pull request is merged successfully.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Model Architecture⭐</h2>

The model architecture is a sequential model consisting of Conv2d, Maxpool2d, Dropout and Dense layers:
1. Conv2D layers throughout the model have different filter size from 32 to 128.
2. Pooling layers have pool size (2,2).
3. Dropout is set to 0.25 as anything above results in poor performance.
4. Final Dense layer has 'softmax' activation for classifying 7 emotions.

- Used 'categorical_crossentropy' for loss with 'Adam' optimizer with 'accuracy' metric.

Note:- Tried Implementing various other models like VGG16 but accuracy was far too low. This model architecture gives good enough accuracy. A bit more tinkering with hyper parameters might lead to a better accuracy.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Image Processing and Training📈</h2>

- The images were normalised, resized to (48,48) and converted to grayscale in batches of 64 with the help of 'ImageDataGenerator' in Keras API.
- Training took around 13 hours locally for 75 epochs with an accuracy of ~66 %.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Current condition✨</h2>

The entire project works perfectly fine. Live detection gives good frame rates due to multithreading.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Project Components📊</h2>

- Spotipy is a module for establishing connection to and getting tracks from Spotify using Spotipy wrapper.
- haarcascade is for face detection.
- camera.py is the module for video streaming, frame capturing, prediction and recommendation which are passed to main.py.
- main.py is the main flask application file.
- index.html in 'templates' directory is the web page for the application. Basics of HTML and CSS.
- utils.py is an utility module for video streaming of web camera with threads to enable real time detection.
- train.py is the script for image processing and training the model.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Issue🤔</h2>

The app in current state can't be deployed on web as:
- Opencv tries to open the camera on whatever device the app is running on. Code in current state makes use of webcam if available on server side not client side. So when app is run locally on a laptop Video Streaming through webcam is possible. But if it's deployed to a cloud, the app is stored in a data center somewhere which obviously doesn't have web camera connected to it and hence it doesn't work.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Further Works💫</h2>

- Instead of CSVs, create a databse and connect it to an application. The DB will fetch songs for recommendations and new songs can be updated directly onto database.
- Add a feature which will update specified playlists for better and more recent recommendations, a specific day over a fixed duration say every sunday and append it to database.
- Directly play the song or redirect to the song on Spotify when user clicks on it.
- Rewrite code such that Video Streaming is done on client side instead of server side so as it make the app deployable.

Note: Model accuracy is not that great. It is ~66%. Further training and finetuning required. May try Vision Transformer Model.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Contributing Guidelines📑</h2>

Read our [Contributing Guidelines](https://github.com/Rakesh9100/Music-Recommendation-System/blob/main/.github/CONTRIBUTING_GUIDELINES.md) to learn about our development process, how to propose bugfixes and improvements, and how to build to Music-Recommendation-System.

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Code Of Conduct📑</h2>

This project and everyone participating in it is governed by the [Code of Conduct](https://github.com/Rakesh9100/Music-Recommendation-System/blob/main/.github/CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Project Admin⚡</h2>

<table>
<tr>
<td align="center">
<a href="https://github.com/Rakesh9100/"><img src="https://avatars.githubusercontent.com/u/73993775?v=4" height="140px" width="140px" alt="Rakesh Roshan"></a><br><sub><b>Rakesh Roshan</b><br><a href="https://www.linkedin.com/in/rakesh-roshan-9100/"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/73993775/278833250-adb040ea-e3ef-446e-bcd4-3e8d7d4c0176.png" width="45px" height="45px"></a></sub>
</td>
</tr>
</table>

<!-- --------------------------------------------------------------------------------------------------------------------------------------------------------- -->

<h2>Contributing is fun🧡</h2>

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)
<h3>Contributions of any kind from anyone are always welcome🌟!!</h3>
<h3>Give it a 🌟 if you ❤ this project. Happy Coding👨‍💻</h3>

<p align="right">(<a href="#top">back to top</a>)</p>

