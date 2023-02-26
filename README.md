






##  YOLO Object Detection on images
<br>
<p align='center'>
<img src="https://editor.analyticsvidhya.com/uploads/1512812.png" width='70%' >
</p>
<br>

YOLO (You Only Look Once) is a state-of-the-art object detection algorithm that can detect objects in an image in real-time with high accuracy. OpenCV is an open-source computer vision library that provides a set of tools and algorithms for processing images and videos.
- Install OpenCV and the required dependencies.
- Download the YOLO pre-trained weights and configuration files.
- Load the YOLO network.
-  Load the input image.
- Preprocess the input image.
- Pass the input image through the YOLO network
- Postprocess the output

<br>

### Built With

![Python](https://img.shields.io/badge/Python%20-%2314354C.svg?style=for-the-badge&logo=python&logoColor=white)





  

![Github Pages](https://img.shields.io/badge/GitHub%20Pages-%23327FC7.svg?style=for-the-badge&logo=github&logoColor=white)


![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)


<br>

## Running this project

This is a  YOLO Object Detection on images using OpenCV and Python Project.

YOLO (You Only Look Once) is a state-of-the-art object detection algorithm that can detect objects in an image in real-time with high accuracy. OpenCV is an open-source computer vision library that provides a set of tools and algorithms for processing images and videos.



```
pip install virtualenv
```

Clone or download this repository and open it in your editor of choice. In a terminal (mac/linux) or windows terminal, run the following command in the base directory of this project

```
virtualenv venv
```

That will create a new folder `env` in your project directory. Next activate it with this command on mac/linux:

```
source venv/bin/active
```

Then install the project dependencies with

```
pip install -r requirements.txt
```

### 1.Install OpenCV and the required dependencies: 
You can install OpenCV and the required dependencies using pip by running the following command:


```
pip install opencv-python opencv-contrib-python

```
### 2.Download the YOLO pre-trained weights and configuration files:
You can download the YOLO pre-trained weights and configuration files from the official website 
```
https://pjreddie.com/darknet/yolo/
```

### 3.Load the YOLO network: 
In OpenCV, you can load the YOLO network using the  function. This function takes two arguments: the path to the weights file and the path to the configuration file. Here's an example:

```
yolo = cv2.dnn.readNet("yolov3.weights", "yolov3.cfg")
```

### 4.Preprocess the input image:
Before passing the image to the YOLO network, you need to preprocess it by resizing it to the input size of the network and normalizing its pixel values. Here's an example:
```
blob = cv2.dnn.blobFromImage(img, 0.00392, (416, 416), (0, 0, 0), True, crop=False)
```

### 4.1.Load the input image: 
You can load the input image using the cv2.imread() function. This function takes one argument: the path to the image file. Here's an example:
```
name = "traffic-jam-11065854.jpg"
img = cv2.imread(name)
height, width, channels = img.shape

```

### 5.Pass the input image through the YOLO network: 
You can pass the preprocessed image through the YOLO network using the net.forward() function. This function takes one argument: the name of the output layer of the network. Here's an example:
```
yolo.setInput(blob)
outputs = yolo.forward(output_layers)
```
### 6. Postprocess the output:
Once you have the output from the YOLO network, you need to postprocess it to get the bounding boxes and class labels of the detected objects. Here's an example:

```
class_ids = []
confidences = []
boxes = []
for output in outputs:
    for detection in output:
        scores = detection[5:]
        class_id = np.argmax(scores)
        confidence = scores[class_id]
        if confidence > 0.5:
            center_x = int(detection[0] * width)
            center_y = int(detection[1] * height)
            w = int(detection[2] * width)
            h = int(detection[3] * height)

            x = int(center_x - w / 2)
            y = int(center_y - h / 2)

            boxes.append([x, y, w, h])
            confidences.append(float(confidence))
            class_ids.append(class_id)

indexes = cv2.dnn.NMSBoxes(boxes, confidences, 0.5, 0.4)
for i in range(len(boxes)):
    if i in indexes:
        x, y, w, h = boxes[i]
        label = str(classes[class_ids[i]])
        cv2.rectangle(img, (x, y), (x + w, y + h), colorGreen, 3)
        cv2.putText(img, label, (x, y + 10), cv2.FONT_HERSHEY_PLAIN, 8, colorRed, 8)

```

<br>

## Screenshots



<table width="100%"> 
<tr>

<td width="50%">
<p align="center">
Light Mode
</p>
<img src="https://github.com/Jauharmuhammed/README-Template/blob/main/assets/light%20Mode.png">  
</td>
  <td width="50%">      
<p align="center">
Dark Mode
</p>
<img src="https://github.com/Jauharmuhammed/README-Template/blob/main/assets/dark-mode.png">
</td> 
</table>
<br/>

## Contact

<div align='left'>

<a href="https://linkedin.com/in/jauharmuhammed" target="_blank">
<img src="https://img.shields.io/badge/linkedin-%2300acee.svg?color=405DE6&style=for-the-badge&logo=linkedin&logoColor=white" alt=linkedin style="margin-bottom: 5px;"/>
</a>
	
<a href="https://twitter.com/jauharmuhammed_" target="_blank">
<img src="https://img.shields.io/badge/twitter-%2300acee.svg?color=1DA1F2&style=for-the-badge&logo=twitter&logoColor=white" alt=twitter style="margin-bottom: 5px;"/>
</a>
	
<a href="mailto:jauharmuhammedk@gmail.com" target="_blank">
<img src="https://img.shields.io/badge/gmail-%23EA4335.svg?style=for-the-badge&logo=gmail&logoColor=white" t=mail style="margin-bottom: 5px;" />
</a>
	
		
<a href="https://codepen.io/jauharmuhammed" target="_blank">
<img src="https://img.shields.io/badge/codepen-%23000000.svg?style=for-the-badge&logo=codepen&logoColor=white" t=mail style="margin-bottom: 5px;" />
</a>

</div>
