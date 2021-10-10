# object-detection

This repository contains documentation and code for object detection. The primary software package we use is called [darknet_ros](https://github.com/leggedrobotics/darknet_ros), running on Ubuntu 18.04 with ROS Melodic.

## Contributing to this repository

Never push your changes directly to the `main` branch! Create a branch for each high level change you are working on (`documentation` or `new-cv-algorithm` or something). When you've finished working on and testing your code, open a merge request in Github, and describe the changes you've made and what needs to be reviewed by other team members. Don't forget to merge in any new changes from `main` into your branch. Once a couple of team members have reviewed and approved your changes, those changes will be merged into `main`! See [this link](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) for a quick guide on working with different git branches.

## Installation

Follow the installation instructions for darknet_ros on the README. Make sure CUDA and OpenCV are installed. For CUDA, make sure you follow all the installation steps, including the mandatory post-installation steps. I've had some trouble with OpenCV 4, so I usually just install OpenCV 3.4.2 using [this script](https://github.com/milq/milq/blob/master/scripts/bash/install-opencv.sh). Download the script, change the `OPENCV_VERSION` to `3.4.2` and run the following command.

```
bash install-opencv.sh
```

You will also need to install CUDA following [these instructions](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation). Don't forget to follow the mandatory post-installation instructions!

If you run into any Nvidia or CUDA issues, try updating the graphics card drivers.
```
sudo apt update
sudo apt install nvidia-driver-{latest version number}
```
You'll need to reboot the computer after installing new graphics card drivers.

## Usage

See the README in `darknet_ros`, but the basic gist is to change the subscribed topic in `darknet_ros/config/ros.yaml` to the topic that the camera node is publishing to, and change the `cfg` file to point to the right weights file.

## Training new objects

Use [DarkMark](https://github.com/stephanecharette/DarkMark) (need to have darknet installed) or [labelImg](https://github.com/tzutalin/labelImg) (works on any OS) to annotate images, then follow the steps [here](https://github.com/alexeyAB/darknet#how-to-train-to-detect-your-custom-objects) to start the training. We'll most likely be using `yolo-v3-tiny`, so make sure you use the right starting weights and cfg files. Can be done with the `darknet` submodule within the `darknet_ros` package. 

## Roadmap

idk...