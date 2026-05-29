# Thermal Map Dataset for Commercial CPU/GPU/TPU Multi/Many-Core Processors

This repository provides thermal-map datasets for training and evaluating machine learning models that predict the spatial temperature distribution of commercial processors from performance metrics, workload features, or time-series runtime signals.

The project page: [https://sheldonucr.github.io/commercial_thermal_map_dataset/](https://sheldonucr.github.io/commercial_thermal_map_dataset/)

The dataset covers the following processors:

- Intel Core i5-3337U
- Intel Core i7-8650U
- AMD Ryzen 7 4800U
- AMD Ryzen 7 7730U
- NVIDIA GeForce RTX 4060
- Google Coral M.2 TPU
- Qualcomm Snapdragon 680 (SM6225)
- AMD Ryzen AI 5 340

We will continue to expand this database with additional platforms and workloads.

The data is stored as serialized Python objects and can be read with Python's `pickle` module. Each file contains a Python dictionary with two keys: `"input"` and `"output"`. The `"input"` entry stores a 2D or 3D NumPy array containing performance metrics, workload descriptors, or other model inputs. The `"output"` entry stores a 3D array of thermal maps. The first dimension indexes the data point. For each data point, the input may be a feature vector or a time series, while the output is a 2D temperature map in degrees Celsius.

Because of GitHub file size limits, this repository includes representative samples. Complete datasets are available upon request.

## References

Lu J, Tan S X, "Thermal Map Dataset for Commercial Multi/Many Core CPU/GPU/TPU", Proceedings of the 2024 ACM/IEEE International Symposium on Machine Learning for CAD, vol. 33, pp. 1–7, 2024. DOI: 10.1145/3670474.3685963. The paper can be downloaded here: [Commercial Thermal Map Dataset.pdf](https://github.com/user-attachments/files/17787524/Commerical.Thermal.Map.Dataset.pdf)

## Related Project

[AI-Empowered Thermal Modeling and Run-Time Management for Manycore Processor and Chiplet Designs](https://vsclab.ece.ucr.edu/projects/2021/11/02/ai-empowered-thermal-modeling-and-run-time-management-manycore-processor-and)



## Intel i5-3337U & i7-8650U

Files starting with `CPU_i5` and `CPU_i7` contain data for the Intel i5-3337U and i7-8650U CPUs. Each file contains continuous recordings of CPU performance metrics and thermal maps collected under a specific workload. For each data point, the input is a feature vector and the output is a thermal map. To train a time-series model, stack performance-metric vectors from prior time points and use the corresponding thermal map as the prediction target.

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
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/figs/thermal_map_i5_3337U.png" width="400">
    <figcaption><p align="center">Fig. 1 — Thermal map of Intel i5-3337U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/figs/thermal_map_i7_8650U.png" width="400">
    <figcaption><p align="center">Fig. 2 — Thermal map of Intel i7-8650U</p></figcaption>
  </p>
</figure>

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/figs/i7_hotspot.png" width="400">
    <figcaption><p align="center">Fig. 3 — i7-8650U with temperatures at sensor and true hot spot</p></figcaption>
  </p>
</figure>


<!-- <video src="https://github.com/user-attachments/assets/0a5c6d14-5940-4c1d-82af-771f71f61019" width="100%" controls></video> -->

<!-- The video above shows the Intel i5-3337U thermal-map evolution during the FLAC workload, illustrating how the 2D temperature distribution changes over time.  -->

<!-- <video src="https://github.com/user-attachments/assets/24e2e7a4-7173-422b-b309-269cd96b8244" width="100%" controls></video> -->

<!-- The video above shows the same Intel i5-3337U FLAC workload as a 3D thermal surface, making the hot-spot intensity and spatial temperature gradients easier to inspect. -->

## AMD Ryzen 7 4800U

`CPU_R7_4800U.pkl` contains data for the AMD Ryzen 7 4800U CPU. For each data point, the input is already organized as a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 8C / 16T (Zen 2) |
| Clock speed | 1.8 / 4.2 GHz (base / boost) |
| Process node | 7 nm |
| Peak performance | ~1 TFLOP (CPU FP32, est.) |
| TDP | 15 W |

<!-- https://github.com/user-attachments/assets/65d351e7-59a4-4116-b9e8-efec81559778 -->

<!-- <video src="./figs/thermal_map_R7_4800U.mp4" width="100%" controls></video> -->

<!-- <video src="https://github.com/user-attachments/assets/4530c8a6-53b7-4b22-b7cf-edf249699f63" width="100%" controls></video> -->

<!-- The thermal map video above shows how hot spots move across cores over time. -->

<!-- https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca -->

<!-- <video src="https://github.com/user-attachments/assets/8c392588-4187-47c9-acf7-099b463f46ca" width="100%" controls></video> -->

<!-- The video above compares the thermal map with the resulting power-density map over time. -->


## AMD Ryzen 7 7730U

`CPU_R7_7730U.pkl` contains data for the AMD Ryzen 7 7730U CPU and will be added to the public sample set when available. For each data point, the input is organized as a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 8C / 16T (Zen 3 refresh) |
| Clock speed | 2.0 / 4.5 GHz (base / boost) |
| Process node | 7 nm |
| Peak performance | ~1.2 TFLOPs (CPU FP32, est.) |
| TDP | 15 W |



<!-- <video src="https://github.com/user-attachments/assets/3ab45b67-f376-4de8-b35a-6d3d0999e641" width="100%" controls></video> -->

<!-- The thermal map video above shows how hot spots move across cores over time. -->


## AMD Ryzen AI 5 340

`CPU_R_AI5_340.pkl` contains data for the AMD Ryzen AI 5 340 and will be added to the public sample set when available. This Strix Point SoC combines a 4-core/8-thread Zen 5 CPU, an integrated GPU, and a dedicated NPU on a 4 nm process. Key specifications are listed below.

| Parameter | Value |
|-----------|-------|
| CPU cores / threads | 4C / 8T (Zen 5) |
| Clock speed | ~3.0 / 4.0 GHz (base / boost, est.) |
| Process node | 4 nm (Zen 5, Strix Point) |
| NPU performance | ~50 TOPS |
| iGPU performance | ~5–6 TFLOPs (est.) |
| TDP | 28–45 W (configurable, CPU + GPU + NPU) |


<!-- <video src="https://github.com/user-attachments/assets/8a739d2f-3365-4e92-8f43-a75133d3b7ff" width="100%" controls></video> -->

<!-- The thermal map video above shows how hot spots move across cores over time for the AMD Ryzen AI 5 340. -->

<!-- <video src="https://github.com/user-attachments/assets/874c789d-00cc-4a5b-95fc-e7d4808d0a4d" width="100%" controls></video> -->


<!-- The video above shows the power-density map derived from the thermal map. -->




## NVIDIA GeForce RTX 4060

`GPU_RTX_4060.pkl` contains data for the NVIDIA GeForce RTX 4060 GPU. For each data point, the input is organized as a time series and the output is the corresponding thermal map.

| Parameter | Value |
|-----------|-------|
| CUDA cores | ~3,072 |
| Clock speed | 1.83 / 2.46 GHz (base / boost) |
| Process node | 5 nm (Ada Lovelace) |
| Peak performance | ~15–24 TFLOPs (FP32) |
| TDP | 115 W (desktop) / 35–80 W (laptop) |

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/figs/thermal_map_RTX_4060.png" width="400">
    <figcaption><p align="center">Fig. 4 — Thermal map of NVIDIA RTX 4060</p></figcaption>
  </p>
</figure>


## Qualcomm SM6225 Snapdragon 680 4G

The Qualcomm SM6225 Snapdragon 680 4G data captures thermal-map and power-density behavior for a mobile SoC workload. Key specifications are listed below.

| Parameter | Value |
|-----------|-------|
| CPU cores | 8C (4× Kryo 265 Gold / A73 + 4× Kryo 265 Silver / A53) |
| Clock speed | 2.4 GHz (A73) / 1.9 GHz (A53) |
| Process node | 6 nm (TSMC) |
| Peak performance | ~1 TOPS (Hexagon DSP) |
| TDP | ~6–8 W |

### Thermal Map Evolution

<!-- The video below shows the temporal evolution of the thermal map for the Qualcomm SM6225 Snapdragon 680 4G SoC, illustrating how on-chip temperature distributions change during workload execution. -->

<!-- <video src="https://github.com/user-attachments/assets/f6162fc7-5f25-4ce1-9a9f-9ff99ebeeb3c" width="100%" controls></video> -->

---

### Thermal Map vs. Power-Density Map

<!-- The video below compares the initial thermal map with the derived power-density map over time. Distinct hot-spot regions show the relationship between localized power dissipation and temperature rise. -->

<!-- https://github.com/user-attachments/assets/251f853d-20c0-4e65-9642-45ac84d38089 -->
<!-- <video src="https://github.com/user-attachments/assets/b0105b6f-8797-4dea-91d5-d291cb2767dc" width="100%" controls></video> -->

---

### Enlarged View of Hot-Spot Regions

<!-- The video below shows an enlarged view of the thermal map alongside the corresponding power-density map, providing finer spatial resolution of hot-spot formation and evolution over time. -->

<!-- <video src="https://github.com/user-attachments/assets/64ed355c-c11c-4b7c-9da3-8abfabf69e1c" width="100%" controls></video> -->



## Google Coral M.2 TPU

`TPU_Google_Edge.pkl` contains data for the Google Coral M.2 TPU. Because the Edge TPU is a fixed-function accelerator, this dataset uses machine-learning workload features rather than real-time performance metrics to predict runtime steady-state temperature. For each data point, the input is a workload feature vector and the output is the steady-state thermal map.

| Parameter | Value |
|-----------|-------|
| Architecture | 1× Edge TPU (ASIC) |
| Clock speed | N/A (fixed-function AI accelerator) |
| Process node | 28 nm (GlobalFoundries) |
| Peak performance | 4 TOPS (INT8) |
| TDP | ~2 W |

<figure>
  <p align="center" width="100%">
    <img src="https://github.com/sheldonucr/commercial_thermal_map_dataset/blob/main/figs/thermal_map_Google_Edge.png" width="400">
    <figcaption><p align="center">Fig. 5 — Thermal map of Google Coral M.2 TPU</p></figcaption>
  </p>
</figure>


## Citing This Dataset

If you use this dataset in your research or project, please cite the following paper:

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
