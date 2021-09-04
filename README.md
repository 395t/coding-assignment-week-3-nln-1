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
2. CIFAR-100,
3. ImageNet

## Base Model
ConvNets?
5 layers?

Test - Marlan

### Colab Link
https://colab.research.google.com/drive/1s8Yp01Z0dDjpbCsEVAeC17ATLyQQyfGE?usp=sharing

### Results

#### Activation
|   | CIFAR-10 | CIFAR-100 | ImageNet |
|---|---|---|---|
| Sigmoid  |   |   |   |
|  Tanh |   |   |   |
|  ReLU | 64.06 |   |   |
|  LeakyReLU | 65.22 |   |   |
|  Maxout |   |   |   |

#### Initialization
|   | CIFAR-10 | CIFAR-100 | ImageNet |
|---|---|---|---|
| random  |   |   |   |
|  normal |   |   |   |
|  pretraining |   |   |   |
