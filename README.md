# Real-Time-Drowsiness-Detection# Realtime-Drowsiness-Detection

# Real-time Drowsiness Detection


It aims to develop a real-time drowsiness detection system for individuals in a video feed. The system will first detect faces in the video and then classify them as drowsy,low vigilant or awake using a pretrained model trained on a dataset of alert,low vigilant and drowsy individuals. The model will output a probability score for each class, and the system will use a threshold to determine whether the individual is drowsy or awake along with localisation of the class(bounding box). This approach can have practical applications in driver safety and workplace safety, but the system's accuracy will depend on the quality of the face detection algorithm, the training data, and the threshold chosen.




The github repo consists of 6 jupyter notebook files each of which performs a specific subtasks of the overall project.
We have used [kaggle](https://www.kaggle.com) for training.
## 1. Dataset Collection and Preprocessing

UTA-RLDD(Real Life Drowsiness Dataset)  is used for training and validation and custom dataset for testing, it was created for the task of multi- stage drowsiness detection, targeting not only extreme and easily visible cases, but also subtle cases of drowsiness. 

The three classes were explained to the participants as follows:
1) Awake: Subjects were told that being alert meant they were experiencing no signs of sleepiness.
2) Low Vigilant: this state corresponds to subtle cases when some signs of sleepiness appear, or sleepiness is present but no effort to keep alert is required.
3) Drowsy: This state means that the subject needs to actively try to not fall asleep.

We have extracted images from these videos and notebook for the code is [dataset_preparation.ipynb](dataset_preparation.ipynb). Anyway We have already extracted the images and uploaded in kaggle to be used.
To use kaggle datasets kaggle must be installed as follows :

 ``` pip install kaggle ```

All datasets api command are already provided in [datasets.txt](datasets.txt).

For YOLOv5 model the repo as well as dataset is present in ``` data/train ``` folder consisting of 330 labelled(in yolo format) images of each class(awake,drowsy,low vigilant). These images are subset of the pre-processed larger dataset

## 2. Baseline Model Set up

The base CNN architecture is used for classification and validation accuracy is reported. Wandb is integrated for hyperparameter tuning. To install **wandb** following command can be used

``` pip install wandb ```
There are 2 versions for this task one where dataset is further divided into 5 folds as in original and validate on one random fold and train on remaining 4 folds and another is ususal train and val split on entire dataset .

The code for the verion 1 is present in [drowsiness-kfold-baseline.ipynb](drowsiness-kfold-baseline.ipynb).

The code for the version 2 is present in [drowsiness-baseline.ipynb](drowsiness-baseline.ipynb).

## 3. Finetuned Model Set up

This part is very similar to previous one and **wandb** is again used for hyperparameter tuning and tested on several pretrained models like **ResNet50 , InceptionV3, etc** .Same dataset(version 1) is used  for training and validation.

The code for the above is present in [drowsiness-finetune-v1.ipynb](drowsiness-finetune-v1.ipynb).

## 4. Testing and Visualization 

Since the models are tracked using **wandb**. One of the stored models can be used for testing and visualization. 

The code for the above is present in [drowsiness-baseline-test.ipynb](drowsiness-baseline-test.ipynb).

## 5. YOLOv5 Model Set up

For realtime drowsiness detection in video Yolo provides very efficient implementation for object detection which is used for drowsiness detection

The training and testing is again integrated with **wandb**. 

The code for the above is present in [yolov5-drowsiness-detection.ipynb](yolov5-drowsiness-detection.ipynb).

All the results and comments for our project is present in the [Project Report.pdf](Project%20Report.pdf)

For viweing the runs in wandb refer [Drowsiness detection](https://wandb.ai/ipda526)

