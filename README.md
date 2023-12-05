****This repo is for ECE1512 Project B****





**Task2**
<br />***The PC sysytm we use to run is Ubuntu, the GPU we use is GTX3090Ti***


<br />The second paper we pick is "Dataset Distillation by Matching Training Trajectories"
<br />***All the code related to this paper is placed in "mtt-distillation-main"***
<br />**run steps**
<br />1. Download the folder to you PC using "https://minhaskamal.github.io/DownGit/#/home" 
<br />2. Run the following in terminal to setup environment
```bash
conda env create -f requirements_11_3.yaml
```
3. Activate your conda environment with
```bash
conda activate distillation
```
<br />4. Generating Expert Trajectories
Before doing any distillation, you'll need to generate some expert trajectories using ```buffer.py```
The following command will train 100 ConvNet models on MNIST with ZCA whitening for 50 epochs each:
```bash
python buffer.py --dataset=MNIST --model=ConvNet --train_epochs=50 --num_experts=100 --zca --buffer_path={path_to_buffer_storage} --data_path={path_to_dataset}
```
    <br />4
    <br />
    <br />
    <br />
    <br />
    <br />

    




