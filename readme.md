Adaptive Auto Attack (AAA) — Exploration for Loop hole
Code for evaluating adversarial robustness using the Adaptive Auto Attack framework with epsilon sweeps across multiple adversarially trained models.

Step by Step Guide

Install the packages listed in the Software Installation section below.
Download the model weights and place them in the model_weights/ directory, organized by defense name (e.g., model_weights/TRADES/, model_weights/AWP/, etc.).
Prepare the test datasets under the data/ directory following the structure described in Dataset Setup.
Open Adaptive_Auto_Attack_main.py and configure the epsilon sweep values. Run the script.

Requirements:

torch>=1.7.1
torchvision>=0.8.2
numpy>=1.19.4
tqdm
pandas
easydict
Pillow

Install all dependencies using the requirements.txt

Dataset Setup
Organize the test datasets under a data/ directory as follows:
data/
├── mnist_test/
│   ├── 0/
│   ├── 1/
│   └── ...

Models
MNIST (L∞)
TRADES (SmallCNN)

Epsilon Sweep
To sweep across multiple epsilon values for a given model, modify the eps_sweep list in the __main__ block:
pythoneps_sweep = [0.1, 0.2, 0.3, 0.35, 0.4]

for eps in eps_sweep:
    main("AAA", model_name="TRADES_mnist",
         average_number=1000, eps_override=eps)
Results are saved as JSON files in the results/ directory, one per model–epsilon combination (e.g., results/TRADES_mnist_eps0p3000.json). Already-completed runs are automatically skipped.
Output Format

System Requirements
All attacks are tested on Linux with CUDA-capable GPUs
