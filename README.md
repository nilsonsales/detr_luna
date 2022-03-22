# DETR LUNA
Fork of DETR using LUNA16 lung cancer dataset

# Training the model
To run the model, put the images and annotations in COCO format in the `dataset/` folder in the following structure:
```shell
luna_images/
luna_images_seg/
test.json
test_seg.json
train.json
train_seg.json
```

Create a conda environment using python 3.7 and install the requirements:
```console
conda create -n DETR python=3.7
conda activate DETR
pip install -r detr/requirements.txt
```

Run the `main.py` code from within the detr directory:
```console
python main.py --device cuda --dataset_file luna --data_path ../dataset/ --output_dir output --resume output/checkpoint.pth --batch_size 16 --epochs 20
```
