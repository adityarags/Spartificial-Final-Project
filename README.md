<p align="center">
<img src="https://discordhome.com/user_upload/backgrounds/7864background.jpg" style="height:200px">
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
![image](https://user-images.githubusercontent.com/59119736/202582117-7b8d27c7-7180-421f-b5e4-66e204ec2596.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202582976-a89a60c6-5c1e-4087-9c9a-953ccb265f03.png)

---

### Attempt 2
Since the number of epochs is too low, tried increasing the number of epochs to 10 to check for improvement.

**Parameters Updated:**  
1. Epochs = 10

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202806467-7d26d6b9-99de-44f4-a34c-513b7b438990.png)


**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202806498-81efd489-dacc-4044-ac82-c9a1af9cde4b.png)



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


---
### Attempt 4
Transfer learning using VGG16 model.  
**Parameters Updated:**  
1. Batch Size = 8
2. Epochs = 20

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202832763-1716f780-1faa-4fa3-b65c-3b9b4fd3f4ed.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202832798-193edb5d-8117-48ff-a437-c59067db2a7d.png)


---
### Attempt 5
Adjusting the learning rate in order to lower the fluctuation in `val_iou_score`.
**Parameters Updated:**  
1. Learning Rate = 1e-5
2. Epochs = 15

**Model History:**  
![image](https://user-images.githubusercontent.com/59119736/202832763-1716f780-1faa-4fa3-b65c-3b9b4fd3f4ed.png)

**`val_iou_score` Trend:**  
![download](https://user-images.githubusercontent.com/59119736/202832798-193edb5d-8117-48ff-a437-c59067db2a7d.png)



