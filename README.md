### 2022_KSW_Fall_Program

### Team Coyote2 : Deep Learning

## Project Title

 Comparison of Combinations of Machine Learning and Feature Extraction Methods for Coyote Howling Detection
 
## Project Period
 Sep/05/2022 ~ Dec/19/2022 

## Project Content
1. [Collaborator](#collaborator)
2. [Project Overview](#project-overview) 
3. [Research problem statements](#research-problem-statements)
4. [Research novelty](#research-novelty)
5. [Environment Setting](#environment-setting)
6. [Experiment](#experiment)
<!--   - [File Structure](#file-structure)
    - [Dataset](#dataset)
    - [Requirments](#requirments) -->
<!--
    - [Result](#result)     
    - [Model Architecture](#mode-architecture) -->

## Collaborator

| Name         | University               | Department                                   | Email               | Contact                        |
| :------------- | :------------------------: | :--------------------------------------------: | :-------------------: | :------------------------------: |
| Yejin Lee    | Hallym University        | Dept. of Computer Science                    | leeye0616@naver.com | https://github.com/yetniek     |
| Heesun Jung  | Hallym University        | Dept. of Computer Science                    | glee623@naver.com   | https://github.com/glee623     |
| Youngbin Kim | Kwangwoon University     | Dept. of Computer Information                | binny9904@naver.com | https://github.com/0binn       |
| BoKyung Kwon | Kwangwoon University     | Dept. of Computer Information                | bbo1209@naver.com   | https://github.com/doomdabo    |
| Jihyun Park  | Jeju National University | Dept. of Computer Science & Statistics       | mmmszip@gmail.com   | https://github.com/mmmtobezip  |
| Griffin Pegg | Purdue University        | Dept. of Computer and Information Technology | pegge@purdue.edu    | https://github.com/coyotehowls |


## Project Overview

<p align="center">
        <img width="1090" alt="Project Overview" src="https://user-images.githubusercontent.com/101625865/208316299-e9b93b6f-1490-4d27-b444-87749f42c18d.png">
</p>

## Research problem statements 

The attacks on livestock, human, and crops by coyotes are occurring over the United States, while traditional simple management such as public
education about the method of avoiding coyotes and coyote hunting contests to reduce their numbers are executed. There are not sufficient cases of
technical approaches or research about the damage to coyotes. 

## Research novelty 
1. This project suggests the optimal coyote detection platform by comparing various feature exatraction and machine learning methods.
2. This project suggests the coyote howling sound detection method that does not exist in the past.
3. The problem of coyote damage can be solved by technical ways.
    
## Environment Setting

>##### File Structure
    📦2022-ksw-fall-program-final-team-coyote/
      └📂dataset
        └📂image
          └📂img_mfcc_8000
           └📜bird_1.jpg
           └...
          └📂img_mfcc_16000 
           └📜bird_1.jpg
           └...
          └📂img_melspect_8000
           └📜bird_1.jpg
           └...
          └📂img_melspect_16000
           └📜bird_1.jpg
           └...
        └📂audio
          └📜bird_1.wav
          └...
        └📜valid.csv
        └📜train.csv
        └📜test.csv
        
     └📂code
       └📂make_audio_dataset
        └📜audio_split.ipynb
        └📜csv_extraction.ipynb
       └📂make_image_dataset
        └📜image_extraction.ipynb
       └📂deep_learning
        └📜CNN_audio.ipynb
        └📜CNN_image.ipynb
       └📂machine_learning
        └📜ML_audio.ipynb
        └📜ML_image.ipynb
       └📂mic
        └📜mic_experiment.py
        └📜utils.py
        └📜audio_mfcc_16000_best_model_.pth 
       └📜requirements.txt

>##### Dataset
<p align="center">
<img width="712" alt="스크린샷 2022-12-18 오후 6 42 17" src="https://user-images.githubusercontent.com/101625865/208325663-cfcb2bf5-3b74-4823-b3ae-1181f2e66a45.png">
</p>

>##### Requirements
    The experimental setting is as follows: 
       
    - Raspberry Pi OS : Debian (64-bit)
    - Raspberry Pi 4 Model B+ (4GB)
    - Python version 3.8.10
    - Other Library : requirements.txt

## Experiment

>##### Best Result
|   |Audio|Image|
|---|:-:|:-:
|Sampling Rate|16,000|16,000|
|Model|CNN Layer 3|CNN Layer 3|
|Feature Extraction|MFCC|Mel Spectrogram|

>##### Model Architecture

<p align="center">
<img width="1163" alt="Project Overall Architecture" src="https://user-images.githubusercontent.com/101625865/208327334-3429c632-3135-48fb-8b3a-5cf896225ce3.png">
</p>
Three microphones are connected into raspberry pi. Each microphone records 3 second repeatedly and we put that data into model right away which put in Raspberry pi. Model will predict whether it is coyote or not. If it was coyote, network team transmit the time stamp to the gateway by Lorawan and three different time values of the coyote sound will determine the location of the coyote. And then they visualize the location on the map.

>##### Hyper Parameter for Best Model 

    ✔ Audio
    - Optimization function : Adam optimizer
    - Learning rate : 0.001
    - Batch size : 10
    - Epoch : 30 
    - Sampling rate : 16,000 (MFCC)
    
    ✔ Image
    - Optimization function : Adam optimizer
    - Learning rate : 0.001
    - Batch size : 32
    - Epoch : 30 
    - Sampling rate : 16,000 (Mel Spectrogram)
    
