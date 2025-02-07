# Ancient Language Handwritten Recognition Under Data Deficient Condition

This repository contains the implementation of a project focused on improving handwritten character recognition for ancient Indian languages using Capsule Networks, particularly under conditions of limited data.

## Introduction
The project addresses the challenge of recognizing handwritten characters in ancient Indian languages, which often suffer from a lack of substantial labeled training data. By leveraging Capsule Networks and innovative data augmentation techniques, the project aims to enhance recognition accuracy with very small datasets.



## Methodology
The system comprises several key steps:

1. Initial training of the CapsNet model
<p align="center"><img src="https://www.dropbox.com/s/s46msiyhqzwwy8c/sys_block_1_crop.png?dl=0&raw=1"></p>

3. Generating instantiation parameters and reconstructed images
<p align="center"><img src="https://www.dropbox.com/s/4jj1ffshh0ogjh3/sys_block_2_crop.png?dl=0&raw=1"></p>

3. Applying decoder re-training techniques
<p align="center"><img src="https://www.dropbox.com/s/0aiheph4ov68sh9/sys_block_3_crop.png?dl=0&raw=1"></p>

4. New image data generation
<p align="center"><img src="https://www.dropbox.com/s/dt5ma39m60z9tr2/sys_block_4_crop.png?dl=0&raw=1"></p>

5. Training the CapsNet model afresh with the new dataset
<p align="center"><img src="https://www.dropbox.com/s/bn8djgwnhiunyz1/sys_block_5_crop.png?dl=0&raw=1"></p>

## Usage
Clone this repo: ``` git clone https://github.com/unforgettablexD/Ancient-Language-Handwritten-Recognition-Under-Data-Deficient-Condition.git```

# Exceution of Pickle file (hdf5, h5)
We have provided hdf5, h5 file for showing our accuracy. 
To run the pickle file to get the accuracy that we mentioned in the results. Please follow these steps.  

You need anaconda install in your system.
Then create an environment. 
Do a git clone. Go to the root folder of the project.
Then exceute this commands. 
```
conda create --name pickleenv python=3.11.5
```
```
conda activate pickleenv 
```
```
pip install -r require_pickle.txt
```


For getting the accuracy of Sanskrit run
```
python sanskrit_run_pickle.py
```
For getting the accuracy of Tamil run
```
python tamil_run_pickle.py 
```
For getting the accuracy of EMNIST run:
```
python emnist_run_pickle.py
```
# Exceution of Code 
All the datasets are already added to the code base. So no need to download. 
But, if you want to have a look at the dataset. Here are the links. 
- [Tamil dataset](https://www.kaggle.com/datasets/sudalairajkumar/tamil-nlp)
- [Sanskrit dataset](https://www.kaggle.com/datasets/ashokpant/devanagari-character-dataset/data)
- [EMNIST dataset](https://www.nist.gov/itl/products-and-services/emnist-dataset)

You need to have windows or mac. Certain laptops and OS can't run this code due to chipset and os version issue. 
It is known best to work with macOS 14.1.1 and Intel Chipset.
```
conda create --name myenv python=3.6.8
```

```
conda activate myenv 
```


```
pip install -r requirements.txt
```
To run the code for training. 
```
python main.py --cnt 190
```
here 190 is the number of training samples per class.
After training is completed you can generate new images as required. Just have to provide the count of the image (--samples_to_generate 3) 
This command generates new images:
```
python main.py -dg --save_dir emnist_bal_200/ -w emnist_bal_200/trained_model.h5 --samples_to_generate 10
```
10 here is the number of samples to generate. 

5. The following command trains the fresh CapsNet M<sub>1</sub> as illustrated in step (a):
```
python textcaps_emnist_bal.py --cnt 200
``` 
The ```cnt``` parameter specifies the number of training samples to be used. Any other custom dataset can also be used.

5. The following command generates new images as illustrated in step (b)-(d):
```
python textcaps_emnist_bal.py -dg --save_dir emnist_bal_200/ -w emnist_bal_200/trained_model.h5 --samples_to_generate 10
``` 
Any arbitrary number of new data samples can be generated by specifying the ```samples_to_generate``` parameter.


## Results

We trained our model on 190 training samples per class across different datasets and compared our results with the state-of-the-art accuracies as shown in Table 2. Despite the limited number of training samples, our model achieved comparable accuracy to these state-of-the-art models.

In particular, for the Sanskrit dataset, our model closely matched the state-of-the-art with an accuracy of 95.27%. For EMNIST-Digits, we showed the robustness of our model by nearly matching the state-of-the-art accuracy. In the Tamil dataset, our model achieved a remarkable 95.86% accuracy.

### Handwritten Character Recognition

Here's how our model's performance compares to the current state-of-the-art:

| Dataset       | State-of-the-Art Model Accuracy (Full training set) | Our Model (190 Samples/Class) |
|---------------|-----------------------------------------------------|------------------------------|
| Sanskrit      | 98.47% (Acharya et al., 2015)                       | 95.27%                       |
| EMNIST-Digits | 99.79% (Dufoorq & Bassett, 2017)                    | 99.64%                       |
| Tamil         | 98.04% (Ulaganathan et al., 2020)                   | 95.86%                       |

Our approach demonstrates that it is feasible to train accurate models for ancient language character recognition with very small datasets.


## Contact
For inquiries and further information, please contact [kumararn@usc.edu].

Discussions, suggestions, and questions are welcome!
