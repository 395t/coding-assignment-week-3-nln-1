
# Non-linearities and Initializations 


## Code Structure
All of the code to reproduce our experiments can be found in `Nonlinear_Activation_and_Initalizations.ipynb`. This includes code to load any of the three datasets used in our experiments, network creation, training function and visualization of test results.

## Commands to Reproduce Experiments
To run locally, create a virtual environment and install the libraries in requirements.txt using the following commands. Alternately, you can use Google Colab to directly run the code.
```
python3 -m venv my_venv
source my_venv/bin/activate
pip3 install -r requirements
pip3 install jupyter notebook
```

To run an experiment, edit the hyperparameters cell in the notebook to select desired experimental settings then simply run all cells in the notebook.


## Task
Our Conv Net model is designed for image classification.


## Model Architecture
We implement a simple convolutional network for our image classification tasks consisting of two convolutional feature extracting blocks followed by two fully connected classification layers and an output layer. Each convolutional block is made up of two convolutional layers and a maxpooling layer. The non-linearities specified in each experiment are applied after each of the four convolutional layers as well as after the two fully connected layers. 

We have two varitations of our network, one to handle input images of size 32x32 defined in the Net() class and one that handles input images of size 64x64 defined in the Net64() class. 


## Datasets
We evaluate our model on 3 publicly available main-stream image datasets:

#### CIFAR-10
This dataset consists of 60000 colour images of size 3x32x32 that are uniformly distributed across 10 classes such as airplane, horse, ship, etc. We split this data into 40k/10k/10k for training, validation and testing respectively. The dataset was downloaded from the following source: 
- [Learning Multiple Layers of Features from Tiny Images](https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf), Alex Krizhevsky, 2009.

#### Tiny-Imagenet
This is a subset of the ImageNet dataset and contains 100000 colour images of 200 classes (500 per class) that are downsized to 64x64 from 256x256. The images are divided into the train, validate and test sets as 350/75/75 for each class. The dataset was introduced in
- Le, Ya, and Xuan Yang. "[Tiny imagenet visual recognition challenge.](http://cs231n.stanford.edu/reports/2015/pdfs/yle_project.pdf)" CS 231N 7.7 (2015): 3.

#### Caltech101
This dataset consists of colour images of objects belonging to 101 classes. The images are unevenly distributed with 40 to 800 images corresponding to each class. Though, most classes have exactly 50 images. The total number of images are 8680 which are divided into train, validate and split sets in the ratio 0.7:0.15:0.15, stratified on the class label. 

The size of the images also vary a lot around 300x200 pixels. We center crop the pictures (and introduce padding wherever necessary) to make them 256x256 before downsampling them to 64x64 for feasibility of training. The dataset was made available by
- Fei-Fei, Li, Rob Fergus, and Pietro Perona. "[One-shot learning of object categories.](http://vision.stanford.edu/documents/Fei-FeiFergusPerona2006.pdf)" IEEE transactions on pattern analysis and machine intelligence 28.4 (2006): 594-611.


## Experiments

We compare 6 non-linear activation functions in our model on image classification task - 

