# SMPLX (Skinned Multi-person Linear Model Expressive)

## Description
Here are the steps to implement [SMPL-X](https://smpl-x.is.tue.mpg.de/), by which 3D model of human body pose, hand pose and facial expression can be computed from a single image. The code can be found at the [GitHub Repo](https://github.com/vchoutas/smplify-x#expressive-body-capture-3d-hands-face-and-body-from-a-single-image).

## Steps to set up system
This code is tested on Ubuntu 18.04 with CUDA 10.2, CUDNN 7.6.5, pytorch 1.1.0 and python 3.6.
1. Download [CUDA Toolikt](https://developer.nvidia.com/cuda-downloads) and [cuDNN](https://developer.nvidia.com/cudnn)
   * [cuDNN Installation Guide](https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html) can be helpful in setting up CUDA and cuDNN
2. Install [PyTorch](https://pytorch.org/)
3. Follow installation instructions for each of the followings:
    * [SMPL-X](https://github.com/vchoutas/smplx)
    * [VPoser](https://github.com/nghorbani/human_body_prior)
    * [Homogenus](https://github.com/nghorbani/homogenus)
    * [Pytorch Mesh Intersection](https://github.com/vchoutas/torch-mesh-isect)




## OpenPose Installation

### Pre-requisites
1. Clone [Github repo](https://github.com/CMU-Perceptual-Computing-Lab/openpose) 
```sh
$ git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose
```
2. Uninstall CMake GUI
```sh
$ sudo apt purge cmake-qt-gui
```
3. Reinstall CMake GUI
```sh
$ sudo apt-get install qtbase5-dev
```
4. Download latest release of CMake for Linux from [CMake Website](https://cmake.org/download/)
- Run `./configure --qt-gui`
- If errors occur at runtime for OpenSSL, run `sudo apt-get install libssl-dev`
- Run ``` ./bootstrap && make -j `nproc` && sudo make install -j `nproc` ```
5. Install Caffe
- Go to Openpose Directory which was clonned. 
- Run `sudo bash ./scripts/ubuntu/install_deps.sh`
6. Install OpenCV
```sh
$ sudo apt-get install libopencv-dev
```
### OpenPose Configuration

1. Open CMake GUI 
2. Select OpenPose directory as source directory and an empty directory (**e.g. build**) to build binaries.
3. Press `configure` and keep the generator in **Unix Make** file
4. If there occurs any caffe related error, go to __3rdparty__ directory and clone [this](https://github.com/CMU-Perceptual-Computing-Lab/caffe.git) repo and configure again in Cmake GUI.
OR run following command
```sh
$ git submodule update --init --recursive --remote
```
5. After successful configuration, press `Generate` button and Build Openpose

### Openpose Building
```
$ cd build
$ make -j`nproc`
```

### Run Openpose on images
Go to Openpose directory and run following
```
$ build/examples/openpose/openpose.bin --image_dir IMAGEDIRECTORY  --face --hand --write_json OUTPUTDIRECTORY --write_images OUTPUTDIRECTORY
```
