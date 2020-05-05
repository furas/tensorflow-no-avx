
Doc: [Tensorflow: Build from source](https://www.tensorflow.org/install/source)

-------------------------------------------------------------------------------

## install bazel 
# I had to use older version to use it.
curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
apt install bazel
bazel

-------------------------------------------------------------------------------

git clone https://github.com/tensorflow/tensorflow.git

cd tensorflow/

## compile code
# --jobs 2      :less jobs because CPU was to hot 
# --config=v2   :compile tensorflow 2.0 ? But it didn't work for old computer
# --config=opt  :compile for CPU (no GPU/CUDA)
#bazel build --config=v2 //tensorflow/tools/pip_package:build_pip_package --jobs 2

bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package --jobs 2

## create wheel for python

./bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

ll /tmp/tensorflow_pkg/

sudo pip3.7 install /tmp/tensorflow_pkg/tensorflow-1.14.0-cp37-cp37m-linux_x86_64.whl

-------------------------------------------------------------------------------

