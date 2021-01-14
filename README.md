# tensorflow-no-avx

TensorFlow compiled on CPU without AVX

---

| Field       | Value       |
|-------------|-------------|
| Date:       | 2019.08.20  |
| Tensorflow: | 1.14.0      |
| Python:     | 3.7.4       |
| System:     | Linux Mint 19.2 "Tina" 64bit |
| Kernel:     | 5.0.0-25-generic x86_64 |
| CPU:        | Intel® Core™ i5 CPU M 430 @ 2.27GHz × 4 |
| Size:       | ~82MB       |
| Link:       | bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl |
| GCC:        | gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1) |

---

[Git Large File Storage (LFS)](https://git-lfs.github.com/) (doesn't use any more)

---

Added to list [tensorflow-community-wheels](https://github.com/yaroslavvb/tensorflow-community-wheels)  
as [Issue 135: Tensorflow 1.14.0, CPU, no AVX, Python 3.7.4, Linux Mint 19.2 "Tina" 64bit](https://github.com/yaroslavvb/tensorflow-community-wheels/issues/135)

### Install

```
pip3 install https://media.githubusercontent.com/media/furas/tensorflow-no-avx/master/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl
```
    
### 2020.05.05

Originally `.whl` was on `Git LFS` but it has limitations for free use so I had to put `.whl` on private server.

**Download and later install from local file:**

[https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl](https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl)

```
pip3 install tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl
```


**Install directly from server:**

```
pip3 install https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl
```

### 2021.01.14

More information about compilation and installation in file [NOTES.md](NOTES.md)

