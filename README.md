# -record the mistakes I have made during my college research
# 在虚拟机VMware安装Ubuntu
步骤 官网下载Ubuntu镜像->创建新虚拟机->选择镜像->设置系统语言，用户名密码->安装完成  
问题1：Ubuntu屏幕太小  
解决方法：安装增强工具 虚拟机->安装vmware tools，如果遇到该选项是灰色的重新安装vmware tools，关闭虚拟机->设备->CD/DVD（SATA）->链接->使用物理驱动器  
问题2：安装时间太久  
解决方法：语言包和软件包的安装可以跳过，由于网络原因这部分非常耗时  
# 安装ROS
安装步骤：  
1、添加 sources.list  
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  
2、添加 keys  
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654  
3、安装  
首先，确保你的Debian软件包索引是最新的：  
sudo apt update  
sudo apt install ros-noetic-desktop-full  
4、初始化  
$ sudo rosdep init   
$ rosdep update  
5、您必须在使用ROS的每个bash终端中获取此脚本的源代码。  
source /opt/ros/noetic/setup.bash    
6、环境配置  
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc  
source ~/.bashrc  
至此已经在Ubuntu20.04的系统中完整安装ROS  Noetic  
7、安装rosinstall  
sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential  
  
踩坑1：E:不能定位软件包ros-melodic-desktop-full，一直定位不到软件包  
由于我跟着视频教学操作，视频中的Ubuntu版本与我的不同，我下载的版本是20.04，而每个Ubuntu版本都有自己的ros适配版本，详细可以查看ros官网，Ubuntu20.04的适配版是ros-noetic  
踩坑2：ros安装不成功，有包下载链接失败  
要更换下载的源，将步骤1的命令改为sudo sh -c 'echo "deb https://mirrors.tuna.tsinghua.edu.cn/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  
踩坑3：添加keys或者apt update报错  
纯属网络问题，多试几次即可  
踩坑4：安装ROS时执行到sudo rosdep init时出现sudo rosdep：找不到命令提示  
解决方法：需要输入：  
$ sudo apt install python-rosdep2  
然后输入：  
$ sudo rosdep init  
时出现错误提示：
ERROR: cannot download default sources list from:
https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/sources.list.d/20-default.listWebsite may be down.  
解决方法：输入  
$ sudo apt-get install python-rosdep python-wstool ros-melodic-ros    
踩坑5：安装完后输入roscore出现如下错误  
Resource not found: roscore  
ROS path [0]=/opt/ros/noetic/share/ros  
ROS path [1]=/opt/ros/noetic/share  
The traceback for the exception was written to the log file  
这大概是我耗时最久的问题了，我试了网上各种各样的命令，都没有解决，但通过CSDN我大概知道是安装ros的时候包没有下载完全，包括踩坑4的问题也是rosdep没有安装上，具体的可以采用输入ros+tab键来查看是否有此命令。亲测最好的解决办法就是按照安装步骤再操作一遍，而且明显发现第二次安装的时间很短，猜想是补齐了之前没有安装好的包。  
踩坑6：安装rosinstall不能定位软件包  
这个问题我没有弄清楚原因，但根据报错提示将命令中的所有python改成python3就成功了。  
