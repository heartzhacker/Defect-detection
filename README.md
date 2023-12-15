## Defect-Detection-Classifier
    Defect detection of water-cooled wall. The sample is hard to collect, so we only have a little dataset 
    which includes 320 training images(160 normal+ 160 defect) and 80 testing images(40 normal+ 40 defect). 
    The image size is 256*256. The dataset is collected by Dong Jin. Thanks the advice from Yu Fang about 
    the using of gcForest.
## dataset 
    the above three images are normal examples and the below are defect.
![normal1](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/normal/2.jpg)
![normal2](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/normal/3.jpg)
![normal3](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/normal/4.jpg)
![defect1](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/defect/2.jpg)
![defect2](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/defect/3.jpg)
![defect3](https://github.com/marooncn/Defect-Detection-Classifier/blob/master/data/train/defect/4.jpg)
## Classifier
    We use Support Vector Machine(SVM) with different feature extractors, deep forest and Convolutional Neural 
    Network to train the classifier.
* Gauss filter+LBP+SVM(rbf kernel)

      Use Gaussian filter and laplacian operator to denoise and extracts edges, then LBP(Local Binary Patt-
      ern) extract features of preprocessed images as the input of SVM.
* CNN+SVM(rbf kernel)
      
      Use VGG16 to extract features as the input of SVM., the weight of VGG16 is trained on ImageNet.
* simple CNN(3 Conv+1 FC)

      Build a simple neural network to train. The network consists of three convolutional layers and a fully
      connected layer.
* transfer Learning(VGG16)
    
      Use VGG16 to extract features as input of a simple network that consists of a fully-connected layer.
* Neural Network Search
    
      Use NNS to search a best network.
* gcForest
    
      Use deep forest(Only cascade forest structure/With multi-grained forests) to train the ensemble classifier. 
### Result
 
|                classifier                  |   accuracy   | 
|--------------------------------------------|--------------|
|      Gauss filter+LBP+SVM(rbf kernel)      |    97.25%    | 
|            CNN+SVM(rbf kernel)             |    71.25%    | 
|          simple CNN(3 Conv+1 FC)           |    72.50%    | 
|         transfer Learning(VGG16)           |    81.25%    |
|          Neural Network Search             |    82.28%    |
|  gcForest (without multi-grained forests)  |    80.00%    |
| gcForest (with multi-grained forests, i=8) |    88.75%    |

