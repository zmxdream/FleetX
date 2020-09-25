# benchmark for word2vec (tensorflow)

# 数据准备
```
sh prepare_data.sh
```

# 模式及运行方式
1. 异步

```
sh run.sh async
```
2. 同步(出core, 暂时不测)：

```
sh run.sh sync
```

# 测试
1. 准备测试路径，如果是paddlecloud任务，则需将模型结果文件下载至本地

2. 测试
```
mkdir -p evals/logs
mkdir -p evals/results
python -u eval.py --task_mode=async --checkpoint_path=output/async --result_path=evals/results
```
checkpoint_path为模型目录


# 效果要求
1. 迭代5轮，测试准确率达到0.60+
2. 迭代20轮，模型收敛，测试准确率达到0.64


# 吞吐率要求
1. 需要迭代2轮，舍弃第一轮的数据（当前观测到第一轮速度较慢），选择第二轮的吞吐数据。
2. 需统计每个节点的吞吐率，并报告所有节点的最低吞吐率、最高吞吐率、以及去除极值之后的平均值。
3. 需用均值绘制直方图
