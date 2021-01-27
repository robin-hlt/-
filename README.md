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
$ sudo rosdep init   $ rosdep update  
5、您必须在使用ROS的每个bash终端中获取此脚本的源代码。  
source /opt/ros/noetic/setup.bash    
6、环境配置  
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc  
source ~/.bashrc  
至此已经在Ubuntu20.04的系统中完整安装ROS  Noetic  
