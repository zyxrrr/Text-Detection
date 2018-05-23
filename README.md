# [ICPR MTWI 2018 CHALLENGE 2 Text Detection of Web Images](https://tianchi.aliyun.com/competition/introduction.htm?spm=5176.100066.0.0.6acdd780mq0dGw&raceId=231651)

# Fork from [TextBoxes++](https://github.com/MhLiao/TextBoxes_plusplus)

TextBoxes++ is a unified framework for oriented scene text detection with a single network. For more details, please refer to our [arXiv paper](https://arxiv.org/abs/1801.02765). 

### Contents
1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Models](#models)
4. [Demo](#demo)
5. [Train](#train)
6. [Changed](#changed)

### Requirements
    g++-5; cuda8.0; cudnn V5.1 (cudnn 6 and cudnn 7 may fail); opencv3.0
  
Please refer to [Caffe Installation](http://caffe.berkeleyvision.org/install_apt.html) to ensure other dependencies;

### Installation

compile TextBoxes++ (This is a modified version of caffe so you do not need to install the official caffe)
  ```Shell
  # Modify Makefile.config according to your Caffe installation.
  cp Makefile.config.example Makefile.config
  make -j8
  # Make sure to include $CAFFE_ROOT/python to your PYTHONPATH.
  make py
  ```

  
### Models

model trained on ICPR MTWI 2018 text (used for testing):
[BaiduYun](https://pan.baidu.com/s/1tlF3zjnEkA8dk7SoNpvv2A)
    
    Please place the above models in "./models/"
    
    

### Demo 
Download the ICPR MTWI 2018 model and place it in "./models/"
  ```Shell
  python examples/text/demo.py
  ```
The detection results and recognition results are in "./demo_images"

### Train

#### Create lmdb data

1. convert ground truth into "xml" form: [example.xml](./data/example.xml)
    
2. create train/test lists (train.txt / test.txt) in "./data/text/" with the following form: 

        path_to_example1.jpg path_to_example1.xml
        path_to_example2.jpg path_to_example2.xml
            
3. Run "./creat_data.sh"
    
#### Start training
    
    1. modify the lmdb path in modelConfig.py
    2. Run "python examples/text/train.py"

### Changed

1. add prior box on conv3_3
2. change aspect_ratios = [2,3,4,5,7]
3. change box size: 
[10, 30.0, 78.0, 126.0, 174.0, 222.0, 270.0]
[30, 78.0, 126.0, 174.0, 222.0, 270.0, 318.0]
