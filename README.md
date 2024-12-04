1. Project Title: Optimizing LLM inference for Energy Efficiency
2. Team Members:
a. Rakene Chowdhury (rc3574)
b. Jishan Desai (jd3895)
3. Goal/Objective:
The primary goal of this project is to optimize the inference process of Large Language Models to improve energy efficiency while maintaining high performance. Due to the computationally intensive nature of LLMs, this project aims to reduce energy consumption, which will contribute to sustainability and lower the cost of large-scale deployment. We will explore and evaluate various optimization techniques targeting different phases of model inference, including computational efficiency, memory usage reduction, and improved hardware utilization. These optimizations are expected to unlock significant energy savings and performance improvements without compromising model accuracy or response time.
4. Challenges:
● Energy Profiling Issues:
○ There are no set correct tools for energy profiling. Due to this, we might be using multiple energy profilers. Which introduces imprecise or different measurements might make it difficult to track energy efficiencies and optimization results.
○ Many energy profiling tools provide energy usage data at a high level, such as total energy consumption. This can make it difficult to precisely identify which specific part of the model is responsible for the most energy usage.
● Precision and Performance tradeoffs: While applying Mixed Precision Inference, can reduce compute time and memory usage. It may lead to precision loss, and we are not aware about what are acceptable trade-offs for different LLM tasks.
● Scalability of the Optimizations: optimization may work well on DistilBERT but scaling to larger LLMs like GPT-3 or LLaMa can be very complex.
● Generalization for various tasks : Optimizations may not generalize across different LLM tasks.Finding the right balance that works well across various use cases without significant degradation can be difficult.
5. Approach and Performance Optimization Techniques to be used:
Our approach to improving DistilBERT's energy efficiency involves a combination of advanced performance optimization techniques aimed at reducing both computational complexity and power consumption without compromising accuracy. Here’s a more detailed breakdown of the key methods we are employing:
● Mixed Precision Inference: This technique involves using both 16-bit (half-precision) and 32-bit (full-precision) floating-point calculations. By performing most operations in half-precision while retaining critical calculations in full-precision, can significantly reduce the computational load and memory usage.
● Post-Training Quantization: After training, quantization reduces the precision of weights and activations from 32-bit to lower bit-widths (e.g., 8-bit). This technique lowers memory use and boosts inference speed, especially on resource-limited edge devices, while calibration helps maintain performance close to the original.
● KV-Cache Optimization: By leveraging key-value caching during the attention computation, we avoid redundant recalculations in transformer-based models like DistilBERT. This
optimization is particularly effective in scenarios involving sequence generation tasks, such as text generation, where previous key-value pairs can be reused during the decoding phase. This not only speeds up inference but also significantly reduces the energy cost per prediction by eliminating unnecessary computations.
● Advanced Attention Mechanisms: If time permits, we plan to explore efficient variations of the self-attention mechanism, such as Flash and Flex attentions, to reduce the complexity of self-attention in long sequences. This optimization may lower computational demands while preserving model accuracy.
Collectively, these techniques create a synergistic effect, resulting in a model that performs nearly identically to the original DistilBERT in terms of accuracy but with substantial improvements in energy efficiency. Our approach targets both the hardware and algorithmic layers to ensure that the model is optimized for real-world deployment, particularly in environments where resource constraints are a priority, such as mobile devices and data centers.
6. Implementation Details:
For our computing setup, we intend to prototype on Columbia's Terremoto cluster and use GCP for running the actual benchmarks to conserve cloud credits. On the hardware side, we plan to perform inference on a single NVIDIA T4 GPU. On the software side, we will begin with Hugging Face's open-source DistilBERT model. Then incorporate optimized Python and C libraries as needed.
We will use the GLUE Benchmark to evaluate the performance of DistilBERT across various natural language understanding tasks, assessing its accuracy and generalization. To measure the model's energy efficiency, we will utilize profilers such as NVIDIA Nsight Systems, PyTorch Profiler, and nvidia-smi to monitor GPU utilization and power consumption, while Zeus and PyJoules will help us track overall energy efficiency metrics throughout model inference. There will be 2 sets of metrics used to measure the improvements:
● Performance Metrics: GLUE Score
● Energy Metrics: Total energy consumption, Energy per token generation, Component
level energy (if applicable) and Energy consumption per inference
7. Demo Planned:
Our demo will include a PowerPoint presentation covering the DistilBERT use case, model architecture, the optimizations we've made, and our results. We'll demonstrate that the model's performance remains identical or nearly identical to the original, but with significant energy savings.
8. References:
● 5 Ways to Reduce your AI Energy Footprint:
https://blog.purestorage.com/purely-educational/5-ways-to-reduce-your-ai-energy-footprint/
● Offline Energy-Optimal LLM Serving: https://arxiv.org/html/2407.04014v1
● MELODI: https://arxiv.org/html/2407.16893v1
● DistilBERT: https://arxiv.org/abs/1910.01108
● GLUE Benchmark: https://gluebenchmark.com/
● KV-Cache: https://arxiv.org/pdf/2211.05102
● Flash Attention: https://modal.com/blog/flash-attention-article