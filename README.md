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
2. Tiny-Imagenet
3. .

## Base Model
ConvNets?
5 layers?

Test - Marlan

### Colab Link
https://colab.research.google.com/drive/1s8Yp01Z0dDjpbCsEVAeC17ATLyQQyfGE?usp=sharing

### Results

#### Activation
|   | CIFAR-10 | Tiny-Imagenet | . |
|---|---|---|---|
| Sigmoid  |   |   |   |
|  Tanh | 65.32  |   |   |
|  ReLU | 64.06 |   |   |
|  LeakyReLU | 65.22 |   |   |
|  Maxout |   |   |   |
|  Softsign | 65.39  |   |   |
|  Softplus |   |   |   |

#### Initialization
|   | CIFAR-10 | Tiny-Imagenet | . |
|---|---|---|---|
| random  |   |   |   |
|  normal |   |   |   |
|  pretraining |   |   |   |
