# HMA

## Updates
- ✅ 2023-09-09: Release the codes and results of HMA.
- ✅ 2024-09-26: Release the pre-train models of HMA.

## Overview
<img src="https://github.com/korouuuuu/HMA/blob/main/figs/Comparison.png" width="600"/>


**Benchmark results on SRx4.**
| Model | Set5 | Set14 | BSD100 | Urban100 | Manga109 |
|-------|:---------:|:---------:|:---------:|:---------:|:---------:|
| [SwinIR](https://github.com/JingyunLiang/SwinIR) | 32.92 | 29.09 | 27.92 | 27.45 | 32.03 |
| HMA | 33.38 | 29.51 | 28.13 | 28.69 | 33.19 |

**Comparison with the state-of-the-art methods.**
<img src="https://github.com/korouuuuu/HMA/blob/main/figs/Visual_Results.png" width="800"/>

## Environment
- [PyTorch >= 1.9.1](https://pytorch.org/)
- [BasicSR == 1.3.4.9](https://github.com/XPixelGroup/BasicSR/blob/master/INSTALL.md)

- ### Installation
Install Pytorch first.
Then,
```
pip install -r requirements.txt
python setup.py develop
```
## How To Test
- Refer to `./options/test` for the configuration file of the model to be tested, and prepare the testing data and pretrained model.  
- The pretrained models are available at
[Google Drive](https://drive.google.com/drive/folders/13Bxt_BXtWgwwcO7tjfoL6zYZAUY1v3zi?usp=sharing).  
- Then run the following codes (taking `HMA_SRx2_pretrain.pth` as an example):
```
python hma/test.py -opt options/test/HMA_SRx2.yml
```
The testing results will be saved in the `./results` folder.  

## How To Train
- Refer to `./options/train` for the configuration file of the model to train.
- Preparation of training data can refer to [this page](https://github.com/XPixelGroup/BasicSR/blob/master/docs/DatasetPreparation.md). ImageNet dataset can be downloaded at the [official website](https://image-net.org/challenges/LSVRC/2012/2012-downloads.php).
- The training command is like
```
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 python -m torch.distributed.launch --nproc_per_node=8 --use_env --master_port=4321 hma/train.py -opt options/train/train_HMA_SRx4_from_Imagenet.yml --launcher pytorch
```

The training logs and weights will be saved in the `./experiments` folder.

## Results
The inference results on benchmark datasets are available at
[Google Drive](https://drive.google.com/drive/folders/1W30mc0CeNOc_mGUWp9XuKJrQSF4WD7zW?usp=drive_link).

## Citations
#### BibTeX

    @InProceedings{Chu_2024_CVPR,
    author    = {Chu, Shu-Chuan and Dou, Zhi-Chao and Pan, Jeng-Shyang and Weng, Shaowei and Li, Junbao},
    title     = {HMANet: Hybrid Multi-Axis Aggregation Network for Image Super-Resolution},
    booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
    month     = {June},
    year      = {2024},
    pages     = {6257-6266}
    }



## Contact
If you have any question, please email douzhichao2021@163.com to discuss with the authors.
