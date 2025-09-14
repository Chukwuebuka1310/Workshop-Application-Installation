# Installation Process For Aurora Core Workshop

## Overview
Robotics is the fusion of engineering, computer science, and artificial intelligence to create machines that sense, decide, and act in the real world. From industrial automation to autonomous vehicles and healthcare systems, robots are transforming the way we live and work

To build these intelligent systems, developers rely on many powerful tools, which include but are not limited to:

* Robot Operating System 2(ROS2)\
ROS 2 provides the essential framework for communication and modular software development, ensuring that different robot components work seamlessly together

* Gazebo\
A powerful 3D simulator, enables researchers and engineers to test algorithms, sensor data, and robot behaviors in safe, realistic virtual environments before implementation on hardware. Condering the cost of hardwares used for these machine can be expensive, this simulator give the engineer the ability see his machine(Robots) function in real time.

* RViz\
A visualization tool integrated with ROS 2, allows developers to interpret robot states, sensor readings, and navigation paths, providing valuable insights for debugging and performance analysis

Hence, the process of installing each of these application is what I will explaining. 

Please note that the installation of all these application differs for the different operating system, and my installation focuses on the Windows Subsystem Linux(ubuntu noble 24.04LTS). 

Howerver, if you need to install for a differnt operating system, then you might want to visit their documentaion page which I will drop for each application

## Pre-requisites
Ubuntu noble - Installation are done in the ubuntu terminal\
Good network - Make installation faster.

### INSTALLATION 1: Robot Operating System 2

For some reasons, the two ubuntu version have differnt ROS2 they can install. For the V24.04, it is expected that you install Jazzy Jalisco and for V22.04, Humble Hawksbill.

In this intallation we stick with V24.04 because that my present version but the process remain the same for both

* System Setup:

<pre>local</pre>

The above indicated checks if you have a local that support utf8. If you do you get a response like:

<pre>LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=</pre>

if you do not, then run this: 

<pre>sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8</pre>

Then check again to see you get the response above. if you do then proceed to the next step.

* Enable required repositories
Before installing ROS 2, you first make sure that the Universe repository (which contains community-maintained packages required by ROS 2) is enabled on your Ubuntu system.

To do this, run

<pre>sudo apt install software-properties-common
sudo add-apt-repository universe</pre>

then, run

<pre>sudo apt update && sudo apt install curl -y
export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')
curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo $VERSION_CODENAME)_all.deb" # If using Ubuntu derivates use $UBUNTU_CODENAME
sudo dpkg -i /tmp/ros2-apt-source.deb</pre>


* Install

Update the apt repository caches, run
<pre>sudo apt update</pre>

Update system for installing new packages, run
<pre>sudo apt upgrade</pre>

Deskstop install, run
<pre>sudo apt install ros-jazzy-desktop</pre>

Installation Complete

🔗 For humble installation: [ROS2 Humble Hawksbill](https://docs.ros.org/en/humble/Installation.html)\
🔗 For jazzy installation: [ROS2 Jazzy Jaliscol](https://docs.ros.org/en/jazzy/Installation.html)

### INSTALATION 2: Gazebo
Since you have installed ROS2, its pretty straigh forward to install Gazebo, just like the ROS2 and ubuntu, the one installed for ROS2 Jazzy Jalisco is Gazebo Harmonic, and it's different for v22.04

🔗 To know which Gazebo version compactible to your ROS2 version: [Gazebo version compactibility](https://gazebosim.org/docs/latest/ros_installation)

First, install some nececessary and required tool for the function of the application, run:
<pre>sudo apt-get update
sudo apt-get install lsb-release gnupg</pre>

Install Gazebo Harmonic
<pre>sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] https://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install gz-ionic</pre>

To launch, run
<pre>gz sim shapes.sdf</pre>

Installation complete. 🎉🎉🎉

Note: Its prefered that you run the snippet line by line, so that you can detect any issue during the installation.

### INSTALLATION 3: RViz
Due to the fact that we installed the full package of ROS2, RViz has been installed.


🎉🎉🎉🎉🎉CONGRATULATIONS, YOU HAVE SUCCESSFULLY INSTALLED ALL REQUIRED APPLICATION FOR THE WORKSHOP 🎉🎉🎉🎉🎉.
