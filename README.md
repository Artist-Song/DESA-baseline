this is a desa reproduce base
citation# DESA
The official implementation of paper "[Overcoming Data and Model heterogeneities in Decentralized Federated Learning via Synthetic Anchors](https://arxiv.org/abs/2405.11525)" accepted at ICML 2024

## CIFAR10 5-agent 2-class baseline

Fixed split:

- client 0: `[0, 1]`
- client 1: `[2, 3]`
- client 2: `[4, 5]`
- client 3: `[6, 7]`
- client 4: `[8, 9]`

Labels stay as global CIFAR-10 labels `0-9`, and model outputs stay 10-way. With `--model_hetero True`, clients use `ConvNet`, `ConvNetD1`, `ConvNetD2`, `ConvNetD3`, and `ConvNetW64`.

Local smoke test:

```bash
python iterative_desa.py --dataset cifar10-5x2 --model ConvNet --model_hetero True --ipc 1 --iters 1 --inv_iters 1 --kd_iters 1 --batch 32 --save_path ./checkpoint_smoke --pretrain True --generate_image True --kd True
```

AutoDL run:

```bash
python iterative_desa.py --dataset cifar10-5x2 --model ConvNet --model_hetero True --ipc 10 --iters 100 --inv_iters 1000 --kd_iters 100 --batch 32 --save_path ./checkpoint --pretrain True --generate_image True --kd True
```

Manual Git commands:

```bash
git status
git add README.md iterative_desa.py
git commit -m "Enable heterogeneous CIFAR10 5x2 baseline"
git push
```
