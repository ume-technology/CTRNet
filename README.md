# CTRNet

This repository is the implementation of "Don't Forget Me: Accurate Background Recovery for Text Removal via Modeling Local-Global Context". [paper](https://arxiv.org/abs/2207.10273) [supple](https://drive.google.com/file/d/1PwiqIzv4jPYOmZLIoEoZSJpc1VqQcPWE/view?usp=sharing)

The inference codes are available. You can download one of our retrained model weights [Here](https://drive.google.com/file/d/1wcMYsoM7eLMX9aU8QvTH--b52C5Y4JaW/view?usp=sharing) （It can attain 35.14 in PSNR).

For any questions, please email to me. Thank you for your interest. 

## Environment
My environment can be refered as follows:
- Python 3.6.9
- PyTorch 1.3 (1.3+ is also work)
- [Inplace_Abn](https://github.com/mapillary/inplace_abn)
- torchlight 
- Polygon
- shapely

Install torchlight
```bash
cd ./torchlight
python setup.py install
```

## Datasets
We use [SCUT-EnsText](https://github.com/HCIILAB/SCUT-EnsText) and [SCUT-Syn](https://github.com/HCIILAB/Scene-Text-Removal).  

After downloading, run [`flist.py`](flist.py) to generate data lists. 

```bash
mkdir datasets
python flist.py --path path_to_enstext_test_set --output ./datasets/enstext_test.flist
```
All the images are set to 512 * 512. The strucuture images for LCG block are generated by the official code in [RTV methods](http://www.cse.cuhk.edu.hk/~leojia/projects/texturesep/). You can generate the data yourselves, and we will also provide the test data here. [data](https://drive.google.com/file/d/1U4WMlD6MW_x0y7-KE2ILxYDnvUBk8lfg/view?usp=sharing).

<!-- ## Training 
Create an new directory and place the pretrain weights for [TResNet_L](https://github.com/Alibaba-MIIL/ASL/blob/main/MODEL_ZOO.md) on OpenImage and our [Structure generator](https://github.com/Alibaba-MIIL/ASL/blob/main/MODEL_ZOO.md). You can also train the structure generator from scratch, but you should modify some codes in this project. 

```bash
CUDA_VISIBLE_DEVICES=0,1 python train.py \
        --bs 2 --gpus 2 --prefix CTRNet \
        --img_flist your/train/flist/of/paris \
        --TRresNet_path path/of/ASL/weight \
        --nEpochs 150
``` -->

## Testing 
For generating the results with text removal, the commond is as follows:

```bash
CUDA_VISIBLE_DEVICES=0 python test.py \
        --bs 1 --gpus 1 --prefix CTRNet \
        --img_flist your/test/flist/ \
        --model your/model/weights --save_path ./results --save \
```

## Acknowledge

The repository is benefit a lot from [SPL](https://github.com/WendongZh/SPL) and [DETR](https://github.com/facebookresearch/detr). Thanks a lot for their excellent work.

## Citation
If you find our method or dataset useful for your reserach, please cite:
```
@ARTICLE{CTRNet,
  author     ={Liu, Chongyu and Jin, Lianwen and Liu, Yuliang and Luo, canjie and Chen, Bangdong and Guo, Fengjun and Ding, Kai},
  journal    ={ECCV},
  title      ={Don’t Forget Me: Accurate Background Recovery for Text Removal via Modeling Local-Global Context},
  year       ={2022},}
```

## Feedback
Suggestions and opinions of our work (both positive and negative) are welcome. Please contact the authors by sending email to Chongyu Liu([liuchongyu1996@gmail.com](mailto:liuchongyu1996@gmail.com)). For commercial usage, please contact Prof. Lianwen Jin via ([eelwjin@scut.edu.cn](mailto:eelwjin@scut.edu.cn)).
