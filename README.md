# YOLOv8 Edge Inference Benchmark: PyTorch vs ONNX (FP16)

This repository contains a benchmarking script to evaluate the performance of converting a standard PyTorch YOLOv8 object detection model into an ONNX format with FP16 quantization. 

The primary goal of this project is to optimize computer vision models for **low-latency edge deployment** (e.g., CCTV nodes and real-time workplace safety monitoring systems) under constrained hardware resources.

##  Benchmark Results (CPU Environment)

To ensure accurate real-world simulation, a rigorous CPU benchmarking environment was engineered with warmup mechanisms before the final inference iterations.

| Metric | PyTorch (FP32 - Baseline) | ONNX (FP16 - Optimized) | Improvement |
| :--- | :--- | :--- | :--- |
| **Average Latency** | 139.12 ms | **118.75 ms** | **- 14.6%** |
| **Throughput (FPS)** | 7.19 FPS | **8.42 FPS** | **+ 17.1%** |
| **Model Size** | ~ 12.0 MB | **6.2 MB** | **~ 48% Smaller** |

##  Key Engineering Takeaways:
- **Real-Time Capability:** Successfully reduced single-frame inference latency, breaking the 120ms barrier on standard CPU execution.
- **Resource Efficiency:** By applying FP16 quantization and graph optimization (`onnxslim`), the model footprint was compressed to just **6.2 MB**, making it highly suitable for RAM-constrained edge devices without sacrificing detection precision.

##  How to Run
The `benchmark.py` script covers the entire pipeline: 
1. Exporting the PyTorch model to ONNX.
2. Slimming and FP16 Quantization.
3. Engine warmup routines.
4. Final latency and throughput benchmarking.
