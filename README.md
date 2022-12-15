# PoliticGAN

## Introduction

**PoliticGAN** is a dataset of K-Politicians built with electoral posters from 1960 to 2020, provided by [Do Won Kim](https://github.com/DO-WON)([Center for Political Communication](http://cpc.snu.ac.kr/)). We experimented on StyleGAN2-ADA, GANSpace, and StarGANv2 models to inspect which neural network will be appropriate for finding facial properties that affect voters' political decision-making. Also, we find that there is lack of non-westernized facial dataset in piblic during data preparation, so this project might have significant help for who studies computer vision with multicultural values.

## Data Preparation


## pre-training용 데이터 전처리

gicho_1th_jpg to gicho_5th_jpg [45,850개]

[autocrop](https://github.com/leblancfg/autocrop) 진행

<img src="./img/bulk_w_bg.PNG">

[backgroundremover](https://github.com/nadermx/backgroundremover) 진행

<img src="./img/bulk.PNG">


## 타겟 데이터 전처리

[총 5,530개]

Candidate No. 1 and No. 2 for the Provincial Councilor at Provincial Election and Local Council Election between 2010 and 2021 [3,081]

Candidate No. 1 and 2 for the mayer of cities and counties at Provincial Election and Local Council Election in 2010, 2014 and 2018 [1,058]

Candidate No. 1 and 2 for he National Assembly in 2012, 2016, and 2020 [1,391]

<img src="./img/mayer_male.PNG">




## 설문조사 반영한 도메인 설정

| image label          | trust             |  binary           | 
| :------------------- | :----------------:| :----------------:|
| img  1               | 75.96             | 1                 |
| img  2               | 50.74             | 0                 |
| img  3               | 63.74             | 1                 |
| ...                  | ...               | ...               |

총 8개의 도메인
|competence 0 | competence 1 | dominance 0 | dominance 1 | gendertyp 0 | gendertyp 1 | trust 0 | trust 1 |
|:----------- |:-----------  |:----------- |:----------- |:----------- |:----------- |:--------|:--------|


<img src="./img/competence_1.PNG">



## StyleGAN2-ADA
[[Original Code]](https://github.com/NVlabs/stylegan2-ada-pytorch)

<img src="./img/stylegan2-ada.png">


## GANSpace
[[Original Code]](https://github.com/harskish/ganspace)

<img src="./img/ganspace (1).jpg">
<img src="./img/ganspace (2).jpg">


## StarGAN v2
[[Original Code]](https://github.com/clovaai/stargan-v2)

<img src="./img/starganv2 (1).jpg">

<img src="./img/starganv2 (2).png">

