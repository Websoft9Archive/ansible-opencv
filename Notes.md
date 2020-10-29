#  OpenCV Notes

组件名称：OpenCV 
安装文档：https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html  
配置文档: https://docs.opencv.org/master/d9/d52/tutorial_java_dev_intro.html 
支持平台： Debian家族 | RHEL家族 | Windows |macOS   

责任人：zxc

## 概要

OpenCV是一个用于图像处理、分析、机器视觉方面的开源函数库。目前，OpenCV已广泛应用于人脸识别、手势识别、人机交互、物体识别、运动跟踪等各类视觉处理领域。

## 环境要求

* 程序语言：  C++
* 应用服务器：无
* 数据库：无
* 依赖组件：opencv_contrib
* 其他：

## 安装说明

本项目采用构建源码包编译安装。

下面基于不同的安装平台，分别进行安装说明。

### CentOS  

```shell
# 安装所需依赖项
sudo yum install epel-release git gcc gcc-c++ cmake3 qt5-qtbase-devel \
    python python-devel python-pip cmake python-devel python34-numpy \
    gtk2-devel libpng-devel jasper-devel openexr-devel libwebp-devel \
    libjpeg-turbo-devel libtiff-devel libdc1394-devel tbb-devel numpy \
    eigen3-devel gstreamer-plugins-base-devel freeglut-devel mesa-libGL \
    mesa-libGL-devel boost boost-thread boost-devel libv4l-devel gtk+-devel \ 
    gimp-devel gimp-devel-tools gimp-help-browser zlib-devel libtiff-devel  \ 
    libjpeg-devel libpng-devel gstreamer-devel libavc1394-devel libraw1394-devel  \        libdc1394-devel jasper-devel jasper-utils swig python libtool nasm  \
    build-essential ant -y

    


# 克隆OpenCV和opencv_contrib存储库
mkdir ~/opencv_build && cd ~/opencv_build
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git

# 创建临时生成目录并切换到该目录
cd ~/opencv_build/opencv && mkdir build && cd build

## 使用cmake命令配置OpenCV生成
cmake3 -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_GENERATE_PKGCONFIG=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON ..

#编译安装
sudo make -j8 && make install

#测试创建jar包
cd  /root/opencv_build/opencv/samples/java/ant
vim srcSimpleSample.java
import org.opencv.core.Core;
import org.opencv.core.Mat;
import org.opencv.core.CvType;
import org.opencv.core.Scalar;
class SimpleSample {
  static{ System.loadLibrary(Core.NATIVE_LIBRARY_NAME); }
  public static void main(String[] args) {
    System.out.println("Welcome to OpenCV " + Core.VERSION);
    Mat m = new Mat(5, 10, CvType.CV_8UC1, new Scalar(0));
    System.out.println("OpenCV Mat: " + m);
    Mat mr1 = m.row(1);
    mr1.setTo(new Scalar(1));
    Mat mc5 = m.col(5);
    mc5.setTo(new Scalar(5));
    System.out.println("OpenCV Mat data:\n" + m.dump());
  }
}

ant -DocvJarDir =/root/opencv_build/opencv/build/bin   
此时,下方会多一个jar包
/root/opencv_build/opencv/samples/java/ant/bulid/jarsrcSimpleSample.java




```

### Ubuntu 

```shell
# 安装所需依赖项
sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
    gfortran openexr libatlas-base-dev python3-dev python3-numpy \
    libtbb2 libtbb-dev libdc1394-22-dev   -y

# 克隆OpenCV和opencv_contrib存储库
mkdir ~/opencv_build && cd ~/opencv_build
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git

# 创建临时生成目录并切换到该目录
cd ~/opencv_build/opencv
mkdir build && cd build

# 使用cmake命令配置OpenCV生成
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_GENERATE_PKGCONFIG=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON ..

#编译安装(j8为可选项,比如现在是告诉编译器建立8个线程)
make -j8 && make intall


```

## 路径

* 程序路径：/root/opencv_build/opencv
* 日志路径：  
* 配置文件路径：
* 其他...

##配置

无

## 账号密码


### 数据库密码

如果有数据库  
无

* 数据库安装方式：
* 账号密码：

### 后台账号

如果有后台账号
无

* 登录地址 
* 账号密码   
* 密码修改方案：最好是有命令行修改密码的方案

## 服务

本项目安装后自动生成：无服务

备注：本项目安装后自动生成服务

服务文件位置：

```

```

## 环境变量

无

## 版本号

通过如下的命令获取主要组件的版本号: 

```
# Check  OpenCV version
  pkg-config --modversion opencv4         
 
#  Check  opencv_contrib version
   python -c "import cv2; print(cv2.__version__)"     #centos
   python3 -c "import cv2; print(cv2.__version__)" 
```

## 常见问题

#### 有没有管理控制台？

无

#### 本项目需要开启哪些端口？

无

#### 有没有CLI工具？

无

## 日志

* 2020-05-12完成CentOS安装研究