# Ori-YOLO: Detection of Astronaut Body Parts on the Space Station Based on Orientation-invariant Convolution

This is the official implementation of "Ori-YOLO: Detection of Astronaut Body Parts on the Space Station Based on Orientation-invariant Convolution" on PyTorch platform.

## Demo

<table> 
  <tr> 
    <td>
      <img src="https://github.com/saber778899/Ori-YOLO/blob/main/demos/demo2.jpg">
    </td> 
    <td>
      <img src="https://github.com/saber778899/Ori-YOLO/blob/main/demos/demo1.jpg">
    </td> 
  </tr> 
</table>

<table> 
  <tr> 
    <td>
      <img src="https://github.com/saber778899/Ori-YOLO/blob/main/demos/demo3.jpg">
    </td> 
    <td>
      <img src="https://github.com/saber778899/Ori-YOLO/blob/main/demos/demo4.jpg">
    </td> 
  </tr> 
</table>


## Illustrations

![image](https://github.com/saber778899/Ori-YOLO/blob/main/test_img/Ori-YOLO.png)

## Installation

```python
$ git clone https://github.com/saber778899/Ori-YOLO.git
$ pip install -r requirements.txt

# Codes are only evaluated on GTX3090
$ pip3 install torch==1.10.0+cu111 torchvision==0.11.1+cu111 torchaudio==0.10.0+cu111 \
  -f https://download.pytorch.org/whl/cu111/torch_stable.html
```

## Datasets

* [Download address for the complete dataset and annotations: ](https://drive.google.com/drive/folders/1wUf7o7ngUXhXjTdUNYcZ4VGuQaP8kzNb?usp=drive_link)

* [Download link for the pre-divided training and validation sets:](https://drive.google.com/drive/folders/1BCIJo1lzVhbxC4TYu6hrPRxHcPhKLde4?usp=drive_link)
  
## Training and Testing

Process official annotations of AstroBodyParts for our task by running 

```python
$ python tools/get_anno_HumanParts_v2.py
```

Preparing yolov5-style labels for body-parts

```python
$ python utils/labels.py --data data/JointBP_HumanParts.yaml
```

For the training stage, please run:

```python
$ python train.py --workers 15 --device 0,1,2,3 --data data/JointBP_HumanParts.yaml \
    --hyp data/hyp-p6.yaml --val-scales 1 --val-flips -1 
```

For the testing stage, please run:

```python
$ python demos/image.py
```


# Acknowledgement

Our code refers to the following repositories. We thank the authors for releasing the codes.

* [TPAMI 2024 (BPJDetPlus) - BPJDet: Extended Object Representation for Generic Body-Part Joint Detection](https://github.com/hnuzhy/BPJDet/tree/BPJDetPlus?tab=readme-ov-file)

* [TIP 2020 (Hier-RCNN & COCOHumanParts) - Hier R-CNN: Instance-level Human Parts Detection and A New Benchmark](https://github.com/soeaver/Hier-R-CNN)

* [YOLOv5 🚀 in PyTorch > ONNX > CoreML > TFLite](https://github.com/ultralytics/yolov5)
