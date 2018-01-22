<img src="https://github.com/wkentaro/labelme/blob/master/labelme/icons/icon.png?raw=true" align="right" />

labelme: Image Annotation Tool with Python
==========================================

[![PyPI Version](https://img.shields.io/pypi/v/labelme.svg)](https://pypi.python.org/pypi/labelme)
[![Travis Build Status](https://travis-ci.org/wkentaro/labelme.svg?branch=master)](https://travis-ci.org/wkentaro/labelme)
[![Appveyor Build status](https://ci.appveyor.com/api/projects/status/epxf9b6c47cw373y/branch/master?svg=true)](https://ci.appveyor.com/project/wkentaro/labelme/branch/master)
[![Docker Build Status](https://img.shields.io/docker/build/wkentaro/labelme.svg)](https://hub.docker.com/r/wkentaro/labelme)


Labelme is a graphical image annotation tool inspired by <http://labelme.csail.mit.edu>.  
It is written in Python and uses Qt for its graphical interface.


### 中文安装及使用说明

（原版英文说明见本说明下方）

#### 安装条件

- 操作系统：Ubuntu / Mac OS / Windows
- 系统上已安装Python：推荐Python3，通过[https://www.python.org/](https://www.python.org/)下载安装；也可以直接点下面对应的链接下载安装
    - Windows: [Python3](https://www.python.org/ftp/python/3.6.4/python-3.6.4.exe) / [Python2](https://www.python.org/ftp/python/2.7.14/python-2.7.14.msi)
    - Mac OS X 64位: [Python3](https://www.python.org/ftp/python/3.6.4/python-3.6.4-macosx10.6.pkg) / [Python2](https://www.python.org/ftp/python/2.7.14/python-2.7.14-macosx10.6.pkg)
- 已安装Python库：PyQt4 / PyQt5（推荐PyQt5）
    - 在Python3.5+的64-bit Linux, macOS, 32-bit / 64-bit Windows上可以直接通过命令行的`pip3 install pyqt5`安装PyQt5
    - 其他方式安装PyQt5请参见https://www.riverbankcomputing.com/software/pyqt/download5

#### 安装步骤

1. clone这个仓库，或者依次点击页面右上方的Clone or Download->Download ZIP并解压下载的ZIP文件。
2. 通过命令行（Windows下可通过Ctrl+R组合键打开“运行”窗口，输入`cmd`后回车，以打开命令行窗口）安装上一步得到的labelme文件夹，例如：
```shell
cd labelme  # 切换目录到上一步得到的labelme文件夹内
pip3 install .  # 通过python3的pip工具安装labelme
```

#### 使用说明

1. 通过在命令行输入`labelme`并回车打开标注软件（标注过程中请不要关闭命令行窗口）。
2. 单击Open按钮或者File->Open菜单打开要标注的图片。
3. 点击Create Polygons按钮后在加载得到的图片上绘制第一个标注区域的多边形轮廓线，闭合图形时在弹出的对话框中输入标签名称，点击OK确定。继续绘制以标注该图片中其余的待标注区域。
4. 如果需要修改已标注区域，可以点击Edit Polygons按钮后，单击按住待修改的标注区域内部并拖动，以移动整个多边形的位置；单击按住待修改的区域顶点并拖动，以移动该区域上的单个顶点。
5. 标注完毕后，单击Save按钮，自定义标注文件名称后保存为`[名称].json`格式的文件。默认标注文件名称与图片文件名相同（不含后缀）。
6. 重复2-5步继续标注余下的图片。

提醒：如果想要检查已标注的图片或对其进行修改，请通过Open按钮或File->Open菜单打开与该图片相应的json文件。

Requirements
------------

- Ubuntu / macOS / Windows
- Python2 / Python3
- [PyQt4 / PyQt5](http://www.riverbankcomputing.co.uk/software/pyqt/intro)


Installation
------------

There are options:

- Platform agonistic installation: Anaconda, Docker
- Platform specific installation: Ubuntu, macOS

**Anaconda**

You need install [Anaconda](https://www.continuum.io/downloads), then run below:

```bash
conda create --name=labelme python=2.7
source activate labelme
conda install pyqt
pip install labelme
```

**Docker**

You need install [docker](https://www.docker.com), then run below:

```bash
wget https://raw.githubusercontent.com/wkentaro/labelme/master/scripts/labelme_on_docker
chmod u+x labelme_on_docker

# Maybe you need http://sourabhbajaj.com/blog/2017/02/07/gui-applications-docker-mac/ on macOS
./labelme_on_docker static/apc2016_obj3.jpg -O static/apc2016_obj3.json
```

**Ubuntu**

```bash
sudo apt-get install python-qt4 pyqt4-dev-tools
sudo pip install labelme
```

**macOS**

```bash
brew install qt qt4 || brew install pyqt  # qt4 is deprecated
pip install labelme
```


Usage
-----

**Annotation**

Run `labelme --help` for detail.

```bash
labelme  # Open GUI
labelme static/apc2016_obj3.jpg  # Specify file
labelme static/apc2016_obj3.jpg -O static/apc2016_obj3.json  # Close window after the save
```

The annotations are saved as a [JSON](http://www.json.org/) file. The
file includes the image itself.

**Visualization**

To view the json file quickly, you can use utility script:

```bash
labelme_draw_json static/apc2016_obj3.json
```

**Convert to Dataset**

To convert the json to set of image and label, you can run following:


```bash
labelme_json_to_dataset static/apc2016_obj3.json
```


Sample
------

- [Original Image](https://github.com/wkentaro/labelme/blob/master/static/apc2016_obj3.jpg)
- [Screenshot](https://github.com/wkentaro/labelme/blob/master/static/apc2016_obj3_screenshot.jpg)
- [Generated Json File](https://github.com/wkentaro/labelme/blob/master/static/apc2016_obj3.json)
- [Visualized Json File](https://github.com/wkentaro/labelme/blob/master/static/apc2016_obj3_draw_json.jpg)


Screencast
----------

<img src="https://github.com/wkentaro/labelme/raw/master/static/screencast.gif" width="70%"/>


Acknowledgement
---------------

This repo is the fork of [mpitid/pylabelme](https://github.com/mpitid/pylabelme), whose development has already stopped.
