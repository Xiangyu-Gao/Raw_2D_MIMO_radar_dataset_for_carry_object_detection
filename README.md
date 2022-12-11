# Raw Radar ADC Dataset for Carry Object Detection

Automotive Radar Object Recognition in the Bird-eye View Using Range-Velocity-Angle (RVA) Heatmap Sequences
of 2D-MIMO MMWave Radar

<p align="center"> <img src='docs/tease.png' align="center" height="300px"> </p>

## Citations

> [**Learning to Detect Open Carry and Concealed Object With 77 GHz Radar**](https://ieeexplore.ieee.org/abstract/document/9765320),            
> Xiangyu Gao, Hui Liu, Sumit Roy, Guanbin Xing, Ali Alansari, and Youchen Luo, <br/>
> *arXiv technical report* ([arXiv 2111.00551](https://arxiv.org/abs/2111.00551.pdf))  
    
    @ARTICLE{9765320,  author={Gao, Xiangyu and Liu, Hui and Roy, Sumit and Xing, Guanbin and Alansari, 
        Ali and Luo, Youchen},  journal={IEEE Journal of Selected Topics in Signal Processing},   
        title={Learning to Detect Open Carry and Concealed Object With 77 GHz Radar},   
        year={2022},  volume={16},  number={4},  pages={791-803},  doi={10.1109/JSTSP.2022.3171168}}

> [**RAW ADC DATA OF 2D-MIMO MMWAVE RADAR FOR CARRY OBJECT DETECTION**](https://ieee-dataport.org/documents/raw-adc-data-2d-mimo-mmwave-radar-carry-object-detection),            
> Xiangyu Gao, Sumit Roy, Hui Liu, Youchen Luo, Guanbin Xing, <br/>
> *IEEE Dataport*

    @data{begn-ye78-22, doi = {10.21227/begn-ye78}, url = {https://dx.doi.org/10.21227/begn-ye78},
        author = {Gao, Xiangyu and Roy, Sumit and Liu, Hui and Luo, Youchen and Xing, Guanbin},
        publisher = {IEEE Dataport},
        title = {Raw ADC Data of 2D-MIMO MMWave radar for Carry Object Detection},
        year = {2022} }

## Update
***(Dec. 11, 2022) Initial release of dataset and tools.***

## Contact
Any questions or suggestions are welcome! 

Xiangyu Gao [xygao@uw.edu](mailto:xygao@uw.edu) 

## Introduction
In this dataset, we provided the raw *analog-to-digital-converter* (ADC) data of a 77GHz mmwave radar for the carry object detection scenario. The overall dataset contains approximately **3000 frames** of *radar data* as well as the synchronized *camera images* and *labels*. For each radar frame, its raw data has 4 dimension: samples (fast time), chirps (slow time), transmitters, receivers. The experiment radar was assembled from the *TI cascaded-chip TIDEP-01012* board, with *12 transmit* antennas and *16 receive* antennas. , it can form a large *2D-MIMO virtual array with 192 elements*, resulting in fine azimuth resolution (1.35°) and additional elevation resolution (19°). Other parameter configurations of radar were described in detail below. 

The data collection was done in the building lobby and laboratory room with the focus of capturing the data for *three main objects carried by individual: phones, laptops, knives (include metallic butter knives and cutting knives)*. Each object can either be *openly carried* or be *concealed*. A single data collection run consisted of a subject holding one of the three objects listed above, and walking at a normal pace on a random path for 10 seconds in front of the testbed. To add variability to the data, the walking pattern of subjects was always randomize and the location of where the objects were concealed or how the objects were openly carried was always changed. 

## Download

Download dataset from the google drive link:
```
https://drive.google.com/file/d/1IcrY3Hm-o9fxUwlZ-j2rLgLuAn0XQSKl/view?usp=share_link
``` 
Or from IEEE Dataport:
```
https://ieee-dataport.org/documents/raw-adc-data-2d-mimo-mmwave-radar-carry-object-detection
```

## Data Format
The dataset contains the raw ADC radar data in **.mat* format, camera images in **.jpg* format, and labels in **.txt* format.

### Radar ADC Data

*  For each radar frame, its raw data has 4 dimension: samples (256), chirps (61), receivers (16), transmitters (12). All transmitters were arranged with time-division multiplexing, i.e., send chirp signal one by one.

The example frame structure is shown as below:
<p align="center"> <img src='docs/cascaded_frame_structure.png' align="center" height="300px"> </p>

* 2D-MIMO antenna array

The example frame structure is shown as below:
<p align="center"> <img src='docs/antenna%20array.png' align="center" height="300px"> </p>

* All radar configurations and algorithm configurations are included in [config](config.py).

### Camera Image

### Labels

## Dataset Tools

### Software Requirement and Installation

Python 3.6, pytorch-1.5.1 (please refer to [INSTALL](requirements.txt) to set up libraries.)

## 3D Slicing of Range-Velocity-Angle Data
For convenience, in the sample codes we use the raw ADC data of each frame as input and perform the [Range, Velocity, and Angle FFT](https://github.com/Xiangyu-Gao/mmWave-radar-signal-processing-and-microDoppler-classification) during the process of slicing. Run following codes for 3D slicing.
    
    python slice3d.py
    

The slicing results are the RA slices, RV slices, and VA slices as shown in below figure.
<p align="center"> <img src='docs/slice_viz.png' align="center" height="230px"> </p>



## License

This tool is release under MIT license (see [LICENSE](LICENSE)).

## Acknowledgement
This project is not possible without multiple great opensourced codebases. We list some notable examples below.  

* [microDoppler](https://github.com/Xiangyu-Gao/mmWave-radar-signal-processing-and-microDoppler-classification)
* [rodnet](https://github.com/yizhou-wang/RODNet)
