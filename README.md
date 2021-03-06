
# tensorflow-no-avx

TensorFlow compiled on CPU without AVX

# tensorflow 1.14.0 (2019.08.20)

| Field             | Value       |
|-------------------|-------------|
| Date:             | 2019.08.20  |
| Tensorflow:       | 1.14.0      |
| Python:           | 3.7.4       |
| System:           | Linux Mint 19.2 "Tina" 64bit |
| Kernel:           | 5.0.0-25-generic x86_64 |
| CPU:              | Intel® Core™ i5 CPU M 430 @ 2.27GHz × 4 |
| Size:             | ~82MB       |
| Link:             | [https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl](https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl) |
| GCC:              | gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1) |
| Compilation Time: | ???         |

# tensorflow 1.14.1 (2021.01.17)

| Field             | Value       |
|-------------------|-------------|
| Date:             | 2021.01.17  |
| Tensorflow:       | 1.14.1      |
| Python:           | 3.7.9       |
| System:           | Linux Mint 20.0 "Ulyana" 64bit |
| Kernel:           | 5.8.0-36-generic x86_64 |
| CPU:              | Intel® Core™ i5 CPU M 430 @ 2.27GHz × 4 |
| Size:             | ~114MB      |
| Link:             | [https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl](https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl) |
| GCC:              | gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04) |
| Compilation Time: | 28284s (~7.8h) (jobs:2) |

---

Added to list [tensorflow-community-wheels](https://github.com/yaroslavvb/tensorflow-community-wheels) as 
- [Issue 135: Tensorflow 1.14.0, CPU, no CUDA, no AVX, Python 3.7.4, Linux Mint 19.2 "Tina" 64bit (based on Ubuntu 18.04)](https://github.com/yaroslavvb/tensorflow-community-wheels/issues/135)
- [Issue 178: Tensorflow 1.14.1, CPU, no CUDA, no AVX, Python 3.7.9, Linux Mint 20.0 "Ulyana" 64bit (based on Ubuntu 20.04)](https://github.com/yaroslavvb/tensorflow-community-wheels/issues/178)

---

# Installation
    
### 2020.05.05

Originally `.whl` was on `Git LFS` ([Git Large File Storage (LFS)](https://git-lfs.github.com/)) and you could install it from GitHub 
`bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl` but `Git LFS` has limitations for free users so I had to put `.whl` on private server.

**Install directly from server:**

```
pip3 install https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl

pip3 install https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl
```

**Download and later install from local file:**

download:

- [https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl](https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl)

- [https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl](https://furas.pl/projects/tensorflow-no-avx/bin/tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl)

install:

```
pip3 install tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl

pip3 install tensorflow-1.14.1-cp37-cp37m-linux_x86_64.whl
```

### 2021.01.14

More information about compilation and installation in file [NOTES.md](NOTES.md)

---

