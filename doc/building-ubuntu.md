## Building Seastar on Ubuntu

### Building seastar on Ubuntu 14.04/15.10/16.04

Installing required packages:
```
sudo ./install-dependencies.sh
```

To compile Seastar explicitly using gcc 5, use:
```
CXX=g++-5 ./cooking.sh -i c-ares -i fmt -t Release
ninja -C build
```


### Building seastar on Ubuntu 18.04

Installing required packages:
```
sudo apt update
sudo apt install git build-essential libtool m4 automake gcc-8 g++-8
git clone --recursive https://github.com/scylladb/seastar.git
cd seastar
sudo ./install-dependencies.sh
```

To compile Seastar (with DPDK, explicitly using gcc 8), use:
```
./configure.py --mode=dev --cook fmt
CXX=g++-8 ./cooking.sh -- -DSeastar_DPDK=ON
CXX=g++-8 ninja -j4 -C build
```
