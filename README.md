1. Project Title: Optimizing DistilBERT inference for Energy Efficiency
2. Team Members:
a. Rakene Chowdhury (rc3574)
b. Jishan Desai (jd3895)
3. Description:
The exponential growth of artificial intelligence (AI) technologies has led to an increasing reliance on transformer-based models like DistilBERT, resulting in significant computational and energy demands. This study investigates energy efficiency during inference, a critical yet underexplored phase of AI model deployment. Through the application of three optimization techniques—Post-Training Quantization (PTQ), Mixed Precision Inference, and Flash Attention—the research demonstrates the potential to reduce energy consumption while maintaining competitive performance metrics. Using the General Language Understanding Evaluation (GLUE) benchmark datasets, the study evaluates the trade-offs between energy efficiency and task-specific accuracy. Key findings reveal that Mixed Precision Inference and Flash Attention achieve substantial energy reductions without degrading performance, while PTQ can have adverse effects on energy consumption. Profiling tool, ZeusML, was employed to quantify energy usage and emissions, providing actionable insights into sustainable AI practices. These results emphasize the importance of model-level optimizations in complementing infrastructure-based strategies for achieving scalable, energy-efficient AI systems.
4. Code Repository:
All of our code to run the experiments is in Energy_EfficientBERT_Inference.ipynb.  You only need to run this notebook to reproduce our results. All the other files are graphs for this README
5. How to Run:
Run each cell in Energy_EfficientBERT_Inference.ipynb from top to bottom sequentially. This will run all experiments and produce graphs from our paper.
6. Results:
![Baseline](Baseline.png, "Baseline")
![Energy](Energy.png, "Energy")
![GLUE](GLUE.png, "GLUE")
![Throughput](Throughput.png, "Throughput")

