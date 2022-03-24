# DETR LUNA
Fork of DETR using LUNA16 lung cancer dataset

## Configuring the environment
1. Download the images and annotations from [this link](https://drive.google.com/drive/folders/1OV2L7uz6oF4ac_XOd5iDsUWiG1eVaSN1?usp=sharing) and extract them to the `dataset/` directory, in the following structure:
```shell
luna_images/
luna_images_seg/
test.json
test_seg.json
train.json
train_seg.json
```

2. Download the COCO images [pretrained weights](https://dl.fbaipublicfiles.com/detr/detr-r50-e632da11.pth) to `detr/weights/`.


3. Create a conda environment using python 3.7 and install the requirements:
```console
conda create -n DETR python=3.7
conda activate DETR
pip install -r detr/requirements.txt
```

## Training the model
Run the `main.py` code from within the detr directory:
```console
python main.py --device cuda --dataset_file luna --data_path ../dataset/ --output_dir output --resume weights/detr-r50-e632da11.pth --batch_size 16 --epochs 20
```

We start the training using the pre-trained weights given in the repo. After training our model, we can continue further epochs refering to our own checkpoint file as `--resume output/checkpoint.pth`.
