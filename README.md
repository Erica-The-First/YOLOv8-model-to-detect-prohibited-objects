# Real-time video surveillance using YOLOv8 model to detect objects

  

This repository contains a step-by-step guide to deploy YOLOv8 (Python 3.12)with for Real-time video surveillance using a personal computer, including the statistics and accuracy results

  
  

## TABLE OF CONTENTS

**CHAPTER 01**: Prepare Materials
1. Images needed to lable to Label Studio
2. Install Anaconda as a Virtual Environment
3. Install Label Studio and run it

**CHAPTER 02**: Label Studio
1. Set up local Environment to make a project 
2. Start labeling (things to be cautious about)
3. Export to file Option

**CHAPTER 03**: AI Training in Google Colab
1. Specifications needed for Google Colab
2. Training in Google Colab
3. Export All Files and Folders from Google Colab to a Zip File

**CHAPTER 04**: Run The Training Result
1. Create a Virtual Environment to run The Training Result
2. Specifications needed for The Virtual Environment
3. Run the Program
  
---
### **CHAPTER 01**: Prepare Materials

  
  
#### 1. Images needed to label for Label Studio
- Make sure to collect pictures or images are taken from MANY positions, lightings, distances, variations of the targeted object at hand, etc...
- The amount of images or pictures as a dataset doesn't have any minimal requirements, but it would be ideal for the amount to be more than 200.
- YOU DO NOT NEED TO label an image if the image in question is way too similar to another image that is already labeled (a carbon copy or a near carbon copy). So make sure there isn’t any case like image being too similar with another in the Dataset

 

#### 2. Install Anaconda as a Virtual Environment
1. go to https://www.anaconda.com/download/success
	- or you could go to https://www.anaconda.com/download, and then click "Skip registration."
2. Download the one in accordance with the Operating System (OS) you're using.
3. Once the installation is done, run the program and then quit it (It will be used *later*).

 

#### 3. Install Label Studio and run it
##### Install Label Studio
go to https://labelstud.io/guide/install to install Label Studio
to put it simply, 
1. Open Terminal
2. make sure you're in Local root folder
	- or if you run it in any Virtual Environment, it should be fine too
	- Be wary that in **some cases**, if you run it in a different Root, Label Studio might not work
```text
pip install label-studio
```

##### Run Label Studio
1. Open Terminal
2. make sure you're in Local root folder
	- or if you run it in any Virtual Environment, it should be fine too
	- Be wary that in **some cases**, if you run it in a different Root, Label Studio might not work
```text
label-studio start
```

- After running it, the default browser will automatically open a Local Environment
- Sign in, or Sign up
	- This will create A local Account, so the email doesn't need to be an official/verified one

---
### **CHAPTER 02**: Label Studio

  
  
#### 1. Set up local Environment to make a project 
once the You have logged in, Create a new Project, and fill in the three circumstance:
- Name Of the Project
- Data Import
	the Ideal Amount when Uploading data is 100 data at a time (when uploading too much all at once, the wanted data might not be uploaded at all)
- Labeling Setup
	Pick a method to label your data. I'll be using **Object Detection with Bounding Boxes**

##### !Warning!
DO NOT separate one project from another if the plan is to combine the contents inside the file from each project AFTER BEING EXPORTED.

When the AI Training starts, they would read the contents inside the file in a specific queue according to what is written while exporting the labeling result from the local environment.


 

#### 2. Start labeling (things to be cautious about)
- It is recommended to label it fit when labeling the object. The box should not be too big, nor too small, to the corresponding object at hand 
- YOU DO NOT NEED TO label an image if the image in question is way too similar to another image that is already labeled (a carbon copy or a near carbon copy).
- When the item is unseen, no need to label it

 

#### 3. Export to file Option
Once the labeling is done, the result then needs to be exported. There will be many options for what the file type is once it is exported. Considering the YOLOv8 is what we will be Using, In this case we'll choose **YOLOv8 OBB with Images** as an Export, 

---
### **CHAPTER 03**: AI Training in Google Colab
link to Google Colab to Train the AI:
	https://colab.research.google.com/github/EdjeElectronics/Train-and-Deploy-YOLO-Models/blob/main/Train_YOLO_Models.ipynb

