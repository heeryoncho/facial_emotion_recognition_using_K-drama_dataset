# Multi-Label Facial Emotion Recognition Using Korean Drama Video Clips
This is the code for BigComp 2022 paper [Multi-label Facial Emotion Recognition Using Korean Drama Video Clips]() by 
Heeryon Cho, Woo Kyu Kang, Younsoo Park, Sungeu Chae, and Seong-joon Kim.

We constructed a novel multi-label facial emotion recognition dataset containing 38,817 colored cropped face images (64 X 64 pixels) tagged with 23 emotion labels. 

The dataset includes 19,800 images tagged with one label, 18,134 images tagged with two labels (i.e., multi-label), 875 images tagged with three labels, and 8 images tagged with four labels. 

While existing facial emotion recognition dataset predominantly captures Western (i.e., non-Asian) faces, our dataset covers various Korean (Asian) faces with wide age range, making this a valuable Asian multi-label facial emotion recognition dataset. 

The dataset can be obtained by following the "**Downloading Data**" instruction given below.

## Requirements
Our code is tested on:
* Ubuntu Ubuntu 20.04.1 LTS
* NVIDIA RTX 3090 GPU
* TensorFlow version 2.5.0
* Python 3.8

We also use [NVIDIA DALI](https://docs.nvidia.com/deeplearning/dali/user-guide/docs/index.html) library to expedite the preprocessing of data.

## Downloading Data
Please access the below link (website of Humanities Research Institute, Chung-Ang University, Seoul, South Korea) to request the dataset.
You will need to sign a user agreement to download and dataset for non-commercial research.
* [http://aihumanities.org/en/archive/datasets/?vid=2](http://aihumanities.org/en/archive/datasets/?vid=2)

## Experiments
We built three deep learning classification models (**autoencoder, CNN, ResNet50 transfer model**) and conducted three Facial Emotion Recognition (FER) experiments:
* 6 class FER (identify 1 correct emotion)
* 22 class FER (identify 1 correct emotion)
* multi-label FER (identify complex emotions; i.e., multi-label classification)

### Table 1. Three Datasets
| Dataset | 6-Class | 22-Class | Multi-label |
|---------|---------|----------|-------------|
| Train   |  10,249 |   15,840 |    31,053   |
| Validation | 1,282 |   1,980 |     3,882   |
| Test    |   1,282 |    1,980 |     3,882   |
| Total   |  12,813 |   19,800 |    38,817   |

### Table 2. Accuracy of Multi-Class Experiments (%)

| Model       | 6 Class | 22 Class |
|-------------|---------|----------|
| Autoencoder |	 66.93  |  60.56   |
| ConvNN      |  72.93  |  82.02   |
| ResNet50    |  84.24  |  83.69   |

### Table 3. Accuracy of Multi-Label Experiments with Different Thresholds (%)
| Model       |  0.1  |  0.2  |  0.3  |  0.4  |  0.5  |
|-------------|-------|-------|-------|-------|-------|
| Autoencoder |  2.19 | 19.86	| 24.06 | 18.99 | 10.56 |
| ConvNN      | 48.82 | 60.82 | 65.30 | 67.65 | 68.03 |
| ResNet50    | 71.56 | 76.46 | 73.83 | 70.02 | 64.73 |

Note that in the case of multi-label classification, we evaluated the result by setting different thresholds (0.1, 0.2, 0.3, 0.4, and 0.5) and converted the class predictions to '1' if the sigmoid output exceeded the threshold.
Then we calculated the exact match accuracy of the predicted output and the true label. 
This is a very strict measure since it does not account for partial correctness of the multi-label predictions.

## Citation
If you find this useful, please cite our work as follows:
```
@inproceedings{bigcomp2022_k-drama_FER,
  author    = {Heeryon Cho and Woo Kyu Kang and Younsoo Park and Sungeu Chae and Seong-joon Kim},
  title     = {Multi-Label Facial Emotion Recognition Using Korean Drama Video Clips},
  crossref  = {BigComp:2022},  
  pages     = {},
  year      = {2022},

```
