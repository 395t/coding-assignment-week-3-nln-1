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
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 63.45 |   |   |
|  LeakyReLU | 64.45 |   |   |
|  Tanh | 65.32  |   |   |
|  Maxout |   |   |   |
|  Softplus | 56.56  |   |   |
|  Softsign | 65.39  |   |   |


##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 1.08 |   |   |
|  LeakyReLU | 1.07 |   |   |
|  Tanh |   |   |   |
|  Maxout |   |   |   |
|  Softplus | 1.25 |   |   |
|  Softsign |   |   |   |


#### Initialization
CIFAR-10 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 63.45  | 64.45  | 65.32  | 56.56 | 65.39 |
|  normalized |   |   |   |   |   |
|  orthoginal |   |   |   |   |   |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |

CIFAR-10 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 1.08  | 1.07  |   | 1.25 |  |
|  normalized |   |   |   |   |   |
|  orthoginal |   |   |   |   |   |
|  xavier | 1.18  | 1.11  | 1.29  | 1.24  | 1.07  |
