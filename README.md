
<a href="https://img.shields.io/badge/FHNW-Deep%20Learning-yellow"><img src="https://img.shields.io/badge/FHNW-Deep%20Learning-yellow" /></a>

# Semantic Segmentation of Brain Tumours

<img src="doc\brain_mris.png" width="600" align="center">


This repository implements two semantic segmentation models UNet-3 (3 skip-cons) and UNet-4 (4 skip cons). the models can be found in `./imgseg/networks.py`



## Documentation

The documentation of the whole procedure from start to finish is 
documented in the notebook `documentation.ipynb`.


## Models

The models can be downloaded from here: https://drive.google.com/drive/folders/1nm74FqZckW0pwa-L1O_SwnRV7-iAA-sR?usp=sharing

During the evaluation the segmentation model with the name `dice_unet4_50eps_16bs.pth` performed best and it is recommended to download this model for inference. The evaluation was made on certain patients from the used kaggle dataset for training. I can not guarantee that the model performs good on other images, which might origin from a different distribution.

- Unet with 4 skip connections
- Trained with normal Dice-Loss
- 50 epochs in total
- Batch size of 16
- Adam optimizer with additional step-wise learning rate scheduler

## Installation

## Manual

1. Clone project locally 
via SSH:
```bash
git clone git@github.com:SimonStaehli/image-segmentation.git
```
or via HTTPS:
```bash
git clone https://github.com/SimonStaehli/image-segmentation.git
```

2. Download models from Google Drive and add it to the folder `./models` here: https://drive.google.com/drive/folders/1nm74FqZckW0pwa-L1O_SwnRV7-iAA-sR?usp=sharing

3. Install required packages
```bash
pip install -r requirements.txt
```
Note: if there is a problem with the installation please refer to the official pytorch installation guide: https://pytorch.org/get-started/locally/

### With Docker
```bash
docker build . -f Dockerfile -t brain-mri-semantic-segmentation
```

```bash
docker run -it brain-mri-semantic-segmentation
```

## Run Locally

Requires all installation steps already made.

Following command will segment all images in the folder `image_in` and store the masks in the folder `image_out`.

```bash
python inference.py -i image_in -o image_out --overlay True
```


## References

Dataset used for training: https://www.kaggle.com/datasets/mateuszbuda/lgg-mri-segmentation 

Kaggle Notebook used for training: https://www.kaggle.com/code/simonstaehli/image-segmentation
