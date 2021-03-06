# jetson_object_detection

How to install YOLO V3?
Before showing the steps to the installation, I want to clarify what is Yolo and what is a Deep Neural Network.

YOLO is an Object Detection algorythm, and it’s the acronym of (You Only Look Once). An object detection algorythm need a DNN (Deep Neural Network) framework to run.

DARKNET is the DNN that was developed to run Yolo. And we’re going to see today how to install Darknet.

Let’s start with the installation.

Update the libraries
sudo apt-get update
Export Cuda path
export PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
Download Darknet and Yolo
git clone https://github.com/AlexeyAB/darknet
cd darknet
wget https://pjreddie.com/media/files/yolov3.weights
wget https://pjreddie.com/media/files/yolov3-tiny.weights
Enable the GPU
We need to Edit the Makefile to enable the GPU, Cuda and Opencv. Let’s edit the Makefile by typing.
sudo vi Makefile
Set the values:
GPU=1
CUDNN=1
OPENCV=1
and the rest leave it as it is.
Compile the Darknet
make
The installation is now completed.

How to run YOLO V3?
You can run Yolo from the Linux terminal.
Once you open the terminal you need first to access the Darknet folder. So just type:

cd darknet
Then you can choose one of the following line, depending of the detection you want to perform.

Image detection:
Edit “dog.jpg” with the path of your image.

./darknet detector test cfg/coco.data yolov3.cfg yolov3.weights -ext_output dog.jpg
Detection from Webcam:
The 0 at the end of the line is the index of the Webcam. So if you have more webcams, you can change the index (with 1, 2, and so on) to use a different webcam.

./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights -c 0
Detection from a Videofile:
Edit “test.mp4” with the path of your videofile.

./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights -ext_output test.mp4
