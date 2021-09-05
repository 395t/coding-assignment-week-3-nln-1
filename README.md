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

### Colab Link
https://colab.research.google.com/drive/1xIgCBX1CQhPzeffXPcjsHHKSnNpusNjl?usp=sharing

### Results

#### Activation

##### Test Accuracy
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 63.45 |   |   |
|  LeakyReLU | 64.45 |   |   |
|  Tanh | 65.32  |   |   |
|  Maxout | 62.83 | 10.86 |   |
|  Softplus | 56.56  |   |   |
|  Softsign | 65.39  |   |   |


##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 1.08 |   |   |
|  LeakyReLU | 1.07 |   |   |
|  Tanh |   |   |   |
|  Maxout | 1.10 | 4.25 |   |
|  Softplus | 1.25 |   |   |
|  Softsign |   |   |   |


#### Initialization
CIFAR-10 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 63.45  | 64.45  | 65.32  | 56.56 | 65.39 |
|  normalized |   |   |   |   |   |
|  orthoginal | 59.52  | 60.81  | 56.29  | 57.85  | 61.75  |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |

CIFAR-10 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 1.08  | 1.07  |   | 1.25 |  |
|  normalized |   |   |   |   |   |
|  orthoginal | 1.16  | 1.15  | 1.29  | 1.21  | 1.11  |
|  xavier | 1.18  | 1.11  | 1.29  | 1.24  | 1.07  |

#### Stability of Model to Hyperparams (learning rate)
|   | 0.1 | 0.01 | 0.001 | 0.0001 |
|---|---|---|---|---|
|  ReLU |  |   | 63.45  |   |
|  LeakyReLU |  |   | 64.45 |   |
|  Tanh |   |   |  65.32 |  |
|  Maxout |  |   | 62.83  |  |
|  Softplus |  |   | 56.56  |   |
|  Softsign |   |   |  65.39 |   |

Accuracy of the relu network on the 10000 test images: 59.52 %
Test loss on the 10000 test images: 1.16 
Accuracy of the leaky_relu network on the 10000 test images: 60.81 %
Test loss on the 10000 test images: 1.15 
/usr/local/lib/python3.7/dist-packages/torch/nn/functional.py:1794: UserWarning: nn.functional.tanh is deprecated. Use torch.tanh instead.
  warnings.warn("nn.functional.tanh is deprecated. Use torch.tanh instead.")
Accuracy of the tanh network on the 10000 test images: 56.29 %
Test loss on the 10000 test images: 1.29 
Accuracy of the softplus network on the 10000 test images: 57.85 %
Test loss on the 10000 test images: 1.21 
Accuracy of the softsign network on the 10000 test images: 61.75 %
Test loss on the 10000 test images: 1.11 
Accuracy of the maxout network on the 10000 test images: 54.87 %
Test loss on the 10000 test images: 1.32
