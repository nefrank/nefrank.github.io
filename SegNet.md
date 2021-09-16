# 2D U-Net for Mammogram Segmentation
 
## Objective
The goal of this project is to develop a computer vision system to perform segmentation of the pectoral muscle in mammograms. A mammogram is an X-ray image of the breast, and can be segmented into different anatomical regions depending on the type of tissue present. Segmenting the locstion of each type of tissue, is both relevant for radiologists as well as computer aided diagnosis (CAD) systems. With CAD systems, a main preprocessing technique is defining the region(s) of interest. In this way, CAD systems may also benefit from the information gained by the segmentation of the pectoral muscle.

## Dataset
Two publicly available datasets were used for this project: <a href="https://wiki.cancerimagingarchive.net/display/Public/CBIS-DDSM">DDSM</a> and <a href="https://www.repository.cam.ac.uk/handle/1810/250394">MIAS</a>. Both datasets are comprised of scanned film mamography images. Due to the scans, the images contain noise and have numerous artifacts of different types, which are handled through pre-processing steps. The DDSM dataset contains images of both mediolateral oblique (MLO) and craniocaudal (CC) views, MIAS only contain MLO images. For this project only the MLO views were used as the CC view does not contain any pectoral tissue. 

![mdb009](https://user-images.githubusercontent.com/72168799/133535367-b2590f9c-3247-4bfa-82fd-5ee4b7a9693b.png)
![mdb009](https://user-images.githubusercontent.com/72168799/133535376-c0554256-dbd0-4d11-b0a4-94ef3cca9fbb.png)

In this image, we can observe the difference after the pre-processing steps have been applied to the raw mammogram to remove noise and artifacts.


## Model
The model used for this project is a modified <a href="https://arxiv.org/ftp/arxiv/papers/2011/2011.01118.pdf">U-Net</a> using depthwise seperable convolutions, as introduced with <a href="https://arxiv.org/pdf/1610.02357.pdf">Xception</a>. The input to the model is a 224x224 grayscale image, and the model outputs a 224x224 segmentation map with pixel-wise classification based on whether that pixel is predicted to be background, breast tissue, or pectoral muscle. 

![image](https://user-images.githubusercontent.com/72168799/133542094-c4fd7a42-d087-4bef-bb9c-84e3aba4345c.png)

The notebook with the code can be found <a href="https://nefrank.github.io/Segmentation_DDSM.html">here</a>.

## Demo

Here we can see an animation showing the model's prediction for a single input improving over each epoch of training.
![Seg](https://user-images.githubusercontent.com/72168799/133529846-4bc793a7-6533-417e-8c41-c70365e30c9a.gif)

The results of the model on some test images are seen below:
![p1](https://user-images.githubusercontent.com/72168799/133529946-aa16b455-6614-4933-ad65-443f1fa9e1bd.png)
![p2](https://user-images.githubusercontent.com/72168799/133529976-eb0a6ef9-4ed4-4b9d-8c3a-dc9681024e5c.png)
![p3](https://user-images.githubusercontent.com/72168799/133529981-92dd9e85-5280-41cc-be47-e5f57430a016.png)
![p4](https://user-images.githubusercontent.com/72168799/133529982-b477507c-afd5-4c3a-9db2-66f30f3d091c.png)
![p5](https://user-images.githubusercontent.com/72168799/133529987-2f4215c4-554f-46d2-9118-c7afa15c4557.png)
