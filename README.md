<br><br><br>

# Non-staionary texture synthesis using adversarial expansions

This is the official code of paper [_Non-staionary texture synthesis using adversarial expansions_](http://vcc.szu.edu.cn/research/2018/TexSyn)

This code was mainly adapted by [Zhen Zhu](https://github.com/jessemelpolio) on the basis of the repository [CycleGAN](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix).

If you use this code for your research, please cite:

Non-staionary texture synthesis using adversarial expansions
[Yang Zhou*](http://mclab.eic.hust.edu.cn/~zhouyang/), [Zhen Zhu*](https://github.com/jessemelpolio), [Xiang Bai](http://mclab.eic.hust.edu.cn/~xbai/), [Dani Lischinski](http://www.cs.huji.ac.il/~danix/), [Daniel Cohen-Or](http://www.cs.tau.ac.il/~dcor/pubs.html), [Hui Huang](http://vcc.szu.edu.cn/~huihuang)
In SIGGRAPH 2018. (* equal contributions)


### Requirements

The total project can be well functioned under the following environment: 

* python-2.7 
* pytorch-0.3.0 with cuda correctly specified
* cuda-8.0
* other packages under python-2.7

### Preparations

Please run `download_pretrained_models` first to make a new folder `Models` and then download the VGG19 model pretrained on ImageNet to this folder. 

### Data

There is no restriction for the format of the source texture images. The structure of the data folder is recommanded as the provided sub-folders inside `datasets` folder. To be more specific, `datasets/half` is what we use in paper production.

The dataset structure is recommended as:
```
+--half
|
|   +--sunflower
|
|       +--train
|
|           +--sunflower.jpg
|
|       +--test
|
|           +--sunflower.jpg
|
|   +--brick
|
|       +--train
|
|           +--brick.jpg
|
|       +--test
|
|           +--brick.jpg
|
...
```


### Architecture of the repository

Inside the main folder, `train.py` is used to train a model as described in our paper. `test.py` is used to test with the original image(result is 2x the size of the input). `test_recurrent.py` is used for extreme expansions.

In folder `data`, file `custom_dataset_data_loader` specified five dataset mode: `aligned`, `unaligned`, `single` and `half_crop`. Generally, we use `single` for testing and `half_crop` for training. 

In folder `models`, two files are of great importance: `models.py` and `networks.py`, please carefully check it before using it. `half_gan_style.py` is the major model we use in our paper. Some utilities are implemented in `vgg.py`.

In folder `options`, all hyperparameters are specified here. If you want to specialize different types of experiments, please change them accordingly.

Folder `scripts` contains scripts used for training and testing. To train or test a model, use commands like `sh scripts/train_half_style.sh`. Go into these files to see how to specify some hyper parameters. `production` scripts are typically used in production period in our paper preparation.

Folder `util` contains some scripts to visualize internal layers inside network(cnn-vis.py), generate perlin noise (perlin2d.py), generate random tile (random_tile.py) and some other useful scripts.

### Train and test

Folder `scripts` contain scripts used for training and testing. To train or test a model, use commands like `sh scripts/train_half_style.sh`. Go into these files to see how to specify some hyper parameters. 


### Cite



### Acknowledgements

The code is based on project [CycleGAN](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix). We sincerely thank for their great work.


