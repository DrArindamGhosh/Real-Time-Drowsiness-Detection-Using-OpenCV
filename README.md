# Real-Time-Drowsiness-Detection-Using-OpenCV
Real Time Drowsiness Detection using OpenCV

Drowsiness detection is a safety technology that can prevent accidents that are caused by drivers who fell asleep while driving. The objective of this project is to build a drowsiness detection system that will detect drowsiness through the implementation of computer vision system that automatically detects drowsiness in real-time from a live video stream and then alert the user with an alarm notification.


## Motivation
Driver fatigue is a serious problem resulting in many thousands of road accidents each year. It is not possible to calculate the exact number of sleep related accidents but research shows that driver fatigue may be a contributory factor in up to 20% of road accidents, and up to one quarter of fatal and serious accidents. These types of crashes are about 50% more likely to result in death or serious injury as they tend to be high speed impacts because a driver who has fallen asleep cannot brake or swerve to avoid or reduce the impact.

Sleepiness increases reaction time (a critical element of safe driving). It also reduces vigilance, alertness and concentration so that the ability to perform attention-based activities (such as driving) is impaired. The speed at which information is processed is also reduced by sleepiness. The quality of decision-making may also be affected.

It is clear that drivers are aware when they are feeling sleepy, and so make a conscious decision about whether to continue driving or to stop for a rest. It may be that those who persist in driving underestimate the risk of actually falling asleep while driving. Or it may be that some drivers choose to ignore the risks (in the way that drink drivers do).

Crashes caused by tired drivers are most likely to happen:
1. on long journeys on monotonous roads, such as motorways
2. between 2am and 6am
3. between 2pm and 4pm (especially after eating, or having even one alcoholic drink)
4. after having less sleep than normal
5. after drinking alcohol
6. if taking medicines that cause drowsiness
7. after long working hours or on journeys home after long shifts, especially night shifts

A study conducted by a traffic safety foundation in the US investigated the relationship between the amount of sleep a driver has had and their likelihood of a collision. The study, being the first of its kind, looked at US road data in the form of the National Motor Vehicle Crash Causation Survey, in order to assess the contributory factors of the crash and how much sleep the driver had had recently. This information was used to compare how much sleep drivers who had been involved in crashes caused by their own unsafe action or error had with how much drivers involved in crashes where this is not the case had. The key findings were that the risk of a collision is significantly increased as drivers have less and less sleep, when compared to drivers who had slept for 7 hours in the last 24 hours. For example, those who had slept for between 5 and 6 hours had 1.9x the collision rate, and those who had slept for 4 hours or less had 11.5x the collision rate. These results show just how dangerous a lack of sleep can be, and how even one or two hours of sleep can make a huge difference in determining a driver’s collision risk.

## Built With

* [OpenCV Library](https://opencv.org/) - Most used computer vision library. Highly efficient. Facilitates real-time image processing.
* [imutils library](https://github.com/jrosebr1/imutils) -  A collection of helper functions and utilities to make working with OpenCV easier.
* [Dlib library](http://dlib.net/) - Implementations of state-of-the-art CV and ML algorithms (including face recognition).
* [scikit-learn library](https://scikit-learn.org/stable/) - Machine learning in Python. Simple. Efficient. Beautiful, easy to use API.
* [Numpy](http://www.numpy.org/) - NumPy is the fundamental package for scientific computing with Python. 


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

1. Install and set up Python 3.
1. Install [cmake](https://github.com/Kitware/CMake/releases/download/v3.13.3/cmake-3.13.3-win64-x64.zip) in your system

## Running the application

1. Clone the repository. 

    ```
    git clone https://github.com/DrArindamGhosh/Real-Time-Drowsiness-Detection-Using-OpenCV.git
    ```
    
1. Move into the project directory. 

    ```
    cd Real-Time-Drowsiness-Detection-Using-OpenCV
    ```
 
1. (Optional) Running it in a virtual environment. 

   1. Downloading and installing _virtualenv_. 
   ```
   pip install virtualenv
   ```
   
   2. Create the virtual environment in Python 3.
   
   ```
    virtualenv -p C:\Python37\python.exe test_env
   ```    
   
   3. Activate the test environment.     
   
        1. For Windows:
        ```
        test_env\Scripts\Activate
        ```        
        
        2. For Unix:
        ```
        source test_env/bin/activate
        ```    

1. Install all the required libraries, by installing the requirements.txt file.

    ```
    pip install -r requirements.txt
    ```
    
1. Installing the dlib library.
     
    1. If you are using a Unix machine, and are facing some issues while trying to install the dlib library, follow [this guide](https://gist.github.com/ageitgey/629d75c1baac34dfa5ca2a1928a7aeaf).  
    
    1. If you are using a Windows machine, install cmake and restart your terminal. 
    
1. Run the application.

    ```
    python Real-Time-Drowsiness-Detection-System.py --shape-predictor shape_predictor_68_face_landmarks.dat --alarm Alert.wav
    ```

## Alogorithm

1. Capture the image of the driver from the camera.
2. Send the captured image to haarcascade file for face detection.
3. If the face is detected then crop the image consisting of the face only. If the driver is distracted then a face might not be detected, so play the buzzer.
4. Send the face image to haarcascade file for eye detection.
5. If the eyes are detected then crop only the eyes and extract the left and right eye from that image. If both eyes are not found, then the driver is looking sideways, so sound the buzzer.
6. The cropped eye images are sent to the hough transformations for detecting pupils, which will determine whether they are open or closed.
7. If they are found to be closed for five continuous frames, then the driver should be alerted by playing the buzzer.
