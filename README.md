# coding-template

## Summary

The summary can contain but is not limited to:

- Code structure.

- Commands to reproduce your experiments.

- Write-up of your findings and conclusions.

- Ipython notebooks can be organized in `notebooks`.

## Reference

We referred the following tutorial while designing our model architecture and coding the complete pipeline.

https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html

## Task
The Conv Net model is designed for image classification.

## Datasets
We evaluate our model on 3 publicly available main-stream image datasets:

#### CIFAR-10
This dataset consists of 60000 colour images of size 3x32x32 that are uniformly distributed across 10 classes such as airplane, horse, ship, etc. The dataset was downloaded from the following source: 
- [Learning Multiple Layers of Features from Tiny Images](https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf), Alex Krizhevsky, 2009.

#### Tiny-Imagenet

#### Caltech101
This dataset consists of colour images of objects belonging to 101 classes. The images are unevenly distributed with 40 to 800 images corresponding to each class. Though, most classes have exactly 50 images. The size of the images also varies a lot around 300x200 pixels. We center crop the pictures (and introduce padding wherever necessary) to make them 256x256 before downsampling them to 64x64 for feasibility of training. 

## Base Model
ConvNets?
5 layers?

### Colab Link
https://colab.research.google.com/drive/1xIgCBX1CQhPzeffXPcjsHHKSnNpusNjl?usp=sharing

## Results

### Activation



![Cifar10_default_training_loss](https://user-images.githubusercontent.com/13873880/132144385-04009348-e681-455c-b70d-b748b5a219c2.png)
![Cifar10_default_validation_loss](https://user-images.githubusercontent.com/13873880/132144478-d92bac1b-37ff-4db5-a4b2-b06ae9ddf720.png)


![Caltech_default_training_loss](https://user-images.githubusercontent.com/13873880/132142942-f9faa9ec-15aa-492c-8e76-cb11cbefc479.png)
![Caltech_default_validation_loss](https://user-images.githubusercontent.com/13873880/132142943-1b1ec9a6-965e-4441-b097-343bf766e4b5.png)


##### Test Accuracy
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 63.45 | 12.15  |  46.62 |
|  LeakyReLU | 64.45 |  9.87 |  44.24 |
|  Tanh | 65.32  | 12.53  |  53.15 |
|  Maxout | 62.83 | 10.86 | 50.77  |
|  Softplus | 59.28  | 0.43  | 38.79  |
|  Softsign | 65.39  | 13.66  | 49.08  |


##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 1.08 |  4.11 |  2.40 |
|  LeakyReLU | 1.07 | 4.35  | 2.50  |
|  Tanh |   |  4.36 |  2.17 |
|  Maxout | 1.10 | 4.25 | 2.12  |
|  Softplus | 1.18 | 5.30  |  2.74 |
|  Softsign |   | 4.48  | 2.23  |





### Initialization
CIFAR-10 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 63.45  | 64.45  | 65.32  | 56.56 | 65.39 |
|  normalized | 46.49  | 46.35  | 43.82  | 52.32  | 57.50  |
|  orthogonal | 59.52  | 60.81  | 56.29  | 57.85  | 61.75  |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |

CIFAR-10 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 1.08  | 1.07  |   | 1.25 |  |
|  normalized | 1.46  | 1.47  | 1.64  | 1.33  | 1.22  |
|  orthogonal | 1.16  | 1.15  | 1.29  | 1.21  | 1.11  |
|  xavier | 1.18  | 1.11  | 1.29  | 1.24  | 1.07  |

Tiny Imagenet Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 12.15  | 9.87  | 11.21  |  |  |
|  normalized |   |   |   |   |   |
|  orthogonal | 10.66  | 10.95  | 10.97  | 0.56  | 15.56  |
|  xavier |   |   |   |   |   |

Tiny Imagenet Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 4.11  | 4.35  | 4.28  |  |  |
|  normalized |   |   |   |   |   |
|  orthogonal | 4.20  | 4.15  | 4.37  | 5.30  | 3.97  |
|  xavier |   |   |   |   |   |

Caltech101 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 46.62  | 44.24  | 53.15  | 38.79  | 49.08  |
|  normalized | 24.88  | 30.95  | 27.19  | 8.99  | 39.25  |
|  orthogonal | 41.55  | 42.86  | 52.30  | 39.09  | 51.69  |
|  xavier |  42.17 |  42.86 | 53.99  | 41.24  | 55.38  |

Caltech101 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 2.40  | 2.50  | 2.17  | 2.74 | 2.23 |
|  normalized | 3.48  | 3.24  | 3.59  | 4.21  | 2.80  |
|  orthogonal | 2.57  | 2.60  | 2.13  | 2.68  | 2.07 |
|  xavier | 2.56  |  2.56 | 2.06  | 2.72  | 1.95  |

### Stability of Model to Hyperparams (learning rate)
|   | 0.1 | 0.01 | 0.001 | 0.0001 |
|---|---|---|---|---|
|  ReLU |  |   | 63.45  |   |
|  LeakyReLU |  |   | 64.45 |   |
|  Tanh |   |   |  65.32 |  |
|  Maxout |  |   | 62.83  |  |
|  Softplus |  |   | 56.56  |   |
|  Softsign |   |   |  65.39 |   |
