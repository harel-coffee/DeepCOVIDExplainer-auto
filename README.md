## DeepCOVIDExplainer: Explainable COVID-19 Diagnosis from Chest X-rays
Supplementary materials for "DeepCOVIDExplainer: Explainable COVID-19 Diagnosis from Chest Radiography Images" accepted at IEEE International Conference on Bioinformatics and Biomedicine (BIBM'2020), to be held in Seoul, South Korea. We provide details of dataset, preprocessing, network architectures, and some additional results. Nevertheless, we'll provide trained models, preprocessed data, interactive Python notebooks, and a web application showing live demo. As planned, we keep this repo updated. 

### Methods
The pipeline of "DeepCOVIDExplainer" consist of preprocessing, classification, snapshot neural ensemble, and decision visualizations. After necessary preprocessing of CXR images, DenseNet, ResNets, and VGGNets are trained in a transfer learning setting, creating their model snapshots, followed by neural snapshot ensemble based on averaging Softmax class posterior and the prediction maximization of best performing models. Finally, class-discriminating attention maps are generated using gradient-guided class activation maps (Grad-CAM++) and layer-wise relevance propagation (LRP) to provide explanations of the predictions and to identify the critical regions on patients chest.  

#### Erratum 
Although we mentioned in the paper mistakenly that network's weights were initialized with ImageNet, we rather trained them from scratch (please refer to the Jupyter notebooks). The reason is that ImageNet contains photos of general objects, which would activate the internal representation of network's hidden layers with geometrical forms, colorful patterns, or irrelevent shapes that are usually not present in biomedical images, e.g., x-ray, MRIs, or CT. 

### Datasets
We choose 3 different versions of COVIDx dataset to train and evaluate the model. The COVIDx v1.0 had a total of 5,941 CXR images from 2,839 patients. It is based on COVID-19 image dataset curated by Joseph P. C., et al. and Kaggle CXR Pneumonia dataset (https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia) by Paul Mooney. COVIDx v1.0 is already used in a literature (https://arxiv.org/abs/2003.09871). However, Kaggle CXR images are of children. Therefore, to avoid possible prediction bias~(e.g., the model might predict based on the chest size itself), we consider using the CXR of adults with pneumonia by augmenting more CXR images from COVID-19 confirmed cases.

COVIDx v2.0 dataset is also based on COVID-19 image dataset, but come with RSNA Pneumonia Detection Challenge dataset (https://www.kaggle.com/c/rsna-pneumonia-detection-challenge) provided by the Radiological Society of North America. On the other hand, COVIDx v3.0 is also based on COVID-19 image dataset and RSNA Pneumonia dataset, we enriched it with additional 49 COVID-19 CXR from: i) Italian Radiological Case CASE (https://radiopaedia.org/articles/covid-19-3?lang=us), and ii) Radiopaedia.org (provided by Dr. Fabio Macori)(https://www.sirm.org/category/senza-categoria/covid-19/). COVIDx v1.0 CXR images are categorized with normal, bacterial, non-COVID19 viral and COVID19 viral, whereas COVIDx v2.0 and v3.0 CXR images are categorized as normal, pneumonia and COVID19 viral. The distribution of images and patient cases amongst the different infection types are as follows: 

### Data availability
We will open source the preprocessed data in npy file format to ease the community to build the model with ease. However, it'll take a few more days. 

### Availability of pretrained models
We plan to make public all the pretrained models and some computational resources available, but it will take time. For the time being, we made only VGG-19 and ResNet-18 upon reasonable request. 

### A quick instructions
A quick example on a small dataset can be performed as follows: 

### Citation request
If you use the code of this repository in your research, please consider citing the folowing papers:

    @inproceedings{DeepCOVIDExplainer,
        title={DeepCOVIDExplainer: Explainable COVID-19 Diagnosis from Chest X-ray Images},
        author={Karim, Md Rezaul and Döhmen, Till and Rebholz-Schuhmann, Dietrich and Decker, Stefan and Cochez, Michael and Beyan, Oya},
        conference={IEEE International Conference on Bioinformatics and Biomedicine (BIBM'2020)},
        publisher={IEEE},
        year={2020}
    }

### Contributing
In future, we'll provide an email address, in case readers have any questions. 
