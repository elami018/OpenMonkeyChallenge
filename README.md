# Open Monkey Challenge

The Goal of this project is to create an artificial neural network that can identify the poses in Non-Human Primates (NHPs) as part of the OpenMokey Challenge(*hosted on [Codalab](https://competitions.codalab.org/competitions/34342#learn_the_details)*). 

<img src="https://github.com/elami018/OpenMonkeyChallenge/blob/main/data/OpenMonkey-Main.png" width="800" height="400">

> The OpenMonkeyChallenge is a computer vision benchmark challenge for Non-Human Primate (NHP) pose tracking. It is an open and ongoing competition based on our provided dataset. Our dataset consists of over 100,000 annotated (17 body landmarks) photographs of NHPs in naturalistic contexts obtained from various sources including the internet, National Primate Centers, and the Minnesota Zoo. Our dataset includes diverse species of monkeys and apes. The 17 landmarks together comprise a pose.

## Dataset

<img src="https://github.com/elami018/OpenMonkeyChallenge/blob/main/data/Dataset.png" width="265" height="400">

The dataset contained 111,529 images of 26 species of primates. For each photograph, the region of interest was cropped such that each cropped image contained at least one primate. The 17 landmarks together comprise a pose. The landmarks include Nose, Left eye, Right eye, Head, Neck, Left shoulder, Left elbow, Left wrist, Right shoulder, Right elbow, Right wrist, Hip, Left knee, Left ankle, Right knee, Right ankle, and Tail.

> Each data instance is made of a triplet, {image, species, pose}. Codalab use the following JSON format:

```json
annotation{
      "image_id"              :   int,
      "species_id"            :   int,
      "file_name"             :   str,
      "landmarks"             :   [x1,y1,v1, ...],
}
```
> where x,y,v are the xy coordinate of landmark, and its visibility (one if visible and zero otherwise.).

## Approach

<img src="https://github.com/elami018/OpenMonkeyChallenge/blob/main/data/DLCpurple.png" width="400" height="100">

Given that the problem at hand is to create a model that
can perform well on the benchmark dataset, our solution
aims to use a residual net (ResNet50) model for our archi-
tecture. We will train an artificial neural network to estimate
the key points in the apes using the popular [DeepLabCut](http://www.mackenziemathislab.org/deeplabcut)
algorithm (*Mathis et al*). DeepLabCut has been shown to be supe-
rior amongst its peers in terms of accuracy for pose esti-
mation in animals. Briefly stated, DeepLabCut is a flex-
ible and simple algorithm that transfers the 50-layer ResNet
pre-trained for the ImageNet object identification task for
keypoint estimation by substituting the classification layer
at the ResNet’s output with the deconvolutional layers.

<img src="https://github.com/elami018/OpenMonkeyChallenge/blob/main/data/DLC-arch.png" width="600" height="400">

> *For further reading refer to our [paper](https://github.umn.edu/MUKHE100/Computer-Vision/blob/main/OpenMonkey/Project%20Report.pdf)*.
