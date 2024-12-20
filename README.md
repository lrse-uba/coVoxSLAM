### Disclaimer
🚧 **This project is currently under revision. The code will be available soon!** 🚧

## coVoxSLAM

GPU-accelerated volumetric SLAM system for globally consistent maps for small and large-scale environments.

<a href="https://youtu.be/hGp-w6n05Tk" target="_blank"><img src="https://github.com/EmiHoess/coVoxSLAM/blob/main/docs/images/submission_image.png?raw=true" 
alt="coVoxSLAM ICRA 25 - Submission Video" width="854" height="480" border="10" /></a>

## Table of Contents
- [coVoxSLAM](#covoxslam)
- [Table of Contents](#table-of-contents)
- [Get Started ](#get-started-)
- [Compilers ](#compilers-)
- [Dependencies ](#dependencies-)
- [Build](#build)
- [Paper](#paper)

![pipeline](docs/diagrams/pipeline.png)
The architecture of coVoxSLAM is shown above. The system consists of a frontend and backend. The frontend is responsible for integrating the incoming sensor data into a TSDF volume to include or update the voxels that build the TSDF maps and propagate updated voxels from the TSDF to the ESDF submaps. The created voxels are grouped in fixed-size blocks, which in turn, are indexed using an appropriately designed hash table. The backend is responsible for estimating the most likely submap collection alignment by minimizing the total error of the three pose graph constraints: odometry, loop closure and submap registration.

## Get Started <a id='getstarted'></a>

coVoxSLAM includes two components: a CPU version and a GPU version. Each can be built and run independently using the provided flags (--cpu for the CPU version and --gpu for the GPU version). By default, the build process will include both versions.


## Compilers <a id='compilers'></a>

To build coVoxSLAM you need a compiler capable of C++20. It has been tested on:

    GCC 11 and above on Linux
    Clang 15 and above on Linux
    MSVC 2019 and above on Windows

## Dependencies <a id='deps'></a>

Dependencies are managed by CMake

- Ceres (only for the CPU version)
- CUDA 12 (only for the GPU version)

## Build

```
mkdir build
cd build
cmake .
```

## Paper

Pre-print available

* Emiliano Höss, Pablo De Cristóforis. "**coVoxSLAM: GPU-Accelerated globally consistent dense SLAM**".
arXiv preprint arXiv:2410.21149. \[ [ArXiv](https://arxiv.org/abs/2410.21149) \]

```bibtex
@article{hoss2024covoxslam,
  title={coVoxSLAM: GPU Accelerated Globally Consistent Dense SLAM},
  author={H{\"o}ss, Emiliano and De Crist{\'o}foris, Pablo},
  journal={arXiv preprint arXiv:2410.21149},
  year={2024}
}
```