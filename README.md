# Thermal map database
 
This repository contains datasets for training machine learning models that predict the thermal spatial distribution of chips based on their performance metrics. The data is collected on Intel i5-3337U CPU, Intel i7-8650U CPU, AMD Ryzen 7 4800U CPU, NVIDIA GeForce RTX 4060 GPU, and Google Coral M.2 TPU.

The data is stored in serialized Python object format and can be read using Python's pickle module. Each file contains a Python dictionary with two items. "input" stores a 2D/3D Numpy array representing performance metrics or other inputs for the model prediction. "output" stores a 3D array representing the thermal map data. The first dimension indicates the data point number within the dataset. For each data point, the input can either be a vector (1D) or a time series (2D), while the output is a 2D thermal map (in degrees Celsius).

Due to GitHub's file size limitations, we only store some samples here. The complete datasets are available upon request.


## Intel i5-3337U & i7-8650U

Files starting with 'CPU_i5' and 'CPU_i7' contain data for the Intel i5-3337U and i7-8650U CPU. Each file corresponds to continuous recordings of CPU performance metrics and thermal maps over time under a specific task. For each data point, the input is a vector and the output is a heat map. You can stack the performance metrics data from the time points preceding a given time to form a time series for training a time series model.


## AMD Ryzen 7 4800U & NVIDIA GeForce RTX 4060

CPU_R7_4800U.pkl and GPU_RTX_4060.pkl contain data for the AMD Ryzen 7 4800U CPU and NVIDIA GeForce RTX 4060 GPU. For each data point, the input is already a time series and the output is the corresponding thermal map.


## Google Coral M.2 TPU

TPU_Google_Edge.pkl contain data for the Google Coral M.2 TPU. Due to its task-specific nature, we do not use performance metrics to predict real-time temperature. Instead, we use the features of the machine learning tasks deployed on it to predict the steady-state temperature during runtime. For each data point, the input is a feature vector of the workload, and the output is the steady-state thermal map.
