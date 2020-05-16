# 文章目录

## 前言

自己近期在学习机器学习，想要动手做一个人脸识别项目，而OpenCV是一个非常不错的开源计算机视觉和机器学习库，里面包含很多人脸检测和识别算法，并且包含很多训练好的模型，实际实践起来相对简单，很适合现阶段的学习。OpenCV支持Python、C++、Java等多种语言，基于Python环境的搭建过程比较简单（Pycharm+Anaconda+OpenCV）,本文主要记录VisualStudio下C++环境的搭建以及OpenCV相关的配置

## 配置环境

Windows10
Visual Studio 2019
OpenCV4.3.0

## 引用

1.[官网VS2019安装教程](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio?view=vs-2019)
2.[创建C++控制台程序官网教程](https://docs.microsoft.com/en-us/cpp/get-started/tutorial-console-cpp?view=vs-2019)
3.[visual studio 2019安装配置可编写c/c++语言的IDE环境](https://blog.csdn.net/digitalkee/article/details/104499579?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)  
4.[Visual Studio 与Visual C++ 有什么区别](https://blog.csdn.net/LHHopencv/article/details/76071036?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase)
5.[VS2017+opencv4.2.0环境搭建详细步骤图解](https://blog.csdn.net/qq_36915078/article/details/105378010?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

## VS2019下载与安装

- [VS官网](https://visualstudio.microsoft.com/zh-hans/downloads/)免费下载Visual Studio 2019社区版
[![Y6YFDx.md.png](https://s1.ax1x.com/2020/05/16/Y6YFDx.md.png)](https://imgchr.com/i/Y6YFDx)
- 在VS2019 installer中勾选C++组件选项，也可以修改安装路径（本机C盘是SSD,使用了默认路径，以便打开速度更快）
[![Y6ttw6.md.png](https://s1.ax1x.com/2020/05/16/Y6ttw6.md.png)](https://imgchr.com/i/Y6ttw6)
- 等待安装完毕

## OpenCV下载与安装

### 下载

- 官网下载OpenCV
    <https://opencv.org/releases/>
- 选择当前最新版本的`OpenCV-4.3.0`，点击`Windows`
![YcScrV.png](https://s1.ax1x.com/2020/05/16/YcScrV.png)

- 页面跳转，自动下载`opencv-4.3.0-vc14_vc15.exe`程序
[![YcSbqK.png](https://s1.ax1x.com/2020/05/16/YcSbqK.png)](https://imgchr.com/i/YcSbqK)

- **注意**：不同版本的OpenCV对应于不同版本的`Visual C++`，这里的`vc14_vc15`表示包含`VC++14`和`VC++15`编译后的两个版本。之所以要注意这一点是因为不同的版本的`Visual Studio`中包含不同版本的`Visual C++`。关于这两者之间的关系，可以参考[引用^[4]^](https://blog.csdn.net/LHHopencv/article/details/76071036?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase)。
- 部分`Visual Studio`与`Visual C++`版本对应关系如下表：

    | Visual Studio 版本 | Visual C++ 版本| 
    :--- |:---
    VS 6.0|VC 6.0
    VS 2013|VC 12
    VS 2015|VC 14
    VS 2017|VC 15
    VS 2019|VC 16

### 安装

- 打开下载的`opencv-4.3.0-vc14_vc15.exe`，选择安装路径，如`D:\Program Files\`
[![YcpSxI.png](https://s1.ax1x.com/2020/05/16/YcpSxI.png)](https://imgchr.com/i/YcpSxI)

- 配置环境变量，将安装文件下的`bin`文件添加到系统变量`Path`中，例如添加`D:\Program Files\OpenCV\build\x64\vc15\bin`，根据自己的安装路径调整
![YcpCsP.png](https://s1.ax1x.com/2020/05/16/YcpCsP.png)

- **注意**：选择`vc15`对应的文件夹

## 创建&配置C++项目

- 打开VS2019，选择`Create a new project`
[![YcCw5D.md.png](https://s1.ax1x.com/2020/05/16/YcCw5D.md.png)](https://imgchr.com/i/YcCw5D)

- 选择`Empty Project`
[![YcC5GQ.md.png](https://s1.ax1x.com/2020/05/16/YcC5GQ.md.png)](https://imgchr.com/i/YcC5GQ)

- 填写项目名称和存放路径
[![YcPCs1.md.png](https://s1.ax1x.com/2020/05/16/YcPCs1.md.png)](https://imgchr.com/i/YcPCs1)

- 项目配置有两种方式：
  - 一种是只配置当前项目的设置
  - 一种是配置当前用户的设置

- 以配置当前项目为例：
  - 右击`Resource Files` → `Add` → `New Item`创建`main.cpp`文件
    [![YcuBin.png](https://s1.ax1x.com/2020/05/16/YcuBin.png)](https://imgchr.com/i/YcuBin)
  - 编写简单的C++程序，并将编译平台设置为`x64`这是因为`OpenCV4.3.0`只支持`x64`
    ![Ycu4iR.png](https://s1.ax1x.com/2020/05/16/Ycu4iR.png)，
  - 右击项目名`OpenCV` → `Properties` → `VC++ Directories`
    ![YcKytA.png](https://s1.ax1x.com/2020/05/16/YcKytA.png)
  - 配置头文件包含路径，编辑`include Directories`，将目录`D:\Program Files\OpenCV\build\include`和目录`D:\Program Files\OpenCV\build\include\opencv2`加入其中
    ![YcQPaQ.png](https://s1.ax1x.com/2020/05/16/YcQPaQ.png)
  - 配置库文件路径，编辑`Library Directories`，添加目录`D:\Program Files\OpenCV\build\x64\vc15\lib`
    ![YcQWdg.png](https://s1.ax1x.com/2020/05/16/YcQWdg.png)
  - 配置链接器，回到`OpenCV Property Pages`页面，点击`Linker` → `Input`，选择右侧第一个附加依赖项`Additional Dependencies`，点击编辑
   ![YclvB8.png](https://s1.ax1x.com/2020/05/16/YclvB8.png)
  - 将文件夹`D:\Program Files\OpenCV\build\x64\vc15\lib`下的`opencv_world430d.lib`文件名加入其中（*注意：不同OpenCV版本的这个库文件编号不同，具体依据自己实际下载情况*）
    ![Yc1h2n.png](https://s1.ax1x.com/2020/05/16/Yc1h2n.png)
    opencv_world430d.lib是Debug版本的文件库，填入即可
    ![Yc1cVS.png](https://s1.ax1x.com/2020/05/16/Yc1cVS.png)

  - 点击`应用`和`确认`，重启VS2019

## 测试

- 替换`main.cpp`内容为以下测试代码：

```cpp
#include <opencv2/opencv.hpp>

using namespace std;
using namespace cv;

int main(int argc, char* argv[]) {
    const char* imagename = "****";//此处为你自己的图片路径

    //从文件中读入图像
    Mat img = imread(imagename, 1);

    //如果读入图像失败
    if (img.empty()) {
        fprintf(stderr, "Can not load image %s\n", imagename);
        return -1; 
    }
    //显示图像
    imshow("image", img);

    //此函数等待按键，按键盘任意键就返回
    waitKey();
    return 0;
}
```

- 点击`Build`→`build solution`或则`Ctrl+Shift+S`，观察编译输出的信息，没有问题选择`Debug`→`Start Debuging`或者`F5`，观察运行结果
![YcYb9g.png](https://s1.ax1x.com/2020/05/16/YcYb9g.png)

- 如果出现以上界面，说明配置成功（示例代码没有提供照片路径，需要自己添加）
