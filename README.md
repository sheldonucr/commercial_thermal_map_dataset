# Thermal map database for commercial CPU/GPU/TPU multi/many core processors
 
This repository contains datasets for training machine learning models that predict the thermal spatial distribution of chips based on their performance metrics. The data is collected on Intel i5-3337U CPU, Intel i7-8650U CPU, AMD Ryzen 7 4800U CPU, NVIDIA GeForce RTX 4060 GPU, and Google Coral M.2 TPU. We will continue to expend this database going forward. Please stay tuned...

The data is stored in serialized Python object format and can be read using Python's pickle module. Each file contains a Python dictionary with two items. "input" stores a 2D/3D Numpy array representing performance metrics or other inputs for the model prediction. "output" stores a 3D array representing the thermal map data. The first dimension indicates the data point number within the dataset. For each data point, the input can either be a vector (1D) or a time series (2D), while the output is a 2D thermal map (in degrees Celsius).

Due to GitHub's file size limitations, we only store some samples here. The complete datasets are available upon request.

### References: 
Lu J, Tan S X, "Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU", Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD, vol. 33, pp. 1-7, 2024. 10.1145/3670474.3685963. The paper can be download here [Commerical Thermal Map Dataset.pdf](https://github.com/user-attachments/files/17787524/Commerical.Thermal.Map.Dataset.pdf)

### Related project 

[AI-Empowered Thermal Modeling and Run-Time Management for Manycore Processor and Chiplet Designs](https://vsclab.ece.ucr.edu/projects/2021/11/02/ai-empowered-thermal-modeling-and-run-time-management-manycore-processor-and)



## Intel i5-3337U & i7-8650U

Files starting with 'CPU_i5' and 'CPU_i7' contain data for the Intel i5-3337U and i7-8650U CPU. Each file corresponds to continuous recordings of CPU performance metrics and thermal maps over time under a specific task. For each data point, the input is a vector and the output is a heat map. You can stack the performance metrics data from the time points preceding a given time to form a time series for training a time series model.

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_i5_3337U.png" width="400">
    <figcaption><p align="center">Fig.1 Thermal map of Intel i5-3337U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_i7_8650U.png" width="400">
    <figcaption><p align="center">Fig.2 Thermal map of Intel i7-8650U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/i7_hotspot.png" width="400">
    <figcaption><p align="center">Fig.3 i7-8650U with temperatures at sensor and true hot spot</p></figcaption>
  </p>
</figure>


## AMD Ryzen 7 4800U

CPU_R7_4800U.pkl contain data for the AMD Ryzen 7 4800U CPU.  For each data point, the input is already a time series and the output is the corresponding thermal map.

<!-- https://github.com/user-attachments/assets/65d351e7-59a4-4116-b9e8-efec81559778 -->

https://github.com/user-attachments/assets/4530c8a6-53b7-4b22-b7cf-edf249699f63


The thermal map video showing the changing hot spots across different cores over time. 

<!-- https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca -->

https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca

The thermal map vs resulting powert density (heat flux map) over time with different hotspots. 


## NVIDIA GeForce RTX 4060

GPU_RTX_4060.pkl contain data for  NVIDIA GeForce RTX 4060 GPU. For each data point, the input is already a time series and the output is the corresponding thermal map.

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_RTX_4060.png" width="400">
    <figcaption><p align="center">Fig.4 Thermal map of NVIDIA RTX 4060</p></figcaption>
  </p>
</figure>


## Qualcomm SM6225 Snapdragon680 4G


### Thermal and Power-Density Analysis of Qualcomm Snapdragon 680 (SM6225)

#### Thermal Map Evolution
The figure below shows the **temporal evolution of the thermal map** of the Qualcomm **SM6225 (Snapdragon 680 4G)** SoC, illustrating how on-chip temperature distributions change over time under workload execution.

<!-- Thermal map over time -->
https://github.com/user-attachments/assets/f6162fc7-5f25-4ce1-9a9f-9ff99ebeeb3c

---

#### Thermal Map vs. Power-Density Map
This figure compares the **initial thermal map** with the corresponding **derived power-density (heat flux) map** over time.  
Distinct hotspot regions are clearly observed, demonstrating the relationship between localized power dissipation and temperature rise.

<!-- Thermal map vs power density -->
https://github.com/user-attachments/assets/251f853d-20c0-4e65-9642-45ac84d38089

---

#### Enlarged View of Hotspot Regions
An enlarged view of the thermal map is shown alongside the corresponding **power-density (heat flux) map**, providing finer spatial resolution of hotspot formation and evolution over time.

<!-- Enlarged thermal and power-density maps -->
https://github.com/user-attachments/assets/64ed355c-c11c-4b7c-9da3-8abfabf69e1c



## Google Coral M.2 TPU

TPU_Google_Edge.pkl contain data for the Google Coral M.2 TPU. Due to its task-specific nature, we do not use performance metrics to predict real-time temperature. Instead, we use the features of the machine learning tasks deployed on it to predict the steady-state temperature during runtime. For each data point, the input is a feature vector of the workload, and the output is the steady-state thermal map.

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_Google_Edge.png" width="400">
    <figcaption><p align="center">Fig.5 Thermal map of Google Coral M.2 TPU</p></figcaption>
  </p>
</figure>


## Citing Commerical Thermal Map Dataset

If you use this dataset in your research or project, please cite it using the following BibTeX entry:

```bibtex
@inproceedings{mlcad2024commericalthermalmapdataset,
      author={Jincong Lu and Sheldon X.-D. Tan},
      title={Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU},
      booktitle={Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD},
      series={MLCAD '24},
      year={2024},
      location={Salt Lake City, Utah}
      url={https://dl.acm.org/doi/10.1145/3670474.3685963},
      doi={10.1145/3670474.3685963},
      publisher={ACM},
      address={New York, NY, USA},
}
