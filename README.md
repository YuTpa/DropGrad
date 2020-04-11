# Regularizing Meta-Learning via Gradient Dropout 
[[Paper]](https://arxiv.org/abs/2001.08735)

Pytorch implementation for our DropGrad approach. With the proposed regularization method, we can:

1. alleviate the overfitting problem in the exisiting gradient-based meta-learning models
2. improve the performance under **cross-domain** setting

Contact: Hung-Yu Tseng (htseng6@ucmerced.edu), Yi-Wen Chen (ychen319@ucmerced.edu)

## Paper
Please cite our paper if you find the code or dataset useful for your research.

Regularizing Meta-Learning via Gradient Dropout<br>
[Hung-Yu Tseng*](https://sites.google.com/site/hytseng0509/), [Yi-Wen Chen*](), [Yi-Hsuan Tsai](), [Sifei Liu](), [Yen-Yu Lin](), [Ming-Hsuan Yang](http://faculty.ucmerced.edu/mhyang/)<br>
ArXiv pre-print, 2020
```
@article{dropgrad,
  author = {Tseng, Hung-Yu and Chen, Yi-Wen and Tsai, Yi-Hsuan and Liu, Sifei and Lin, Yen-Yu and Yang, Ming-Hsuan},
  booktitle = {International Conference on Learning Representations},
  title = {Regularizing Meta-Learning via Gradient Dropout},
  year = {2020}
}
```

## Usage

### Prerequisites
- Python >= 3.5
- Pytorch >= 1.3 and torchvision (https://pytorch.org/)
- You can use the `requirements.txt` file we provide to setup the environment via Anaconda.
```
conda create --name py36 python=3.6
conda install pytorch torchvision -c pytorch
pip3 install -r requirements.txt
```

### Install
Clone this repository:
```
git clone https://github.com/hytseng0509/DropGrad.git
cd CrossDomainFewShot
```

### Datasets
Download 2 datasets seperately with the following commands.
- Set `DATASET_NAME` to: `cub`, `miniImagenet`.
```
cd filelists
python3 process.py DATASET_NAME
cd ..
```
- Refer to the instruction [here](https://github.com/wyharveychen/CloserLookFewShot#self-defined-setting) for constructing your own dataset.


### Training
Train gradient-based model on the mini-ImageNet dataset.
- `DPMETHOD` : dropout method `none`, `binary`, `gaussian`.
- `DPRATE`: we suggest [0.1, 0.2].
```
python3 train.py --dropout_method DPMETHOD --dropout_rate DPRATE --name MAML_DPMETHOD_DPRATE --train_aug
```

### Evaluation
Test the model on the mini-ImageNet or CUB (cross-domain) dataset
- Specify `--dataset` to `miniImagenet` or `cub`
```
python3 test.py --name MAML_DPMETHOD_DPRATE --dataset TESTSET
```

## Note
- This code is built upon the implementation from [CloserLookFewShot](https://github.com/wyharveychen/CloserLookFewShot).
- The dataset, model, and code are for non-commercial research purposes only.
- You can change the number of shot (i.e. 1/5 shots) using the argument `--n_shot`.