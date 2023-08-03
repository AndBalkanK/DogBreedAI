# DogBreedAI
This AI will show you the breed of any dog in the list (e.g. German shepherd, golden retriever, italian greyhound, shih tzu, and toy terrier). It is used if you would want to see what breed of dog any of them are because maybe you would want to get that breed of dog. 

# The Algorithm
This re-trained ResNet-18 model was created on Jetson Nano and trained on a dataset of five different dogs images ( german shepherd, golden retriever, toy terrier, italian greyhound, and shih tzu). It runs on an imagenet.py program that will classify the snake as either species.

# Running This Project
Make sure that both the Jetson Inference library and Python3 are installed on your Jetson Nano.
Download the resnet18.onnx and model_best.pth.tar. Links to the models: (https://drive.google.com/drive/u/0/folders/1gJKHu09UoMbe0EvLXrBIfYXrUDE_lXbs)
Download the data folder (images). Link to data: (https://drive.google.com/drive/folders/1kZluwzSqHIF3zsrDVIAJJBa2GEeEgW_0?usp=drive_link)
Open the terminal and navigate to the classification directory:
```
   $cd jetson-inference/python/training/classification
```
Set the net and data variables as shown below:
```
   $NET=models/Dog_breeds
   $DATASET=data/Dog_breeds
```
Use this command to process an image:
```
   $imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/golden_retriever/n02099601_7037.jpg dog.jpg
```
Alternatively, if you would like to use your own dog classification images, add it to the data directory and go to google colab (this link https://colab.research.google.com/drive/122jLDEXT8WF9Mf_OC0AIzlXeF56o6GFg#scrollTo=eo3hVo4myykM to re train the network)
Finally, view the image output to see the classification as the dog type
View a video explanation here: https://youtu.be/146F73EHEXs

# A more in depth view
Make sure that both the Jetson Inference library and Python3 are installed on your Jetson Nano.
Download the model_best.pth.tar file and the Dog_breeds folder. Link to the files: https://drive.google.com/drive/folders/1kZluwzSqHIF3zsrDVIAJJBa2GEeEgW_0?usp=drive_link and https://colab.research.google.com/drive/122jLDEXT8WF9Mf_OC0AIzlXeF56o6GFg

Open the terminal on your nano and navigate to the classification directory:
```
   $ cd jetson-inference/python/training/classification
```
Create two new directories, data and models:
```
   $ mkdir data
   $ mkdir models
```
Navigate to the models directory and create a new directory called Dog_breeds:
```
   $ cd models
   $ mkdir Dog_breeds
```
The data directory is where you would import your image files to be able to get the images

Upload the model_best.pth.tar file to the Dog_breeds directory in the models directory and upload the Dog_breeds folder to the data directory.
Navigate to the jetson-inference directory and run the docker:
```
   $ cd ../../../../
   $ ./docker/run.sh
```
Navigate to the classification directory again:
```
   $ cd python/training/classification
```
Export the model to ONNX:
```
   $ python3 onnx_export.py --model-dir=models/Dog_breeds
```
Exit the docker and navigate to the classification directory again:
```
   $ exit
   $ cd python/training/classification
```
Set the NET and DATASET variables:
```
   $ NET=models/Dog_breeds
   $ DATASET=data/Dog_breeds
```
Run this command to see how it operates on an image from the Dog_breeds test folder:
```
   $ imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/golden_retriever/n02099601_7037.jpg dog.jpg
```
Open the new image in VSCode to see how the model works or scroll up to see how the model classified the image if you are using a regular terminal.

To run the model on a different image, change this section of the code: /dog breed/image name.jpg save.jpg
The first 'dog breed' refers to which set of images in the test folder you are choosing from. 'image name.jpg' is the image you are classifying in the set of images you chose. Finally, 'save.jpg' is the name of the image that will be exported once the model finishes classifying it.