Reminder to Read all the part to fully understand how the trianing works,
BUT to not take too much time, following the steps bellow should be enough to understand on what facilities that are given from The Google Colab.
  
  
#### 1. Specifications needed for Google Colab
Make sure the Runtime: (at the top left side of the screen)
	click "Runtime", then pick "Change runtime type"
	- Runtime type: Python 3
	- Hardware accelerator: T4 GPU
	- Runtime version: Latest (recommended)

 

#### 2. Training in Google Colab
##### 1. Verify NVIDIA GPU Availability
Run the block of code, as shown below:
![[Screenshot 2025-09-29 at 16.37.54.png]]
##### 2. Upload Image Dataset and Prepare Training Data
1. Use the exported file that consists of labeled images before, then rename it to "data"
	- ex: "project1.zip" to "data.zip"
2. and then upload it to the file side
	You can choose to drag the file into the red box or upload it manually 
	![[Screenshot 2025-09-29 at 16.31.26.png]]
##### 3. Unzip the file
To unzip the file, run the code below (by clicking the play button):
![[Screenshot 2025-09-29 at 16.45.09.png]]

##### 4. Create the required folder structure
To create the required folder structure, click the play button:
![[Screenshot 2025-09-29 at 16.50.04.png]]

##### 5. Install Ultralytics
Click the play button:
![[Screenshot 2025-09-29 at 17.16.12.png]]

##### 6. Configuration
make a config file, click the play button:
![[Screenshot 2025-09-29 at 17.24.27.png]]

##### 7. Run Training
Make modification from the part selected below:
![[Screenshot 2025-09-29 at 17.30.23.png]]

From "yolo11s" to "yolov8s",
```text
yolov8s
```

After modifying, run it:
![[Screenshot 2025-09-29 at 17.37.03.png]]

##### 8. Text Model
to arrange the file needed for testing:
![[Screenshot 2025-09-29 at 19.43.24.png]]

to test:
![[Screenshot 2025-09-29 at 20.04.30.png]]

##### 9. Download YOLO Model
to download the model, you can pick any of the button below
![[Screenshot 2025-09-29 at 20.13.24.png]]
Do be mindful that the first one will make "my_model.zip" file then need to be downloaded manually and not automatically 

You'll see this in the folder section
![[Screenshot 2025-09-29 at 20.24.35.png]]

![[Screenshot 2025-09-29 at 20.24.38.png]]

#### 3. Export All Files and Folders from Google Colab to a Zip File
If you would like to download all the files related to this, 

make a new block of code in the Google coleb:
![[Screenshot 2025-09-30 at 13.08.39.png]]

Paste the code below to the block:

```text
!zip -r /content/all_files.zip /content/
```

As shown below, then play the button:
![[Screenshot 2025-09-30 at 14.03.21.png]]

After you finish running it, the "all_files.zip" file will appear in the file section, as shown in the image below:
![[Screenshot 2025-09-29 at 16.31.26.png]]

and then download the "all_files.zip" file.


### **CHAPTER 04**: Run The Training Result
We will be using CLI (Not GUI)

  
  
#### 1. Create a Virtual Environment to run The Training Result
##### 1. Open your Terminal 
Make sure, before you continue, that you're in local root 
##### 2. run 
```text
conda create —-name yolov8 python=3.12
```
 This will make a virtual environment while also installing the version of Python needed to run 
##### 3. Activate Virtual Environment  
```text
conda activate yolov8
```

to look for Python version:
```text
conda list python
```
##### 4. Change Directory to my_model
```text
cd /Users/~/my_model
```
the "~" stand for the path needed till "my_model" folder
	The result from this is the user's current directory being "my_model"

#### 2. Specifications needed for The Virtual Environment

sending data, including files, using URL syntax
```text
curl -o yolo_detect.py https://www.ejtech.io/code/yolo_detect.py
```
to get the data needed to run the program
_source: https://youtu.be/r0RspiLG260?si=xeDLuV2luVzrnPJH_

#### 3. Run the Program
to run the program, prompt the command below
```text
python yolo_detect.py --model my_model.pt --source usb0 --resolution 1280x720
```

result:
![[Screenshot 2025-09-26 at 01.48.21_ccopy 2.png]]


---
Keep in mind that these results aren't always smooth, and may cause an unexpected result
	If this do happen, it is recommended to look more deeper into the model or the in any step of the process needed to be modified.# YOLOv8-model-to-detect-prohibited-objects
