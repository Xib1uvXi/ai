# Install TensorFlow-Go

## Prerequisites

Install bazel

```shell
sudo apt-get install pkg-config zip g++ zlib1g-dev unzip python
```

[download bazel](https://github.com/bazelbuild/bazel/releases)

run the installer

```shell
chmod +x bazel-<version>-installer-linux-x86_64.sh
./bazel-<version>-installer-linux-x86_64.sh --user
```

set up environment

```shell
export PATH="$PATH:$HOME/bin"
```

You can also add this command to your ~/.bashrc or ~/.zshrc file.

install swig & python-numpy

```shell
sudo apt-get install swig python-numpy
```

## Build

download the source code

```shell
go get -d github.com/tensorflow/tensorflow/tensorflow/go
```

build the TensorFlow C library

```shell
cd ${GOPATH}/src/github.com/tensorflow/tensorflow
./configure
bazel build -c opt //tensorflow:libtensorflow.so
```

```shell
sudo cp ${GOPATH}/src/github.com/tensorflow/tensorflow/bazel-bin/tensorflow/libtensorflow.so /usr/local/lib
sudo cp ${GOPATH}/src/github.com/tensorflow/tensorflow/bazel-bin/tensorflow/libtensorflow_framework.so /usr/local/lib
```

build and test

```shell
go test github.com/tensorflow/tensorflow/tensorflow/go
```