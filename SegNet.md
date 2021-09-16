# 2D U-Net for Mammogram Segmentation
 
## Objective
The goal of this project is to develop a ship detection system using on-shore video recordings. The overall scope includes detection of maritime objects in each frame (boats, buoys, floating objects, etc.), classification of these objects, and tracking the objects throughout the frames of the video. The model's current capability is to detect and track maritime objects without classification. 

## Dataset
The dataset used is the Singapore Maritime Dataset (<a href="https://sites.google.com/site/dilipprasad/home/singapore-maritime-dataset">Link</a>). The dataset is comprised of high-definition videos (1080X1920 pixels). It is divided into two parts, on-shore videos, and on-board videos. The on-shore dataset is acquired by a fixed mounted camera on land, whereas the on-board dataset has the camera placed on-board a moving vessel. The videos were filmed from different locations and include varying scenes. There is also a Near Infrared (NIR) video dataset captured with a Near-IR Bandpass filter. The dataset contains schenes with varying environmental conditions, such as rain and haze, as well as different times of the day.

The dataset was divided into Training / Testing splits according to this paper. (<a href="https://openaccess.thecvf.com/content_CVPRW_2019/papers/PBVS/Moosbauer_A_Benchmark_for_Deep_Learning_Based_Object_Detection_in_Maritime_CVPRW_2019_paper.pdf">A Benchmark for Deep Learning Based
Object Detection in Maritime Environments</a>)

## Model
To train the object detection system, a YOLOv4 model was created using Darknet (<a href="https://github.com/AlexeyAB/darknet">Link</a>) to obtain a set of weights. For speed considerations when running the model on videos, we decided to use the YOLOv4-tiny model, trading off performance for speed.

The weights from the first model are then used with DeepSORT to track the detected objects between frames in the video. 

## Further Steps

- Look into using more data:
  - <a href="http://www.diag.uniroma1.it//~labrococo/MAR/">MAR-DCT</a>
  - <a href="https://www.vicos.si/resources/modd/MODD">MODD</a>
  - <a href="https://chriskanan.com/datasets/">VAIS</a>
  - <a href="https://github.com/avaapm/marveldataset2016">MARVEL</a> 
  - <a href="http://www.lmars.whu.edu.cn/prof_web/shaozhenfeng/datasets/SeaShips%287000%29.zip">SeaShips</a> 
  - <a href="http://www.cvg.reading.ac.uk/PETS2016/a.html">PETS</a> 
- Using an ensemble method to combine the performance of multiple models, each trained with different data augmentation types
- Look into using more current/up-to-date object detection models (YOLOv5, PP-YOLO, RCNNs, etc.)

## Demo

![Seg](https://user-images.githubusercontent.com/72168799/133529846-4bc793a7-6533-417e-8c41-c70365e30c9a.gif)

![p1](https://user-images.githubusercontent.com/72168799/133529946-aa16b455-6614-4933-ad65-443f1fa9e1bd.png)
![p2](https://user-images.githubusercontent.com/72168799/133529976-eb0a6ef9-4ed4-4b9d-8c3a-dc9681024e5c.png)
![p3](https://user-images.githubusercontent.com/72168799/133529981-92dd9e85-5280-41cc-be47-e5f57430a016.png)
![p4](https://user-images.githubusercontent.com/72168799/133529982-b477507c-afd5-4c3a-9db2-66f30f3d091c.png)
![p5](https://user-images.githubusercontent.com/72168799/133529987-2f4215c4-554f-46d2-9118-c7afa15c4557.png)
