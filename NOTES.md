
Doc: [Tensorflow: Build from source](https://www.tensorflow.org/install/source)

-------------------------------------------------------------------------------

## Install bazel 

**I had to use older version to use it.**

https://docs.bazel.build/versions/master/install-ubuntu.html


This method I could install only `1.0.0` but it needs `0.26.2` or older

```
sudo apt install curl gnupg

#curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor > bazel.gpg
#sudo mv bazel.gpg /etc/apt/trusted.gpg.d/

curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list

sudo apt update
sudo apt install bazel-1.0.0

bazel
```

Download `0.26.1` because I didn't find `0.26.2`

https://github.com/bazelbuild/bazel/releases/tag/0.26.1

https://github.com/bazelbuild/bazel/releases/download/0.26.1/bazel_0.26.1-linux-x86_64.deb

```
sudo dpkg -i bazel_0.26.1-linux-x86_64.deb
```

## Clone code 

```
git clone https://github.com/tensorflow/tensorflow.git

cd tensorflow/

git checkout r1.14
```

## Configure

It needs `bazel 0.26.2`

```
./configure
```

```
WARNING: --batch mode is deprecated. Please instead explicitly shut down your Bazel server using the command "bazel shutdown".
You have bazel 0.26.1 installed.
Please specify the location of python. [Default is /usr/bin/python]: /usr/bin/python3.7


Found possible Python library paths:
  /usr/local/lib/python3.7/dist-packages
  /usr/lib/python3/dist-packages
Please input the desired Python library path to use.  Default is [/usr/local/lib/python3.7/dist-packages]

Do you wish to build TensorFlow with XLA JIT support? [Y/n]: 
XLA JIT support will be enabled for TensorFlow.

Do you wish to build TensorFlow with OpenCL SYCL support? [y/N]: 
No OpenCL SYCL support will be enabled for TensorFlow.

Do you wish to build TensorFlow with ROCm support? [y/N]: 
No ROCm support will be enabled for TensorFlow.

Do you wish to build TensorFlow with CUDA support? [y/N]: 
No CUDA support will be enabled for TensorFlow.

Do you wish to download a fresh release of clang? (Experimental) [y/N]: 
Clang will not be downloaded.

Do you wish to build TensorFlow with MPI support? [y/N]: 
No MPI support will be enabled for TensorFlow.

Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native -Wno-sign-compare]: 


Would you like to interactively configure ./WORKSPACE for Android builds? [y/N]: 
Not configuring the WORKSPACE for Android builds.

Preconfigured Bazel build configs. You can use any of the below by adding "--config=<>" to your build command. See .bazelrc for more details.
	--config=mkl         	# Build with MKL support.
	--config=monolithic  	# Config for mostly static monolithic build.
	--config=gdr         	# Build with GDR support.
	--config=verbs       	# Build with libverbs support.
	--config=ngraph      	# Build with Intel nGraph support.
	--config=numa        	# Build with NUMA support.
	--config=dynamic_kernels	# (Experimental) Build kernels into separate shared objects.
Preconfigured Bazel build configs to DISABLE default on features:
	--config=noaws       	# Disable AWS S3 filesystem support.
	--config=nogcp       	# Disable GCP support.
	--config=nohdfs      	# Disable HDFS support.
	--config=noignite    	# Disable Apache Ignite support.
	--config=nokafka     	# Disable Apache Kafka support.
	--config=nonccl      	# Disable NVIDIA NCCL support.
Configuration finished
```

## Compile code

```
# --jobs 2      :less jobs because my CPU was to hot 
# --config=v2   :compile tensorflow 2.0 ? But it didn't work for old computer
# --config=opt  :compile for CPU (no GPU/CUDA)
# bazel build --config=v2 //tensorflow/tools/pip_package:build_pip_package --jobs 2

bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package --jobs 2
```

## Create wheel for python

```
./bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

ll /tmp/tensorflow_pkg/

sudo pip3.7 install /tmp/tensorflow_pkg/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl
```

---

**EDIT 2021**

I don't have `Python 3.7` in `Linux Mint 20` to test if it still working. 

I would have to install unofficial `Python 3.7` from repo [deadsnakes](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa)

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update

sudo apt-get install python3.7
sudo apt-get install python3.7-dev
```

And install module(s)

```
# modules for install wheel
sudo python3.7 -m pip install setuptools wheel

# modules needed in tensorflow (-U to update to the newest version)
sudo python3.7 -m pip install -U numpy

# tensorflow
sudo python3.7 -m pip install tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl
```

---

To use `contrib` you have to import it

```
import tensorflow.contrib
```

---

Use even less `CPU` with `cpulimit`

```
cpulimit -l 80 -- bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package --jobs 1
```
