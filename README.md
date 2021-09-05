# coding-template

## Summary

The summary can contain but is not limited to:

- Code structure.

- Commands to reproduce your experiments.

- Write-up of your findings and conclusions.

- Ipython notebooks can be organized in `notebooks`.

## Reference

Any code that you borrow or other reference should be properly cited.

https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html

## Task
Image Classification

## Datasets
1. CIFAR-10, 
2. Tiny-ImageNet
3. .

## Base Model
ConvNets?
5 layers?

Test - Marlan

### Colab Link
https://colab.research.google.com/drive/1s8Yp01Z0dDjpbCsEVAeC17ATLyQQyfGE?usp=sharing

### Results

#### Activation

##### Test Accuracy
|   | CIFAR-10 | Tiny-ImageNet | . |
|---|---|---|---|
| Sigmoid  |   |   |   |
|  Tanh | 65.32  |   |   |
|  ReLU | 63.45 |   |   |
|  LeakyReLU | 64.45 |   |   |
|  Maxout |   |   |   |
|  Softsign | 65.39  |   |   |
|  Softplus | 56.56  |   |   |

##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | . |
|---|---|---|---|
| Sigmoid  |   |   |   |
|  Tanh |   |   |   |
|  ReLU | 1.08 |   |   |
|  LeakyReLU | 1.07 |   |   |
|  Maxout |   |   |   |
|  Softsign |   |   |   |
|  Softplus | 1.25 |   |   |

#### Initialization
CIFAR-10
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) |   |   |   |  |  |
|  normalized |   |   |   |   |   |
|  orthoginal |   |   |   |   |   |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |
