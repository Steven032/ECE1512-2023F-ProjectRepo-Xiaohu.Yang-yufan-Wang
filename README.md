****This repo is for ECE1512 Project B****
**Task1**




**Task2**
<br />***The PC sysytm we use to run is Ubuntu, the GPU we use is GTX3090Ti***

<br />The first paper is "Towards Lossless Dataset Distillation via Difficulty-Aligned Trajectory Matching"
<br />***All the code related to this paper is placed in "DATM-main"***
<br />**run steps**
<br />1. Download the folder to you PC using "https://minhaskamal.github.io/DownGit/#/home" 
<br />2. Run the following in terminal to setup environment

```bash
conda env create -f environment.yaml
```
3. Activate your conda environment with
```bash
conda activate distillation
```
<br />4. Generating Expert Trajectories
Before doing any distillation, you'll need to generate some expert trajectories using ```buffer.py```

The following command will train 100 ConvNet models on MNIST with ZCA whitening for 50 epochs each:
```bash
cd buffer
python buffer_FTD.py --dataset=MNIST --model=ConvNet --train_epochs=50 --num_experts=100 --zca --buffer_path=../buffer_storage/ --data_path=../dataset/ --rho_max=0.01 --rho_min=0.01 --alpha=0.3 --lr_teacher=0.01 --mom=0. --batch_train=256
```

<br />5.Distillation by Matching Training Trajectories
The following command will then use the buffers we just generated to distill MNIST down to  10 image per class:
```bash
cd distill
python DATM.py --cfg ../configs/MNIST/ConvIN/IPC10.yaml
```
**The output can be find here in this repo once finish the above process**
 <br />DATM-main/Output 2
    
 

<br />******The second paper we pick is "Efficient Dataset Distillation using Random Feature Approximation"******
<br />***All the code related to this paper is placed in "RFAD-master"***
<br />**run steps** The following run steps are from **https://github.com/yolky/RFAD.git**
# Example usage
To run generate a distilled set on cifar10, 10 samples per class, platt loss with label learning, for example:

```python3 run_distillation.py --dataset cifar10 --save_path path/to/directory/ --samples_per_class 10 --platt --learn_labels ```

This does not automatically evaluate the dataset on the test set.

To evaluate a distilled set with NNGP/NTK kernel ridge regression with an already made distilled dataset on all datasets except celebA:
```python3 eval_distilled_set.py --dataset fashion --save_path path/to/directory --run_krr```

To evaluate a distilled set with a finite network trained with SGD on mnist, with an already made distilled dataset:

```python3 eval_distilled_set.py --dataset mnist --save_path path/to/directory --run_finite --lr 1e-3 --weight_decay 1e-3 --label_scale 8` --centering ```

To automatically load the set of training hyperparameters used for finite training results in the paper, use the command "--use_best_hypers", i.e.

```python3 eval_distilled_set.py --dataset cifar10 --save_path path/to/directory --run_finite --use_best_hypers ```

utils.py contains the best hyperparameters for finite network training

To use the empirical NNGP for inference on fashion-mnist:
```python3 run_network_parameter_analysis.py --dataset fashion --save_path path/to/directory```

To use the empirical NNGP for inference on fashion-mnist:
```python3 run_network_parameter_analysis.py --dataset fashion --save_path path/to/directory```

To run the time profiling experiment for model counts of 1,2,4,8, for samples per class in the coreset of 1,5,10,20,50:
```python3 run_time_profile_exp.py --dataset cifar10 --n_models 1 2 4 8 --samples_per_class 1 5 10 20 50```

To run corruption experiments on CelebA with corruption 0.8:
```python3 run_distillation.py --dataset celeba --save_path path/to/directory/ --samples_per_class 1 --platt --n_batches 1 --init_strategy noise --corruption 0.8```
To run CelebA experiments, make sure you are on the latest version of PyTorch, as older version have a bug where the test/train splis are incorrect.

To evaluate with NNGP KRR on CelebA:
```python3 eval_distilled_set_batched.py --dataset celeba --save_path path/to/directory --run_krr```

We additionally include some distilled dataset for cifar10 with 1,10, or 50 samples per class in ./distilled_images_final/cifar10 in the files 'best.npz'

    




