# DETR LUNA
Fork of Facebook's [DETR](https://github.com/facebookresearch/detr/) Object Detection with Transformers model using the [LUNA16](https://luna16.grand-challenge.org/) lung cancer dataset.

## Description
This fork uses 2D CT scan images extracted from the LUNA16 lung cancer dataset. The original LUNA16 dataset contains 3D CT scan objects. For this work, these objects were converted to 2D 512x512 images. Some data-augmentation techniques were used, giving us around 4,000 images with one of more lung nodules.

## Configuring the environment
1. Download the images and annotations from [this link](https://drive.google.com/drive/folders/1JwuaIvH2c4u9YsiXy4MfOPAL_bK6JhWU?usp=sharing) and extract them to the `dataset/` directory, in the following structure:
```shell
luna_images_test/
luna_images_train/
luna_images_seg_test/
luna_images_seg_train/
test.json
test_seg.json
train.json
train_seg.json
```

2. Download the COCO images [pretrained weights](https://dl.fbaipublicfiles.com/detr/detr-r50-dc5-f0fb7ef5.pth) to `detr/weights/`.


3. Create a conda environment using python 3.7 and install the requirements:
```console
conda create -n DETR python=3.7
conda activate DETR
pip install -r detr/requirements.txt
```

## Training the model
Run the `main.py` code from within the detr directory:
```console
python main.py --device cuda --dataset_file luna --data_path ../dataset/ --output_dir output_2/ --resume weights/detr-r50-dc5-f0fb7ef5.pth --batch_size 8 --lr_drop 1000 --num_queries 10 --epochs 600
```

We start the training using the pre-trained weights given in the repo. After training our model, we can continue further epochs refering to our own checkpoint file as `--resume output/checkpoint.pth`.
