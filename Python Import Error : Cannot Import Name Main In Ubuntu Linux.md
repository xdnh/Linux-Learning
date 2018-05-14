##  ubuntu 下更新pip后发生 ImportError: cannot import name 'main'的问题解决
今天工作需要用python2的环境，由于安装的是pip 8的版本，好奇心（手贱。。。）pip版本有些低就随手将将pip更新了，刚新到pip 10版本的，没想到刚更新完就报错了，
发生 ImportError: cannot import name 'main'的问题，他报错的文件是在usr/bin/pip 的，之后就进入到那个路径下,打开对应文件。

### **首先直接说解决方案**
1. **思路**：
> 卸载pip(10.0.1)版本，恢复之前版本(8.1.1)
- pip2:
```Python
python -m pip uninstall pip
```
- pip3:
```Python
python3 -m pip uninstall pip
```
2. **实验结果图展示**:
![实验结果图](https://github.com/xdnh/Linux-Learning/raw/master/src/Screenshot%20from%202018-05-14%2015-26-32.png)
### **参考网址**
[Python Import Error : Cannot Import Name Main In Ubuntu Linux]()
### **尝试过的方案**
不好使（起码是对我来说）
- [After pip 10 upgrade on pyenv "ImportError: cannot import name 'main'" #5240](https://github.com/pypa/pip/issues/5240)
- [ubuntu 下更新pip后发生 ImportError: cannot import name 'main'的问题解决](http://www.cnblogs.com/white-the-Alan/p/8900554.html)
- [ubuntu升级pip后， ImportError: cannot import name ‘main‘](https://www.codetd.com/article/98706)

### 升级pip9.0版本
Fix for us was pinning to pip 9.03, so:
```Python
pip install --upgrade pip==9.0.3
```
instead of
```Python
pip install -U pip
```
