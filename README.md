
# 基于强化学习的伺服系统控制策略研究

# 引言介绍

这是对于论文 “Control Strategy of Speed Servo Systems Based on Deep Reinforcement Learning” 的算法实现，如果想获取更多的信息，可以跳转到[链接](https://kolbey.github.io/2023/07/06/rl-pid-control/)查看。

# 传统的PID控制

传统的PID控制策略无需训练

```bash
python run.py --choose_model class_pid --curve_type trapezoidal --height 1000 --run_type test
```

画出结果曲线:

```bash
python plot_result.py --choose_model class_pid --curve_type trapezoidal --height 1000 --run_type test
```

<div align=center>
    <span class='gp-n'>
        <img src='https://github.com/kolbey/RL-PID-Servo-Control/blob/main/results/ChooseModel_class_pid_CurveType_trapezoidal_Height_1000_DumpSystem_False_RunType_test/ecValues.png' width="250" alt="ecValues"/>
        <img src='https://github.com/kolbey/RL-PID-Servo-Control/blob/main/results/ChooseModel_class_pid_CurveType_trapezoidal_Height_1000_DumpSystem_False_RunType_test/iaeValues.png' width="250" alt="iaeValues"/>
        <img src='https://github.com/kolbey/RL-PID-Servo-Control/blob/main/results/ChooseModel_class_pid_CurveType_trapezoidal_Height_1000_DumpSystem_False_RunType_test/radValues.png' width="250" alt="radValues"/>
    </span>
</div>


# 基于强化学习方法的PID参数整定控制策略

基于DDPG算法训练智能体自适应的对PID参数进行整定

```bash
python run.py --choose_model search_pid_parameter --curve_type trapezoidal --height 1000 --run_type train
```

实验过程曲线:

<div align=center>
    <span class='gp-n'>
        <img src='https://github.com/kolbey/RL-PID-Servo-Control/blob/main/results/ChooseModel_search_pid_parameter_CurveType_trapezoidal_Height_1000_DumpSystem_False_RunType_train/reward.PNG' width="500" alt="epRewards_fig"/>
    </span>
</div>


# 基于强化学习方法的PID电流补偿控制策略

训练

```bash
python run.py --choose_model search_electric --curve_type trapezoidal --height 1000 --run_type train
```

测试

```bash
python run.py --choose_model search_electric --curve_type trapezoidal --height 1000 --run_type test
```

画出结果曲线:

```bash
python plot_result.py --choose_model search_electric --curve_type trapezoidal --height 1000 --run_type train
```

曲线展示如下:

<div align=center>
    <span class='gp-n'>
        <img src='https://github.com/kolbey/RL-PID-Servo-Control/blob/main/results/ChooseModel_search_electric_CurveType_trapezoidal_Height_1000_DumpSystem_False_RunType_train/epRewards.png' width="500" alt="epRewards"/>
    </span>
</div>


# 库包依赖

- tensorflow-gpu==1.14.0
- atari-py==0.2.6
- gym==0.17.3
- numpy==1.91.3

具体的库包依赖可以参看 `requirements.txt` 
