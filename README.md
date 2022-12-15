# PoliticGAN

## Introduction

**PoliticGAN** is a dataset of K-Politicians built with electoral posters from 1960 to 2020, provided by [Do Won Kim](https://github.com/DO-WON)([Center for Political Communication](http://cpc.snu.ac.kr/)). We experimented on StyleGAN2-ADA, GANSpace, and StarGANv2 models to inspect which neural network will be appropriate for finding facial properties that affect voters' political decision-making. Also, we find that there is lack of non-westernized facial dataset in piblic during data preparation, so this project might have significant help for who studies computer vision with multicultural values.

## Data Preparation


### Bulk Dataset for Pre-training

| image label        | [45,850] |
| :------------------|------|
|gicho_1st           | [??] |
|gicho_2nd           | [??] |
|gicho_3rd           | [??] |
|gicho_4th           | [??] |
|gicho_5th           | [??] |


**1. Run [autocrop](https://github.com/leblancfg/autocrop) for Face Alignment and Crop to 256x256 Size**

<img src="./img/bulk_w_bg.PNG">

**2. Run [backgroundremover](https://github.com/nadermx/backgroundremover) for Concealing Party-ego**

<img src="./img/bulk.PNG">


### Target Dataset for Main Traning


| image label                                                                                                                        | [5,530] |
| :----------------------------------------------------------------------------------------------------------------------------------|---------|
|Candidate No. 1 and No. 2 for the Provincial Councilor at Provincial Election and Local Council Election between 2010 and 2021      | [3,081] |
|Candidate No. 1 and 2 for the mayer of cities and counties at Provincial Election and Local Council Election in 2010, 2014 and 2018 | [1,058] |
|Candidate No. 1 and 2 for he National Assembly in 2012, 2016, and 2020                                                              | [1,391] |


**Run [autocrop](https://github.com/leblancfg/autocrop) and [backgroundremover](https://github.com/nadermx/backgroundremover) as well**

<img src="./img/mayer_male.PNG">




## Data Split and set domain with voters' impression data 

**1. 설문조사 반영 도메인 설정**

| image label          | trust             |  binary           | 
| :------------------- | :----------------:| :----------------:|
| img  1               | 75.96             | 1                 |
| img  2               | 50.74             | 0                 |
| img  3               | 63.74             | 1                 |
| ...                  | ...               | ...               |

**2. 총 8개의 도메인으로 데이터 스플릿**

|competence 0 | competence 1 | dominance 0 | dominance 1 | gendertyp 0 | gendertyp 1 | trust 0 | trust 1 |
|:----------- |:-----------  |:----------- |:----------- |:----------- |:----------- |:--------|:--------|


<img src="./img/competence_1.PNG">


- **학습, 평가 및 검증을 위한 데이터 스플릿**

| label | train | validation | test |
|:----------- |:-----------  |:----------- |:----------- |
|Ratio | 0.8 | 0.1 |0.1 |


## StyleGAN2-ADA
[[Original Code]](https://github.com/NVlabs/stylegan2-ada-pytorch)

**1k steps on a single RTX 3090 GPU with 45,850 images (bulk dataset)**

### Generated Images *(Virtual Politicians!)*

<img src="./img/stylegan2-ada.png">

## GANSpace
[[Original Code]](https://github.com/harskish/ganspace)

I went latent space exploration with the above pre-trained StyleGAN2-ADA.

### IPA interpolation *(do not know which trait to another)*

<img src="./img/ganspace (1).jpg">
<img src="./img/ganspace (2).jpg">


## StarGAN v2
[[Original Code]](https://github.com/clovaai/stargan-v2)

Training from scratch: 나누어진 domain의 style code 학습 및 domain 간 style transfer 학습 진행

**10k steps on a single RTX 3090 GPU with 5,530 images (target dataset)**

<img src="./img/starganv2 (1).jpg">

### interpolation *(competence 0 -> dominance 1)*

<img src="./img/starganv2 (2).png">

