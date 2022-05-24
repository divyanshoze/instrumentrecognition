[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-f059dc9a6f8d3a56e377f745f24479a46679e63a5d9fe6f495e02850cd0d8118.svg)](https://classroom.github.com/online_ide?assignment_repo_id=6590135&assignment_repo_type=AssignmentRepo)

### Project title: [InstrumentDetection]

# University: University Of Nottingham

# Course: MLiS MSc

## Summary:

Hello there, It's pretty much the same content as one in the previous ReadMe. Apart from getting done with processing data and running feature extractions on train and test audio .wav files corresponding to their JSON file places. 

Now, We got our labels ready i.e. the instrument family code from [0-10] for all instruments in the family to use as targets in Train and Test sets. After getting done with this, we passed the sets through RandomForestClassifier to challenge our model's classification/prediction capability. Further on, we put a confusion matrix to evaluate the performance based on each instrument detected.


### Dataset:
https://magenta.tensorflow.org/datasets/nsynth

### References Used:
1)https://towardsdatascience.com/getting-to-know-the-mel-spectrogram-31bca3e2d9d0

2)https://librosa.org/doc/latest/index.html

3)Librosa: Audio and Music Signal Analysis in Python, Brian McFee



### Libraries Used:

<img width="444" alt="Screenshot 2021-12-15 at 4 11 26 AM" src="https://user-images.githubusercontent.com/93164784/146121829-011e5892-1cb7-46f2-9d26-f973e27098b1.png">



### Implemented:
1) Preprocessing on the NSynth Dataset
2) Feature Extraction from json and .wav audio files 
3) SingleAudioClip to demonstrate how Feature Extraction and Visualization works
4) SingleAudioClip to understand the Anatomy of a Wave File
5) Prepared sets of Train and Test with Feature List and Target Labels
6) Passed it through the RandomForestClassifier to get predictions
7) Evaluated the model's performance through Confusion Matrix

# Module Division-

## Feature Extraction:

<img width="648" alt="Screenshot 2021-12-15 at 4 16 33 AM" src="https://user-images.githubusercontent.com/93164784/146122280-443b1f1b-2d7f-4730-8423-1764fe5949ec.png">


In this module, we take in a file and use the audio .wav components to extract features like spectrogram, mfcc, chroma energy, contrast etc
Since features like spectrogram give out activated form values in form of M x N array, we did temporal averaging for each feature that it can be added further to Classifiers in tabular format.

Achieved through this Module:
1) Loading the signal from the file
2) Check if it's harmonic or percussive
3) Received values for all visuals features through using Librosa
4) Converted those feature values in 1D array form after temporal averaging 


## Instrument Classs-

<img width="815" alt="Screenshot 2021-11-24 at 1 56 37 PM" src="https://user-images.githubusercontent.com/93164784/143251691-4d4e97c8-3e11-4bda-9112-be159f2ecab9.png">

  In this module, we take in a file and return the corresponding label for the file i.e. instrument based on naming convention
  We run the loop over each file within the passed filename and match it with the classlabels that we have defined for the entire dataset.
  ClassLabels here are all the instruments serving as target labels for the dataset.
  
  Achieved through this Module:
  1) Instrument Code after matching the file and predefined classlabels
  2) Helped in getting instrument family codes to be used as Targets variable column in Training/Testing set
 
 # Visualization results-
 
 [After running a specific instrument audio clip]
 
 ### Waveform Representation:
 <img width="404" alt="Screenshot 2021-11-24 at 2 10 31 AM" src="https://user-images.githubusercontent.com/93164784/143255007-36a28b0d-d766-4d93-b0d1-e35846a0c7ed.png">
 
### Mel Spectrogram [log powered dB]
<img width="423" alt="Screenshot 2021-11-24 at 2 13 15 AM" src="https://user-images.githubusercontent.com/93164784/143255070-b2832ee5-e212-4e30-b2a3-29b4b43da6b2.png">

### MFCC
<img width="359" alt="Screenshot 2021-11-24 at 2 13 22 AM" src="https://user-images.githubusercontent.com/93164784/143255083-aec38a0e-4467-4d68-a6ff-a75d291ffe5f.png">

### Chroma Energy
<img width="397" alt="Screenshot 2021-11-24 at 2 13 29 AM" src="https://user-images.githubusercontent.com/93164784/143255097-e8cbd940-08d9-41bf-b418-d416907f4ac3.png">

### Contrast
<img width="425" alt="Screenshot 2021-11-24 at 2 13 38 AM" src="https://user-images.githubusercontent.com/93164784/143255144-40118069-8aa8-4b96-bd36-55acc7a62d86.png">

## Confusion Matrix:

[After running the Random Forest Classifier on the Model]

<img width="346" alt="Screenshot 2021-12-15 at 1 44 50 AM" src="https://user-images.githubusercontent.com/93164784/146123916-75730d2f-5189-44d4-acbe-10c033421b46.png">

  
 # Important takeways -
 
 -Since the size of the actual NSynth Training file was of 25-26gb, we had the valid set as one for training the model; was interested in learning about how this    task can be implemented using python and not worry about how and what dataset we are using.
 
  -We had put visualizations, audio beep for you to hear the audio clip whenever it's passing through the function: scrapped it from this file to SingleAudioClip to show the visuals and anatomy in a more simpler scale. Those visuals from all train and test files were not really contributing for the final task i'm performing here so I decided to study about them in a different file and play with the libraries to learn.
  
 -We got each feature a separate column based on their index which was required, because passing the list for each column value was creating a problem when passing it through the Classifier at the end. 
 
-We sampled the train file for 400 per family instrument because of the unequal distribution between files in the NSynth Dataset.

-'Fanciest Algorithm isn't always the optimal algorithm to use', some quote i'm paraphrasing but makes perfect sense in case of our model. We managed to get good accuracy on using the Random Forest without having to put the Neural Network like CNN.


# Files Attached:
1) InstrumentDetection.ipynb , which prepares our featurelists with labels.
2) RandomForestClassifier.ipynb , which we use to predict targets on our Test set after training on the Train set.
3) SingleAudioClip.ipynb , the cherry on top which lets us study the anatomy of a wave file and get some cool visuals for the extracted features.
4) Audio .wav file  to run on for the SingleAudioClip.ipynb
5) Folder for all visualizations we have got.
 
# Improvements-

-We try to run it on an actual song to identify the main instrument playing throughout
-Turn the thing from being a supervised learning to unsupervised learning model, not give the model any hints and test our extracted features to the limits
-Live visual representation for a clip playing, to see how pitch/freq/amplitude varies [like a equalizer in audio systems but ofcourse not to tune the settings]


