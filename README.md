# PerceptualGAN

<p align="center"><img width="100%" src="front.jpg" /></p>

This is a PyTorch implementation of the following paper

[Image Manipulation with Perceptual Discriminators](https://arxiv.org/abs/1809.01396) <br/>
[Diana Sungatullina]()<sup> 1</sup>, [Egor Zakharov]()<sup> 1</sup>, [Dmitry Ulyanov]()<sup> 1</sup>, [Victor Lempitsky]()<sup> 1,2</sup>
<br/>
<sup>1 </sup>Skolkovo Institute of Science and Technology <sup>2 </sup>Samsung Research <br/>
European Conference on Computer Vision ([ECCV](https://eccv2018.org/)), 2018

## Dependencies
* [Python 3.5+](https://www.continuum.io/downloads)
* [PyTorch 0.4.0](http://pytorch.org/)
* [TensorFlow 1.3+](https://www.tensorflow.org/) (for tensorboard)

## Usage

### 1. Cloning the repository
```bash
$ git clone https://github.com/egorzakharov/PerceptualGAN.git
$ cd PerceptualGAN/
```

### 2. Downloading the required dataset

Please follow the guidelines from official repositories

#### [Celeba-HQ](https://github.com/tkarras/progressive_growing_of_gans)
#### [monet2photo, apple2orange](https://github.com/junyanz/CycleGAN)

### 3. Setting up tensorboard for pytorch

All training data (with intermediate results) is displayed via tensorboard.

Follow the installation instructions in [repository](https://github.com/lanpa/tensorboardX).

To launch, run the following command in repository folder:

```bash
tensorboard --logdir runs
```

### 4. Training

Set the following options within the training script:

<b>images_path</b>: for Celeba-HQ should point at the folder with images

<b>train/test_img_A/B_path</b>: should point either at the txt list with image names (as in the case of Celeba-HQ) or at image folders (CycleGAN).

<b>pretrained_gen_path</b>: when training with GAN loss, should point at the folder with latest_gen_B.pkl file

Examples are present within scripts directory. For detailed description of options refer to:

```
train.py
models/translation_generator.py
models/discriminator.py
```

### 5. Testing

Example usage:

```bash
$ python test.py --input_path data/celeba_hq --img_list data/lists_hq/smile_test.txt --image_size 256 \
--net_path runs/celebahq_256p_smile/checkpoints/latest_gen_B.pkl --output_path results/smile_test
```

<br/>

## Acknowledgement

This work has been supported by the Ministry of Education and Science of the Russian Federation (grant 14.756.31.0001).
