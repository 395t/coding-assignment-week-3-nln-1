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

## Results

### Activation


##### Test Accuracy
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 63.45 |   |  46.62 |
|  LeakyReLU | 64.45 |   |  44.24 |
|  Tanh | 65.32  |   |  53.15 |
|  Maxout | 62.83 | 10.86 | 50.77  |
|  Softplus | 56.56  |   | 38.79  |
|  Softsign | 65.39  |   | 49.08  |


##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 1.08 |   |  2.40 |
|  LeakyReLU | 1.07 |   | 2.50  |
|  Tanh |   |   |  2.17 |
|  Maxout | 1.10 | 4.25 | 2.12  |
|  Softplus | 1.25 |   |  2.74 |
|  Softsign |   |   | 2.23  |


### Initialization
CIFAR-10 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 63.45  | 64.45  | 65.32  | 56.56 | 65.39 |
|  normalized |   |   |   |   |   |
|  orthogonal | 59.52  | 60.81  | 56.29  | 57.85  | 61.75  |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |

CIFAR-10 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 1.08  | 1.07  |   | 1.25 |  |
|  normalized |   |   |   |   |   |
|  orthogonal | 1.16  | 1.15  | 1.29  | 1.21  | 1.11  |
|  xavier | 1.18  | 1.11  | 1.29  | 1.24  | 1.07  |

Tiny Imagenet Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) |   |   |   |  |  |
|  normalized |   |   |   |   |   |
|  orthogonal | 10.66  | 10.95  | 10.97  | 0.56  | 15.56  |
|  xavier |   |   |   |   |   |

Tiny Imagenet Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) |   |   |   |  |  |
|  normalized |   |   |   |   |   |
|  orthogonal | 4.20  | 4.15  | 4.37  | 5.30  | 3.97  |
|  xavier |   |   |   |   |   |

Caltech101 Accuracy
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) |   |   |   |  |  |
|  normalized | 24.88  | 30.95  | 27.19  | 8.99  | 39.25  |
|  orthogonal | 41.55  | 42.86  | 52.30  | 39.09  | 51.69  |
|  xavier |   |   |   |   |   |

Caltech101 Test Loss
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) |   |   |   |  |  |
|  normalized | 3.48  | 3.24  | 3.59  | 4.21  | 2.80  |
|  orthogonal | 2.57  | 2.60  | 2.13  | 2.68  | 2.07 |
|  xavier |   |   |   |   |   |

### Stability of Model to Hyperparams (learning rate)
|   | 0.1 | 0.01 | 0.001 | 0.0001 |
|---|---|---|---|---|
|  ReLU |  |   | 63.45  |   |
|  LeakyReLU |  |   | 64.45 |   |
|  Tanh |   |   |  65.32 |  |
|  Maxout |  |   | 62.83  |  |
|  Softplus |  |   | 56.56  |   |
|  Softsign |   |   |  65.39 |   |

