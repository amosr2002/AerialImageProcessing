# AerialImageProcessing

This Project is my undergraduate capstone project which I am working on currently. The goal of this project is to train a neural network to identify the target objects in the image. Aside from the first goal, GPS tracking can be hard for Parachute location tracking because of signal jamming/interference. So the next goal which I am currently working on is training a neural network which takes in the predicted pixel class matrices from the panoptic segmentation. The neural network will take in two of the predicted pixel class matrices and have the actual geographic location for both images, and we are trying to predict the difference between the two locations. With this methodology, we are hoping to constantly update the location of the parachute. My partners are working on developing a simulator that creates synthetic parachute flight path video feeds. I am currently developing scripts to create a training dataset for the neural network.

I have not had much image processing experience in the past, so I have also included a couple of my notebooks which I created for tutorial/learning purposes.

For the Object/Semantic Segmentation tasks I used the highly popular Pytorch Detectron2 Library. Detectron2 offers pre-trained instance/panoptic segmentation models that are trained on millions of images. Detectron2 also allows to fine-tune/re-train on custom datasets.

- Detectron2_Instance_Segmentation_and_Custom_Training_Dataset_tutorial (1).ipynb
  - This notebook includes the code for the instance segmentation detectron2 model
    - Instance segmentation classifies objects in an image. For example, if there is a car and a bike, the instance segmentation model will predict those objects
    - The image below is the result of instance segmentation
    ![image](https://user-images.githubusercontent.com/77814810/204119392-12924043-f6c3-4de3-b595-623453cff515.png)

    - Semantic Segmentation is pixel level classification. Each Pixel in the image is assigned a class label.
  - This notebook also includes the code for the custom dataset training in detectron2
  
- MQP_Detectron2 (1).ipynb
  - This file includes the images I used as inputs for the panoptic segmentation. The main image I used for the panoptic segmentation was an image of the Antigua island. The panoptic segmentation classified the Sky, Sea, Mountain, and Grass regions. The reason I used an image of the Antigua island is because the synthetic parachute video feeds will include grass, sky, and sea regions. I also tried finding the boundary lines in an image to guide the parachute where to land.
  - The image below shows the result of the panoptic segmentation
  ![image](https://user-images.githubusercontent.com/77814810/204119374-bc452c58-cb86-47ae-bfda-d53b47163e09.png)
  - With this image we can access a Pixel matrix. For example the top of the image is the Sky, so the top rows of the matrix will have values that represent the sky class. The bottom rows of the matrix will have values that represent the sea.
    - So this matrix will be used to train another neural network to track the location of the parachute

  
- OpenCVProcessing.ipynb
  - This file includes code where I practiced using various OpenCV Functions. I experimented with contour detection, edge detection, grayscaling, blurring, etc.