- ReLU [(Deep Sparse Rectifier Neural Networks, Glorot, Bordes, Bengio; 2011)](https://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf)
- LeakyReLU [(Rectifier Nonlinearities Improve Neural Network Acoustic Models, Maas, Hannun, Ng; 2013)](https://ai.stanford.edu/~amaas/papers/relu_hybrid_icml2013_final.pdf)
- Tanh [(Deep Sparse Rectifier Neural Networks, Glorot, Bordes, Bengio; 2011)](https://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf)
- Maxout [(Maxout Networks, Goodfellow, Warde-Farley, Mirza, Courville, Bengio; 2013)](https://arxiv.org/abs/1302.4389)
- Softsign [(Understanding the difficulty of training deep feedforward neural networks, Glorot, Bengio; 2010)](https://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf)
- Softplus [(Deep Sparse Rectifier Neural Networks, Glorot, Bordes, Bengio; 2011)](https://proceedings.mlr.press/v15/glorot11a/glorot11a.pdf)

We also evaluate the performance of our model with different initialization strategies. We compare the 6 activations above with the following model initializations (on all 3 datasets):

- Random (default)
- Normalized [(Exact solutions to the nonlinear dynamics of learning in deep linear neural networks, Saxe, McClelland, Ganguli; 2013)](https://arxiv.org/abs/1312.6120)
- Orthogonal [(Exact solutions to the nonlinear dynamics of learning in deep linear neural networks, Saxe, McClelland, Ganguli; 2013)](https://arxiv.org/abs/1312.6120)
- Xavier [(Understanding the difficulty of training deep feedforward neural networks, Glorot, Bengio; 2010)](https://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf)

Finally, we also test the stability of our model to varying learning rate. We measure model performance with 4 values of learning rate - 0.1, 0.01, 0.0001, 0.00001.

We use 2 metrics of evaluation for comparing the model performance in any experiment - Test Accuracy and Test Loss (the test loss results are in `appendix.md`).

## Results and Discussions

We train the model for 10-15 epochs depending on the convergence. The loss on the validation set is used for model selection. The convergence plots show that most activations cause the model to converge between 10 to 15 epochs while some activations like maxout converge before 10 epochs.

![Cifar10_default_training_loss](https://user-images.githubusercontent.com/13873880/132155801-f1040647-7b71-4f6e-adf8-9d6093aad176.png)
![Cifar10_default_validation_loss](https://user-images.githubusercontent.com/13873880/132155803-056325a4-c101-4e46-9185-bb4c5d9bc6ea.png)


![Caltech_default_training_loss](https://user-images.githubusercontent.com/13873880/132142942-f9faa9ec-15aa-492c-8e76-cb11cbefc479.png)
![Caltech_default_validation_loss](https://user-images.githubusercontent.com/13873880/132142943-1b1ec9a6-965e-4441-b097-343bf766e4b5.png)

### Variation with Activation Function 
- Surprisingly, the tanh and softsign activation gets best performance across activations.
- Softlpus is clearly struggling on tiny-imagenet, and obtaining lower performances in the other 2 datasets.
- The performance of the model (with every activation) on tiny-imagenet is considerably poor compared to other datasets. This can be attributed to the higher variance in the input images across classes and the greater number of classes, which requires a deeper model like VGG16 to learn better. We couldn???t try that due to lack of time. We also experimented with a subset of 50 classes from the dataset but there was no significant improvement in the performance. 



##### Test Accuracy
|   | CIFAR-10 | Tiny-ImageNet | CalTech 101 |
|---|---|---|---|
|  ReLU | 63.45 | 12.15  |  46.62 |
|  LeakyReLU | 64.45 |  9.87 |  44.24 |
|  Tanh | **65.32**  | 12.53  |  **53.15** |
|  Maxout | 62.83 | 10.86 | 50.77  |
|  Softplus | 59.28  | 0.43  | 38.79  |
|  Softsign | **65.39**  | **13.66**  | 49.08  |


### Variation with Model Initialization
- As discussed by Saxe et al., initialization of the weight matrices with orthogonal matrices leads to better model performance when compared to initialization via random normalized values from a Gaussian distribution. These results are evident across 15 experiments where the different initialization schemes were implemented across the three datasets using relu, leaky relu, tanh, softplus, and soft sign activations. The learning rate (0.001) and number of epochs (10) were held constant to more directly compare initialization performance.
- The results of our xavier initialization experiments were generally ineffective when paired with ReLU and Leaky ReLU and showed some signs of potential improvement with the tanh, softplus, and softsign activation functions specifically with the CalTech 101 dataset. On the CIFAR-10 dataset it performed worse than the default initialization for all activation functions. We hypothesize that the issue of the decreasing variance of the back propagated gradients discussed by Glorot et al. may not have been as evident in the CIFAR-10 dataset relative to the CalTech101 dataset where the improved accuracy with Xavier initialization seems to show the existence of this issue.

##### Test Accuracy on CIFAR-10
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 63.45  | 64.45  | **65.32**  | 56.56 | **65.39** |
|  normalized | 46.49  | 46.35  | 43.82  | 52.32  | 57.50  |
|  orthogonal | 59.52  | 60.81  | 56.29  | 57.85  | 61.75  |
|  xavier | 59.46  | 61.53  | 55.77  | 57.65  | 63.05  |



##### Test Accuracy on Caltech101
|   | ReLU | Leaky ReLu | tanh | softplus | softsign |
|---|---|---|---|---|---|
| random (default) | 46.62  | 44.24  | 53.15  | 38.79  | 49.08  |
|  normalized | 24.88  | 30.95  | 27.19  | 8.99  | 39.25  |
|  orthogonal | 41.55  | 42.86  | 52.30  | 39.09  | 51.69  |
|  xavier |  42.17 |  42.86 | 53.99  | 41.24  | **55.38**  |



### Stability of Model to Hyperparameters (Learning Rate)
We measure model performances with learning rates of [0.1, 0.01, 0.001 (default), 0.0001]. If one model's performance is more invariant to different learning rates, it means the model is easier to train and also require less tuning. We compare results accross different activation functions.

- **Testing Accuracy**
  - As in the table below, softsign activation is clearly the most robust to varying learning rates. Maxout and softplus activations are the least stable, both getting results equivalent to random on two of the learning rates. However, maxout is actually pretty good when the learning rate is smaller, and softplus achieves the best accuracy (across activations) on 0.01 learning rate. ReLU, LeakyReLU and Tanh display medium stability with different value of learning rates.







##### Test Accuracy on CIFAR-10
|   | 0.1 | 0.01 | 0.001 | 0.0001 |
|---|---|---|---|---|
|  ReLU | 10.00 | 23.53  | 63.45  | 52.28  |
|  LeakyReLU | 10.00 |  34.82 | 64.45 | 52.61  |
|  Tanh | 19.40  | 24.90  |  **65.32** | 60.84 |
|  Maxout | 10.00 | 10.00  | 62.83  | 62.33 |
|  Softplus | 10.00 | 58.71  | 56.56  | 10.00  |
|  Softsign | 21.14  | 47.15  |  **65.39** | 51.01  |



- **Training Loss Across Activation with Different Learning Rate**
  - Generally, models that perform better lead to better convergence and thus lower training loss. Softplus is the only exception here; it seems to be the most robust to learning rates only looking at the training curve, but it actually struggles in terms of testing accuracy. We think it might be stuck at a local minima so that the loss is relatively low but it is actually not learning anything. Other than that,  we observe similar trends as in the testing accuracy, with softsign and tanh being the most robust. Another thing worth noting is that models using maxout converge really fast when the learning rate is smaller (0.001 and 0.0001). It could be the flexibility of this activation so that it can quickly capture the input feature distribution. 
(If you cannot find the training curve on the plot, meaning the loss for that specific activation is too high and cannot fit in the plot.)


![training_loss (lr=0.1](https://user-images.githubusercontent.com/35536646/132161741-b92905bf-8fe7-4530-a610-d17500c47683.png)
![training_loss (lr=0.01](https://user-images.githubusercontent.com/35536646/132161748-226797c1-1bc2-415b-8ba5-78eb6f8a959d.png)
![image_-3_across_activation](https://user-images.githubusercontent.com/35536646/132161928-92979b1b-b87f-4f01-a548-1ba03c6adefc.png)
![image_-4_across_activation](https://user-images.githubusercontent.com/35536646/132161932-8adf1cbc-28d8-44d0-a884-339e9a42be66.png)


Softplus is the most stable (in terms of training loss) across different learning rate, with loss contained in a reasonable range with all four rates. While maxout is the most unstable if appied larger learning rate(0.1, 0.01); both learning rates yield `nan` on training loss.

![softplus](https://user-images.githubusercontent.com/35536646/132161953-d85c284e-4b72-4bb4-be73-5cdf5e0e6cfc.png)
![maxout](https://user-images.githubusercontent.com/35536646/132161949-841f0cd5-ccc6-4e62-852f-ddd956ba4d94.png)




### Maxout Without Dropout and With Varying Number of Units

It is designed to work well with dropout, but seems to perform just fine without it
adding more units to max over seemed like it could improve performance, but the results say simpler is better


![Figure 1](https://user-images.githubusercontent.com/34489261/132160348-37134082-e969-40fb-975d-ec2a5f630db6.png) ![Figure 2](https://user-images.githubusercontent.com/34489261/132160352-b6595fc4-a542-4730-aa10-38d8b37dea18.png)


## Reference

We referred the following tutorial while designing our model architecture and coding the complete pipeline.

https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html
