# Seq_nms_YOLO

## Introduction

![](img/index.jpg) 

This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.

## Steps 📋

Using a linux terminal
1. Go to the folder where you are going to clone the repository

2. Clone the repository
  - `git clone https://github.com/lepori1/seq_nms_yolo.git`

3. Create a virtual environment with python 3.7 and activate it:
  - `conda create -y --prefix ./env python=3.7`
  - `source activate ./env`

4. Install dependencies in the following order:
  - `conda install -y -c conda-forge opencv`
  - `conda install -y -c anaconda cudatoolkit=10.1`
  - `conda install -y cudnn=7.6.4`
  - `conda install -y numpy`
  - `conda install -y -c menpo imageio`

5. Set the variable to include the lib/pkgconfig folder from your environment:
  - For example: `PKG_CONFIG_PATH=$PKG_CONFIG_PATH:./env/lib/pkgconfig`
  - `export PKG_CONFIG_PATH`

6. Make the project:
  - `make`

7. Download the `yolo.weights` and `tiny-yolo.weights`:
  - `wget https://pjreddie.com/media/files/yolo.weights`
  - `wget https://github.com/leetenki/YOLOtiny_v2_chainer/blob/master/tiny-yolo-voc.weights`

8. Rename this last file:
  - `mv tiny-yolo-voc.weights tiny-yolo.weights`

9. Copy a video file to the video (/seq_nms_yolo/video) folder, for example, `input.mp4`.

10. Go to the video folder and run `video2img.py` and `get_pkllist.py`:
  - `cd video`
  - `python video2img.py -i videoname.videotype` replacing videoname.videotype for your video name and extension.
  - `python get_pkllist.py`

11. Install some final dependencies:
  - `conda install -y matplotlib`
  - `conda install -y -c anaconda scipy`
  - `conda install -y -c conda-forge tensorflow`
  - `pip install tensorflow-object-detection-api`

12. Return to root folder and copy `libdarknet.so` and `libdarknet.a` to env/lib:
  - `cd ..`
  - `cp libdarknet.so env/lib/`
  - `cp libdarknet.a env/lib/`
 
13. Run `yolo_seqnms.py` to generate output images in `video/output`:
  - `python yolo_seqnms.py`

14. If you want to reconstruct a video from these output images, you can go to the video folder and run `img2video.py`:
  - `cd video`
  - `python img2video.py -i output`

And you will see detection results in `video/output`


## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).

Main reference: https://github.com/melodiepupu/seq_nms_yolo.
