目前在centos7.1测试通过

开始编译
""""""""""""""""""""
git clone https://github.com/baidu/bigflow.git

cd bigflow/build_support

sh build_deps.sh

source ./environment

mkdir -p ../build && cd ../build && cmake ..

make

make release

On Docker编译指南
"""""""""""""""""""

::
    
    git clone https://github.com/baidu/bigflow.git
    cd bigflow
    docker run -i -t -v $PWD:/root/bigflow centos:7.1.1503 bash

进入docker环境会，执行：::

    export MAKEFLAGS='-j 4'
    yum install sudo -y -q && cd /root/bigflow/build_support && sh -x build_deps.sh && source ./environment && mkdir /root/bigflow/build && cd /root/bigflow/build && cmake .. && make && make release
 
 即可完成编译，执行单测请使用：::
 
    cd /root/bigflow/bigflow_python
    sh run-tests
