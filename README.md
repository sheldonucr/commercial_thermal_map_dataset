# Thermal Map Dataset for Commercial CPU/GPU/TPU Multi/Many-Core Processors

This repository contains datasets for training machine learning models that predict the thermal spatial distribution of chips based on their performance metrics. The data is collected on Intel i5-3337U CPU, Intel i7-8650U CPU, AMD Ryzen 7 4800U CPU, AMD Ryzen 7 7730U CPU, AMD Ryzen AI 5 340, NVIDIA GeForce RTX 4060 GPU, and Google Coral M.2 TPU. We will continue to expand this database going forward. Please stay tuned.

The data is stored in serialized Python object format and can be read using Python's pickle module. Each file contains a Python dictionary with two items. `"input"` stores a 2D/3D NumPy array representing performance metrics or other inputs for the model prediction. `"output"` stores a 3D array representing the thermal map data. The first dimension indicates the data point number within the dataset. For each data point, the input can either be a vector (1D) or a time series (2D), while the output is a 2D thermal map (in degrees Celsius).

Due to GitHub's file size limitations, only some samples are stored here. The complete datasets are available upon request.

### References

Lu J, Tan S X, "Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU", Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD, vol. 33, pp. 1–7, 2024. DOI: 10.1145/3670474.3685963. The paper can be downloaded here: [Commercial Thermal Map Dataset.pdf](https://github.com/user-attachments/files/17787524/Commerical.Thermal.Map.Dataset.pdf)

### Related Project

[AI-Empowered Thermal Modeling and Run-Time Management for Manycore Processor and Chiplet Designs](https://vsclab.ece.ucr.edu/projects/2021/11/02/ai-empowered-thermal-modeling-and-run-time-management-manycore-processor-and)



## Intel i5-3337U & i7-8650U

Files starting with `CPU_i5` and `CPU_i7` contain data for the Intel i5-3337U and i7-8650U CPUs. Each file corresponds to continuous recordings of CPU performance metrics and thermal maps over time under a specific task. For each data point, the input is a vector and the output is a heat map. You can stack the performance metric data from the time points preceding a given time to form a time series for training a time series model.

**Intel i5-3337U**

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 2C / 4T |
| Clock speed | 1.8 / 2.7 GHz (base / boost) |
| Process node | 22 nm (Ivy Bridge) |
| Peak performance | ~45 GFLOPS (FP64, est.) |
| TDP | 17 W |

**Intel i7-8650U**

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 4C / 8T |
| Clock speed | 1.9 / 4.2 GHz (base / boost) |
| Process node | 14 nm (Kaby Lake-R) |
| Peak performance | ~200 GFLOPS (FP32, est.) |
| TDP | 15 W |

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_i5_3337U.png" width="400">
    <figcaption><p align="center">Fig. 1 — Thermal map of Intel i5-3337U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_i7_8650U.png" width="400">
    <figcaption><p align="center">Fig. 2 — Thermal map of Intel i7-8650U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/i7_hotspot.png" width="400">
    <figcaption><p align="center">Fig. 3 — i7-8650U with temperatures at sensor and true hot spot</p></figcaption>
  </p>
</figure>


## AMD Ryzen 7 4800U

`CPU_R7_4800U.pkl` contains data for the AMD Ryzen 7 4800U CPU. For each data point, the input is already a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 8C / 16T (Zen 2) |
| Clock speed | 1.8 / 4.2 GHz (base / boost) |
| Process node | 7 nm |
| Peak performance | ~1 TFLOP (CPU FP32, est.) |
| TDP | 15 W |

<!-- https://github.com/user-attachments/assets/65d351e7-59a4-4116-b9e8-efec81559778 -->

https://github.com/user-attachments/assets/4530c8a6-53b7-4b22-b7cf-edf249699f63

The thermal map video above shows the changing hot spots across different cores over time.

<!-- https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca -->

https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca

The thermal map vs. resulting power density (heat flux map) over time, with different hotspots.


## AMD Ryzen 7 7730U

`CPU_R7_7730U.pkl` contains data for the AMD Ryzen 7 7730U CPU. For each data point, the input is already a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 8C / 16T (Zen 3 refresh) |
| Clock speed | 2.0 / 4.5 GHz (base / boost) |
| Process node | 7 nm |
| Peak performance | ~1.2 TFLOPs (CPU FP32, est.) |
| TDP | 15 W |

*(Images and videos coming soon.)*


## AMD Ryzen AI 5 340

`CPU_R_AI5_340.pkl` contains data for the AMD Ryzen AI 5 340 (to be added soon). This is a Strix Point SoC featuring a 4-core/8-thread Zen 5 CPU, an integrated GPU, and a dedicated NPU, fabricated on a 4 nm process. Key specifications are listed below.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 4C / 8T (Zen 5) |
| Clock speed | ~3.0 / 4.0 GHz (base / boost, est.) |
| Process node | 4 nm (Strix Point) |
| NPU performance | ~50 TOPS |
| iGPU performance | ~5–6 TFLOPs (est.) |
| TDP | 28–45 W (configurable, CPU + GPU + NPU) |


https://github.com/user-attachments/assets/8a739d2f-3365-4e92-8f43-a75133d3b7ff

The thermal map video above shows the changing hot spots across different cores over time for AMD Ryzen AI 5 340.

https://github.com/user-attachments/assets/874c789d-00cc-4a5b-95fc-e7d4808d0a4d

The resulting power density map from the thermal map






## NVIDIA GeForce RTX 4060

`GPU_RTX_4060.pkl` contains data for the NVIDIA GeForce RTX 4060 GPU. For each data point, the input is already a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CUDA cores | ~3,072 |
| Clock speed | 1.83 / 2.46 GHz (base / boost) |
| Process node | 5 nm (Ada Lovelace) |
| Peak performance | ~15–24 TFLOPs (FP32) |
| TDP | 115 W (desktop) / 35–80 W (laptop) |

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_RTX_4060.png" width="400">
    <figcaption><p align="center">Fig. 4 — Thermal map of NVIDIA RTX 4060</p></figcaption>
  </p>
</figure>


## Qualcomm SM6225 Snapdragon 680 4G

### Thermal and Power-Density Analysis of Qualcomm Snapdragon 680 (SM6225)

| Parameter | Value |
|-----------|-------|
| CPU cores | 8C (4× Kryo 265 Gold / A73 + 4× Kryo 265 Silver / A53) |
| Clock speed | 2.4 GHz (A73) / 1.9 GHz (A53) |
| Process node | 6 nm (TSMC) |
| Peak performance | ~1 TOPS (Hexagon DSP) |
| TDP | ~6–8 W |

#### Thermal Map Evolution
The figure below shows the **temporal evolution of the thermal map** of the Qualcomm **SM6225 (Snapdragon 680 4G)** SoC, illustrating how on-chip temperature distributions change over time under workload execution.

https://github.com/user-attachments/assets/f6162fc7-5f25-4ce1-9a9f-9ff99ebeeb3c

---

#### Thermal Map vs. Power-Density Map
This figure compares the **initial thermal map** with the corresponding **derived power-density (heat flux) map** over time.
Distinct hotspot regions are clearly observed, demonstrating the relationship between localized power dissipation and temperature rise.

<!-- https://github.com/user-attachments/assets/251f853d-20c0-4e65-9642-45ac84d38089 -->
https://github.com/user-attachments/assets/b0105b6f-8797-4dea-91d5-d291cb2767dc

---

#### Enlarged View of Hotspot Regions
An enlarged view of the thermal map is shown alongside the corresponding **power-density (heat flux) map**, providing finer spatial resolution of hotspot formation and evolution over time.

https://github.com/user-attachments/assets/64ed355c-c11c-4b7c-9da3-8abfabf69e1c



## Google Coral M.2 TPU

`TPU_Google_Edge.pkl` contains data for the Google Coral M.2 TPU. Due to its task-specific nature, we do not use performance metrics to predict real-time temperature. Instead, we use the features of the machine learning tasks deployed on it to predict the steady-state temperature during runtime. For each data point, the input is a feature vector of the workload, and the output is the steady-state thermal map.

| Parameter | Value |
|-----------|-------|
| Architecture | 1× Edge TPU (ASIC) |
| Clock speed | N/A (fixed-function AI accelerator) |
| Process node | 28 nm (GlobalFoundries) |
| Peak performance | 4 TOPS (INT8) |
| TDP | ~2 W |

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/fig/thermal_map_Google_Edge.png" width="400">
    <figcaption><p align="center">Fig. 5 — Thermal map of Google Coral M.2 TPU</p></figcaption>
  </p>
</figure>


## Citing This Dataset

If you use this dataset in your research or project, please cite it using the following BibTeX entry:

```bibtex
@inproceedings{mlcad2024commercialthermalmapdataset,
      author={Jincong Lu and Sheldon X.-D. Tan},
      title={Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU},
      booktitle={Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD},
      series={MLCAD '24},
      year={2024},
      location={Salt Lake City, Utah},
      url={https://dl.acm.org/doi/10.1145/3670474.3685963},
      doi={10.1145/3670474.3685963},
      publisher={ACM},
      address={New York, NY, USA},
}
```
