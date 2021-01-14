
Doc: [Tensorflow: Build from source](https://www.tensorflow.org/install/source)

-------------------------------------------------------------------------------

## Install bazel 

**I had to use older version to use it.**

https://docs.bazel.build/versions/master/install-ubuntu.html

```
sudo apt install curl gnupg

#curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor > bazel.gpg
#sudo mv bazel.gpg /etc/apt/trusted.gpg.d/

curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list

apt install bazel

bazel
```

## Clone code 

```
git clone https://github.com/tensorflow/tensorflow.git

cd tensorflow/

git checkout r1.14

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
