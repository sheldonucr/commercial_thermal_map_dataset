# Thermal map database
 
This repository contains datasets for training machine learning models that predict the thermal spatial distribution of chips based on their performance metrics. The data is collected on Intel i5-3337U CPU, Intel i7-8650U CPU, AMD Ryzen 7 4800U CPU, NVIDIA GeForce RTX 4060 GPU, and Google Coral M.2 TPU.

The data is stored in serialized Python object format and can be read using Python's pickle module. Each file contains a Python dictionary with two items. "input" stores a 2D/3D Numpy array representing performance metrics or other inputs for the model prediction. "output" stores a 3D array representing the thermal map data. The first dimension indicates the data point number within the dataset. For each data point, the input can either be a vector (1D) or a time series (2D), while the output is a 2D thermal map (in degrees Celsius).

Due to GitHub's file size limitations, we only store some samples here. The complete datasets are available upon request.

References:
Lu J, Tan S X, "Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU", Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD, vol. 33, pp. 1-7, 2024. 10.1145/3670474.3685963 [3670474.3685963.pdf](https://github.com/user-attachments/files/17787519/3670474.3685963.pdf)
latex citation here [Uploading acm_3670474.3685963.bib…](@inproceedings{10.1145/3670474.3685963,
author = {Lu, Jincong and Tan, Sheldon X.-D.},
title = {Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU},
year = {2024},
isbn = {9798400706998},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3670474.3685963},
doi = {10.1145/3670474.3685963},
abstract = {This paper presents a comprehensive set of datasets containing transient thermal maps of commercial multi/many-core CPU, GPU, and TPU processors. These thermal maps were obtained using a thermal IR imaging system and include data from a range of processors: Intel i5-3337U dual-core CPU, Intel i7-8650U quad-core CPU, AMD Ryzen 7 4800U 8-core CPU, NVIDIA GeForce RTX 4060 GPU, and Google Coral M.2 TPU. Additionally, we review recently proposed thermal map estimation methods developed using various Deep Neural Network (DNN) techniques, including Long Short-Term Memory (LSTM), Generative Adversarial Networks (GAN), and transformer-based models. We provide a detailed discussion and comparison of these models trained on the thermal map datasets. These datasets aim to support and stimulate advanced research in thermal map estimation and modeling within the research community.},
booktitle = {Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD},
articleno = {25},
numpages = {7},
location = {Salt Lake City, UT, USA},
series = {MLCAD '24}
})


## Intel i5-3337U & i7-8650U

Files starting with 'CPU_i5' and 'CPU_i7' contain data for the Intel i5-3337U and i7-8650U CPU. Each file corresponds to continuous recordings of CPU performance metrics and thermal maps over time under a specific task. For each data point, the input is a vector and the output is a heat map. You can stack the performance metrics data from the time points preceding a given time to form a time series for training a time series model.






## AMD Ryzen 7 4800U

CPU_R7_4800U.pkl contain data for the AMD Ryzen 7 4800U CPU.  For each data point, the input is already a time series and the output is the corresponding thermal map.

https://github.com/user-attachments/assets/65d351e7-59a4-4116-b9e8-efec81559778

## NVIDIA GeForce RTX 4060
![thermal_image_480](https://github.com/user-attachments/assets/d1285af8-aa5e-4f0e-b8c9-a608e2b373c8)

GPU_RTX_4060.pkl contain data for  NVIDIA GeForce RTX 4060 GPU. For each data point, the input is already a time series and the output is the corresponding thermal map.


## Google Coral M.2 TPU

TPU_Google_Edge.pkl contain data for the Google Coral M.2 TPU. Due to its task-specific nature, we do not use performance metrics to predict real-time temperature. Instead, we use the features of the machine learning tasks deployed on it to predict the steady-state temperature during runtime. For each data point, the input is a feature vector of the workload, and the output is the steady-state thermal map.
