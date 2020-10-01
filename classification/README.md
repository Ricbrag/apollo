# Image Classification

This folder is modified based on the pytorch classification project [original repo](https://github.com/bearpaw/pytorch-classification).

For all experiments, the recommended random seeds are in {1, 101, 8191, 65537, 131071, 524287, 6700417}.

## CIFAR-10 Experiments
### SGD
#### milestone decay
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 164 \
    --opt sgd --lr 0.1 --opt_h1 0.9 --weight_decay 5e-4 \
    --lr_decay milestone --milestone 80 120 --decay_rate 0.1 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```
#### cosine annealing
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 200 \
    --opt sgd --lr 0.1 --opt_h1 0.9 --weight_decay 5e-4 \
    --lr_decay cosine --last_lr 0.0001 --decay_rate 0.1 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```
### Adam & RAdam
#### milestone decay
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 164 \
    --opt [adamw|radamw] --lr 0.001 --opt_h1 0.9 --opt_h2 0.999 --eps 1e-8 --weight_decay 5e-4 \
    --lr_decay milestone --milestone 80 120 --decay_rate 0.1 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```
#### cosine annealing
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 200 \
    --opt [adamw|radamw] --lr 0.001 --opt_h1 0.9 --opt_h2 0.999 --eps 1e-8 --weight_decay 5e-4 \
    --lr_decay cosine --last_lr 1e-6 --decay_rate 0.1 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```
For Adam-adj & RAdam-adj, change `--weight_decay` from `5e-4` to `2.5e-1`.
### Apollo
#### milestone decay
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 164 \
    --opt apollo --lr 0.5 --opt_h1 0.9 --eps 1e-4 --weight_decay 5e-4 \
    --lr_decay milestone --milestone 80 120 --decay_rate 0.1 \
    --warmup_updates 100 --init_lr 0.01 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```
#### cosine annealing
```base
python -u cifar.py --depth 110 --batch_size 128 --epochs 200 \
    --opt apollo --lr 0.5 --opt_h1 0.9 --eps 1e-4 --weight_decay 5e-4 \
    --lr_decay cosine --last_lr 0.001 --decay_rate 0.1 \
    --warmup_updates 100 --init_lr 0.01 \
    --dataset cifar10 --data_path <data path> --model_path <model path> \
    --run <run_id> --seed <random seed> 
```

## ImageNet Experiments