# 关于Anaconda3

## 什么是Anaconda？
通过独立的虚拟环境对Python第三方包（即环境）进行管理的软件。
- 安装简单
- 开源免费
- 社区支持

## 如何安装
**for Mac**<br>
别装了。既然用了mac，还是使用服务器开发吧，况且mac存储比较金贵:)

**for Windows**<br>
1. 官网下载安装包：[传送门](https://www.anaconda.com/download)
2. 运行.exe，安装。
- Anaconda可以不装在C盘！建议选择剩余空间大于30G的磁盘（万一以后三头六臂有很多项目嘞）。
- 路径全英文！不要出现中文！
- 勾选`添加Anaconda到环境变量`
- 默认的python3.x版本无所谓勾不勾
3. 手动添加/检查环境变量
    1. 右键“此电脑” -> 属性 -> 高级系统设置 -> 环境变量
    2. 双击“Path”
    3. 添加环境变量，如果已经有了就检查一下。假设你的安装路径是`D:\Anaconda`，你需要分别添加：`D:\Anaconda`，`D:\Anaconda\Scripts`，`D:\Anaconda\Library\bin`。
 4. 测试是否安装成功
    1. 打开cmd
    2. 输入`conda -version`，能成功显示版本号即可。
    3. 输入`conda info`，能显示配置信息即可。
 5. 安装成功。

## 如何使用
1. 按`win`键，打开`Anaconda Prompt`。Anaconda Prompt可以理解为conda版的cmd，即正常cmd的功能它都有。所以以后可以告别cmd了。此时你的路径前会有一个`(base)`，它表示你目前正在默认环境下。
2. 创建一个新的环境，输入`conda create -n helloworld python=3.10`。这句话的含义是：创建一个名字为helloworld的环境，以python3.10为py版本。
3. 输入`conda activate helloworld`，前面的（base）变成了（helloworld），表示你现在已经切换到新的环境了。
4. 安装你需要的第三方库，我们以numpy为例。输入`conda install numpy`，系统会反馈即将安装的包及其依赖的版本号，如果你认为ok，就yes，完成安装。
5. 如果我们想指定版本可以`conda search numpy`，选择一个库中有的版本（以1.21为例），再运行`conda install numpy==1.21`即可。
6. 测试是否安装成功。
   1. 输入python，回车。
   2. 运行`import numpy as np`, `np.__version__`。返回1.21版本号，安装成功。

### conda install 和 pip install的区别
|              |     conda      |       pip        |
| :----------- | :------------: | :--------------: |
| 数据来源     |  Anaconda.org  |       PyPI       |
| 包的丰富度   |    常用的包    | 更新及时、更齐全 |
| 包存储的位置 | anaconda3/pkgs |    特定环境中    |
| 安全性       | 会检测依赖关系 |  环境可能会冲突  |

### 总结
1. conda install 和 pip install 效果上基本等价。
2. 尽量首选使用conda install，如果你需要的包比较冷门，退而求其次使用pip install。
3. 每个工程单独一个环境，环境名要具体体现工程内容，如：下游任务+模型名字。禁止叫'abcd'。

## 删除环境
```bash
conda remove -n helloworld --all
```
## 清理安装包
```bash
# 不会对现有环境造成影响
conda clean --all
```