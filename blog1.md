# Installing ROS(Robot Operating System)

From their website @ ROS.org:    

>“The Robot Operating System (ROS) is a flexible framework for writing robot software. It is a collection of tools, libraries, and conventions that aim to simplify the task of creating complex and robust robot behaviour across a wide variety of robotic platforms.”     


I am choosing to install ROS because I have an interest in automated devices.  From personal drones and manufacturing tools to the internet of things(IoT), a robust robot operating system will become more commonly required by a growing number of industries worldwide.    


All installation instructions for various platforms can be found here:

```
http://wiki.ros.org/ROS/Installation
```

I followed the general Ubuntu version found here:

```
http://wiki.ros.org/jade/Installation/Ubuntu
```

My first step was to find out what version of Ubuntu I am running on my CS50 VirtualBox.  I first tried find it by running *“uname -a”* from the command line but it didn’t give me enough information.  I then ran *“cat /etc/*-release”* from the command line and found that I am running *“Ubuntu 14.04.01 Trusty LTS”.*  The latest version of ROS supports Trusty versions of Ubuntu so I am good to go.


![Screen1](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen1.png)



Now that I know I am running Ubuntu Trusty, I know that the first step of the installation instructions is already completed.  By default, Ubuntu Trusty is already configured to allow *"restricted"* , *"universe"* , and *"multiverse"* repositories.

Next, I set up my sources.list and set up my keys using the following two commands:

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

```
```
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
```

Next, I needed to make sure my Debian package index was up to date so I ran: 

```
sudo apt-get update
```

I ended up getting some errors but they don’t look like deal breakers so I will ignore them for now.


![Screen2](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen2.png)



Next, I installed the *“Full Desktop”* version of ROS which is the recommended version.  It contains ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators, navigation and 2D/3D perception.

```
sudo apt-get install ros-jade-desktop-full
```

The package was just under 2GB.  It took about 5 minutes to download and 5 minutes to unpack and install.  There were no errors during installation and everything looks good so far:

![Screen4](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen4.png)


The next step was to initialize rosdep and then update it:

```
sudo rosdep init rosdep update
```

This enables you to “easily install system dependencies for source you want to compile and is required to run some core components in ROS”:

![Screen5](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen5.png)


Next, I performed the environmental setup. The instructions suggest that it might be *“convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched”* :

```
echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc source ~/.bashrc
```

I am not sure if I will ever need it, but I went ahead and installed **rosinstall** which is a command-line tool that allows you to “easily download many source trees for ROS packages with one command”:

 
![Screen6](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen6.png)    


![Screen7](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/screen7.png)    



That is it for the installation process.  The instructions now suggest we venture on over to  another set of instructions entitled “Tutorials”.

```
http://wiki.ros.org/ROS/Tutorials
```

I will attempt to work through some of these tutorials in the next few posts.
