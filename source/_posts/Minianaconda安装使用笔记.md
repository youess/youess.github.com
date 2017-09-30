---
title: Minianaconda安装使用笔记
date: 2017-09-25 17:55:38
tags: [conda, env]
---

[Minianaconda][1]就不多介绍，应该是我碰到最好的集成使用python的一个工具了，好处谁用谁知道。
*啰嗦一句就是最好的跨平台包管理工具*

1. 安装

到清华镜像站下载最新安装程序

```
# 下载
wget -c https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda-latest-Linux-x86_64.sh

# 安装按步骤安装就行
sh Miniconda-latest-Linux-x86_64.sh

# 切换清华镜像源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```

2. 使用

可能minianconda安装的python版本不符合你的胃口，换环境换版本

```
# 创建一个python3.6的python环境并且安装anaconda相关的包
conda create -n py36 python=3.6 anaconda
# 激活
source activate py36
# 退出
source deactivate
# 设置默认的环境
conda config --set core.default_env=py36
```

3. 创建虚拟环境

虚拟环境跟切换python版本环境一样

```
# 新建一个env_name，用Python3.6并安装numpy pandas等包
conda create -n env_name python=3.6 numpy pandas

# 如果不安装任何包
conda create --no-default-packages -n env_name python

# 环境切换备份
## backup
conda list --explicit > my_env_file.txt
## restore whole environment
conda create --name myenv --file my_env_file.txt
## only install all the listed packages
conda install --name myenv --file my_env_file.txt
```

4. 删除虚拟环境

```
# 删除
conda remove --name myenv --all
# 检查
conda info --envs
```

5. 记一个从YML文件安装相关包的方法

```
conda env create -f env.yml

# env.yml内容
"""
name: fast.ai

dependencies:
  - python=3.6
  - numpy
  - pandas
  - jupyter
  - matplotlib
  - pillow
  - keras==1.2.2
  - theano
  - tensorflow
  - pandas==0.19
  - scikit-learn
  - bcolz
  - sympy
"""
```

更多的请参考[官方文档][2], 以及[cheetsheet][3]

[1]: https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/
[2]: https://conda.io/docs/user-guide/tasks/use-r-with-conda.html
[3]: https://conda.io/docs/_downloads/conda-cheatsheet.pdf
