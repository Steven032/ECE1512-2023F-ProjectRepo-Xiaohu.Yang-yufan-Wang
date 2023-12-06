****This repo is for ECE1512 Project B****





**Task2**
<br />***The PC sysytm we use to run is Ubuntu, the GPU we use is GTX3090Ti***

<br />The first paper is "Towards Lossless Dataset Distillation via Difficulty-Aligned Trajectory Matching"
<br />***All the code related to this paper is placed in "DATM-main"***
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

<br />5.Distillation by Matching Training Trajectories
The following command will then use the buffers we just generated to distill MNIST down to  10 image per class:
```bash
python distill.py --dataset=MNIST --ipc=10 --syn_steps=20 --expert_epochs=2 --max_start_epoch=4 --zca --Iteration=1000  --lr_img=1000 --lr_lr=1e-05 --lr_teacher=0.01 --buffer_path={path_to_buffer_storage} --data_path={path_to_dataset}
```
**The output can be find here in this repo once finish the above process**
 <br />mtt-distillation-main/Output of Generating Expert Trajectories&Distillation by Matching Training Trajectories
    
 

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

<br />5.Distillation by Matching Training Trajectories
The following command will then use the buffers we just generated to distill MNIST down to  10 image per class:
```bash
python distill.py --dataset=MNIST --ipc=10 --syn_steps=20 --expert_epochs=2 --max_start_epoch=4 --zca --Iteration=1000  --lr_img=1000 --lr_lr=1e-05 --lr_teacher=0.01 --buffer_path={path_to_buffer_storage} --data_path={path_to_dataset}
```
**The output can be find here in this repo once finish the above process**
 <br />mtt-distillation-main/Output of Generating Expert Trajectories&Distillation by Matching Training Trajectories
    
 

    




