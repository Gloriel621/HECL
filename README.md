# High-Fidelity Face Age Transformation via Hierarchical Encoding and Contrastive Learning (HECL)

This README provides instructions for setting up, training, and testing the High-Fidelity Face Age Transformation via Hierarchical Encoding and Contrastive Learning (HECL), a state-of-the-art model for age transformation in images. The guide assumes operation on a Linux environment and recommends the use of a GPU for execution.

## Environment Setup, Training, and Inference Instructions

### Environment Setup

1. **Create a Conda Environment:**
   Use the `environment.yml` file provided in the repository to create a conda environment by running the following command:
   ```bash
   conda env create -f environment.yml

## Data Preparation

1. **Download Datasets:**
   Ensure to download the following datasets and place them in the directory where HECL is located(not inside the HECL directory):
   - FFHQ-Aging-Dataset: [GitHub Link](https://github.com/royorel/FFHQ-Aging-Dataset)
   - Cross-Age-Face Dataset: [GitHub Link](https://github.com/AvLab-CV/AgeTransGAN?tab=readme-ov-file#cross-age-face-dataset)
   - All-Age-Faces-Dataset: [Google Drive Link](https://drive.google.com/drive/folders/17l3dqmv7SjmQ1SFiP0aIvWbF2KNcFyuK?usp=sharing)

   Unzip All-Ages-Faces-Dataset/results/cropped_imgs.zip.

2. **Preprocess the Datasets:**
   Execute the Python scripts below to preprocess the datasets. This step is crucial for preparing the data for training:
   ```bash
   python3 datasets/create_dataset.py
   python3 datasets/create_dataset_caf.py
   python3 datasets/create_dataset_allagesdataset.py
   ```
   Alternatively, you can use the provided shell script to automate this process:
   ```bash
   sh create_dataset.sh
   ```

### Training

First, turn on `visdom` on another terminal. This will open visdom server on `localhost:8097` by default.
```bash
visdom
```

To train the model, modify the `--dataroot`, `--name` parameters in `train.sh` script according to your needs, then run:
```bash
sh train.sh
```

### Pretrained Models

Download checkpoints.zip [Google Drive Link](https://drive.google.com/file/d/1-yFO6AAyEfQgpD9E3BQhJSf01G0cox5k/view?usp=sharing), unzip and put the checkpoints folder in the HECL directory.
The inference can be done using pretrained models.

### Inference

For inference, modify the `--dataroot`, `--name`, `--which_epoch`, and `--checkpoint_dir` parameters in `test.sh` script according to your needs, then run:
```bash
sh test.sh
```

### Notes

Ensure that you have correctly placed the datasets in the required directory before preprocessing.

Modify the script parameters carefully to match your local setup for successful training and testing.
