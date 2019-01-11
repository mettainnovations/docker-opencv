FROM mettainnovations/ubuntu-base:16.04-cuda10.0

RUN mkdir -p /home/developer
ENV HOME /home/developer
WORKDIR /home/developer

# Download and Install OpenCV
RUN git clone https://github.com/opencv/opencv_contrib.git && \
    cd opencv_contrib && \
    git checkout 3.4.3 && \
    cd .. && \
    git clone https://github.com/opencv/opencv.git && \
    cd opencv && \
    git checkout 3.4.3 && \
    git submodule init && \
    git submodule update && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DWITH_QT=YES -DWITH_OPENMP=YES -DWITH_CUDA=YES -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules -DCMAKE_CXX_FLAGS="-Wno-deprecated-declarations" -DCUDA_ARCH_BIN="30 35" -DCUDA_TOOLKIT_ROOT_DIR=/usr/local/cuda-10.0 .. && \
    make -j4 && \
    make install 
