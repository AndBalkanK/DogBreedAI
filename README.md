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
