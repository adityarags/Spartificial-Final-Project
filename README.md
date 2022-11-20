<p align="center">
<img src="https://discordhome.com/user_upload/backgrounds/7864background.jpg" style="width:100%">
</p>

# Final Project
#### Work by: Aditya R


# Goal of the Project
<!-- <p align="center" >
  <img src="https://media.giphy.com/media/1lFP84yOvlEtLCbFCX/giphy.gif" style="height:100px">
 </p> -->
 
The aim of the project is to improve the `val_iou_score` of a given model that performs image segmentation to analyze the surface of the moon.  


# Dataset Used
For this project, the **Artificial Lunar Landscape dataset** has been used.  
<a href="https://www.kaggle.com/datasets/romainpessia/artificial-lunar-rocky-landscape-dataset"> Link to the Kaggle Dataset </a>





# 🤞Attempts

### Preliminary Attempt
No Changes made to any parameters!

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202579375-6731545b-9880-4db2-aaff-e0dd9f6f500d.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202579311-c0c02667-6ede-4de7-890d-4ed00aa0fd5f.png)

---


### Attempt 1
Noticed that the original shape of the image is 480 x 720, but the original notebook was resizing the image to 256 x 256. By reducing the size of the image, many features in the image are lost. This is why I changed the height and width of the image to the original image's height and width.  
**Parameters Updated:**  
1. Image Height = 480
2. Image Width = 720  

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202914515-59d340ba-a45a-4d45-bbef-2caceb3ed277.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202582976-a89a60c6-5c1e-4087-9c9a-953ccb265f03.png)

**Notes:**
In only 5 epochs, it seems to have lower score than the original notebook.

---

### Attempt 2
Since the number of epochs is too low, tried increasing the number of epochs to 10 to check for improvement.

**Parameters Updated:**  
1. Epochs = 10

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202806467-7d26d6b9-99de-44f4-a34c-513b7b438990.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202806498-81efd489-dacc-4044-ac82-c9a1af9cde4b.png)


**Notes:**
Increasing the epochs have shown improvements in the model's `val_iou_score`.

---
### Attempt 3
Decreasing the batch size to 8 in order to have the model train on more images on each epoch. Increased the number of epochs to 20 to check the effect.  
**Parameters Updated:**  
1. Batch Size = 8
2. Epochs = 20

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202818322-dadd380c-a62d-43ca-80cf-7cd67cea221e.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202818411-e8eefee8-65fe-44d7-9150-f16a7d118a64.png)

**Notes:**
Decreasing the batch size does create a noticeable improvement in the model's `val_iou_score`.

---
### Attempt 4
Transfer learning using VGG16 model: Since the traditional method of manually creating tensorflow layers and building a UNet seems to result in lower val_iou_scores, we can try incorporate Trasfer learning using the VGG16 pretrained model.  
Since the VGG16 model accepts only square images as input, input image shape was changed to (480, 480, 3).  
**Parameters Updated:**  
1. Batch Size = 8
2. Epochs = 20
3. Image Height = 480
4. Image Width = 480
5. Activation: 'softmax'
6. Loss:'categorical_crossentropy'
7. Optimizer: Adam
8. encoder_weights: imagenet

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202832763-1716f780-1faa-4fa3-b65c-3b9b4fd3f4ed.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202832798-193edb5d-8117-48ff-a437-c59067db2a7d.png)

**Notes:**  
Transfer learning has definitely improved the `val_iou_score` of the model, but the score fluctuates a lot.

---
### Attempt 5
Adjusting the learning rate in order to lower the fluctuation in `val_iou_score`.  
**Parameters Updated:**  
1. Learning Rate = 5e-5
2. Epochs = 15

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202862099-e1041219-a2e1-47cf-b622-43d68490fdc8.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202862053-05dfbd37-c9ac-4a2e-b110-3e4c7ed1bc8e.png)

**Notes:**
The model's `val_iou_score` seems to come down quickly after reaching a large value. This could be because we are training the model with too many images in each epoch.

---
### Attempt 6
Adjusting the batch size to 16 to reduce overfitting.  
**Parameters Updated:**  
1. Batches = 16

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202876509-1d945b85-d126-4d2f-bc31-32dcbafca36a.png)



**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202876519-835792f7-17e3-45de-a7b0-6867690a6b9f.png)

**Notes:**
Overfitting seems to have been reduced, but the `val_iou_score` of the model fluctuates a lot. This may be because the optimizer is not controlled by proper parameters. 

---
### Attempt 7
Changing the optimizer to RMSprop to try to control the fluctuations in the model's `val_iou_score`. 
**Parameters Updated:**  
1. Optimizer = tf.keras.optimizers.RMSprop(lr)

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202887206-a5e8db1f-271d-41d9-9f22-3bed4cec3aef.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202887207-a79c7831-30b7-4e24-ab69-97511c71916b.png)

**Notes:**
The model's `val_iou_score` seems to get stable at 0.939 with higher epochs.

---
### Attempt 8
Trying to decrease the number of epochs to check if model stabilizes at 0.939  `val_iou_socre`.  
**Parameters Updated:**  
1. Epochs = 10
**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202913283-c922a092-797b-479a-963b-4cbc1c19fb46.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202913307-dc19fdaa-5a37-4a6b-85d0-c778e6f2bb50.png)

**Notes:**
The model's `val_iou_score` is stable even in lower epochs.

# Final Conclusion  
From this experiment we can conclude that by changing the following parameters, we can develop a segmentation model for lunar surface images with a `val_iou_score` of about 0.939:
1. Image Height: 480
2. Image Width: 480
3. Epochs: 10 / 15 / 20
4. Batch Size: 16
5. Learning Rate: 5e-5
6. Incorporating Trasfer learning with VGG16 Pretrained model.
7. Activation: 'softmax'
8. Loss:'categorical_crossentropy'
9. Optimizer: Root Mean Squared Propogation
10. encoder_weights: imagenet
