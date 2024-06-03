# TCNet: Continuous Sign Language Recognition from Trajectories and Correlated Regions
![flowchart](fig2.pdf)

This is the codebase for our paper [TCNet: Continuous Sign Language Recognition from Trajectories and Correlated Regions](https://arxiv.org/abs/2403.11818), the repository is based on [TLP](https://github.com/hulianyuyy/Temporal-Lift-Pooling) and [CorrNet](https://github.com/hulianyuyy/CorrNet), as we use the same feature extraction backbone, sequential modeling and classifier.

# Installation

The required packages are in the file `requirements.txt`, and you can run the following command to install the environment

```
conda create --name TCNet python=3.8 -y
conda activate TCNet

conda install pytorch==1.12.1 torchvision==0.13.1 torchaudio==0.12.1 -c pytorch

pip install -r requirements.txt
```

### Note:
- **The above commands are for reference only**, please configure your own environment according to your needs.
- We recommend installing **`PyTorch >= 1.12.0`**, which may greatly reduce the GPU memory usage.
- It is recommended to install **`timm == 0.4.12`**, because some of the APIs we use are deprecated in the latest version of timm.
- We have supported training with `PyTorch 2.0`, but it has not been fully tested.


# Data Preparation
We read and process the same way as [CorrNet]([https://github.com/MCG-NJU/VideoMAE/blob/main/DATASET.md](https://github.com/hulianyuyy/CorrNet)), but with a different convention for the format of the data list file. 


## PHOENIX2014
Run the following command to process the image sequence
```
cd ./preprocess
python data_preprocess.py --process-image --multiprocessing
```
## PHOENIX2014-T dataset
Run the following command to process the image sequence
```
cd ./preprocess
python data_preprocess-T.py --process-image --multiprocessing
```
## CSL dataset
Run the following command to process the image sequence
```
cd ./preprocess
python data_preprocess-CSL.py --process-image --multiprocessing
```
## CSL-Daily dataset
Run the following command to process the image sequence
```
cd ./preprocess
python data_preprocess-CSL-Daily.py --process-image --multiprocessing
```
# Training
Run the following command to train the model from scratch
```
python main.py --device your_device
```

