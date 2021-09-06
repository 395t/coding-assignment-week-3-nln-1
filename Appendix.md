
##### Test Loss
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 1.08 |  4.11 |  2.40 |
|  LeakyReLU | 1.07 | 4.35  | 2.50  |
|  Tanh | 1.03  |  4.36 |  2.17 |
|  Maxout | 1.10 | 4.25 | 2.12  |
|  Softplus | 1.18 | 5.30  |  2.74 |
|  Softsign |  0.98 | 4.48  | 2.23  |


##### Test Loss on CIFAR-10
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 1.08  | 1.07  |   | 1.25 |  |
|  normalized | 1.46  | 1.47  | 1.64  | 1.33  | 1.22  |
|  orthogonal | 1.16  | 1.15  | 1.29  | 1.21  | 1.11  |
|  xavier | 1.18  | 1.11  | 1.29  | 1.24  | 1.07  |


##### Test Accuracy on Tiny-Imagenet
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 12.15  | 9.87  | 11.21  |  |  |
|  normalized | 0.51  | 3.53  | 3.05  | 0.54  | 9.89  |
|  orthogonal | 10.66  | 10.95  | 10.97  | 0.56  | 15.56  |
|  xavier |   |   |   |   |   |


##### Test Loss on Tiny-Imagenet
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 4.11  | 4.35  | 4.28  |  |  |
|  normalized | 5.30  | 4.88  | 5.21  | 5.30  | 4.44  |
|  orthogonal | 4.20  | 4.15  | 4.37  | 5.30  | 3.97  |
|  xavier |   |   |   |   |   |


##### Test Loss on Caltech101
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 2.40  | 2.50  | 2.17  | 2.74 | 2.23 |
|  normalized | 3.48  | 3.24  | 3.59  | 4.21  | 2.80  |
|  orthogonal | 2.57  | 2.60  | 2.13  | 2.68  | 2.07 |
|  xavier | 2.56  |  2.56 | 2.06  | 2.72  | 1.95  |



##### Test Loss on CIFAR-10
|   | 0.1 | 0.01 | 0.001 | 0.0001 |
|---|---|---|---|---|
|  ReLU      | 2.37 | 2.02  | 1.08  | 1.36  |
|  LeakyReLU | nan |  1.79 | 1.07 | 1.33 |
|  Tanh      | 63.13  | 3.87  |  1.03 | 1.10 |
|  Maxout    | nan | nan  | 1.10  | 1.12 |
|  Softplus  | 2.35  | 1.18  |  1.18 | 2.31  |
|  Softsign  | 76.15 | 1.48  | 0.98  | 1.36  |
