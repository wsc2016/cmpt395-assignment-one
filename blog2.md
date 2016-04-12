# Creating A Workspace & An ROS Package

<hr>
`ARTICLE 1 - Part A`

After successfully installing ROS, I am going to attempt to create an ROS package following one of their tutorials on their site at:

```
http://wiki.ros.org/ROS/Tutorials/CreatingPackage
```

The tutorial offers two methods for creating packages but I arbitrarily chose to create my ROS package using rosbuild rather than catkin because ROS suggest that it may be the simpler method.

![Scr4](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr4.png)
  
Our first step in creating an ROS package is navigating to our home directory.  Our custom package will depend on common ROS packages such as std_msgs, roscpp, and rospy so all we have to do type in the following command:

```
roscreate-pkg beginner_tutorials std_msgs rospy roscpp
```

I experienced a warning telling me to update my ROS_PACKAGE_PATH environment variable.

![Scr1](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr1.png)

My first inclination was to see what directory is in the ROS_PACKAGE_PATH variable by using this command:

```
echo $ROS_PACKAGE_PATH
```

I then checked to see if my package could be found by ROS and it told it was not able to.

![Scr2](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr2.png)

In the rosbuild instructions, it states that I can navigate to my set ROS_PACKAGE_PATH simply by typing:

```
roscd
```

I navigate to my set directory and attempt to recreate my package but I get a permission denied warning.

![Scr3](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr3.png)

I attempted to sudo my way out of this but still no joy.

![Scr5](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr5.png)

It’s at this point that I will pause this tutorial on how to create a package and try to resolve this permissions issue by setting up my workspace.


<hr>
`ARTICLE 2`

I am now going to setup a simple workspace for my ROS projects.  The instructions here aren’t clear but it’s telling me to run this command to create my workspace:

```
rosws init ~/fuerte_workspace /opt/ros/fuerte
```

I received an error because I am actually running the jade version of ROS and not fuerte so I need to account for this. 

But first, I need to download and install rosw, which is part of the rosinstall package.  The following command downloads it using the Ubuntu package manager:

```
sudo apt-get install python-rosinstall
```

![Scr6](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr6.png)





Now, in my ROS directory, I can finally run this corrected command to create my workspace:

```
rosws init ~/jade_workspace /opt/ros/jade
```

![Scr7](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr7.png)

So far so good.  Next, I need to create a sandbox directory for new packages.  According to ROS, a sandbox directory can be a convenient way to store packages without having to run additional rosws commands.

I created a new directory called sandbox and added it to the hidden .rosinstall file using rosws:

```
mkdir ~/jade_workspace/sandbox

rosws set ~/jade_workspace/sandbox
```

I received an error but I don’t think it’s a deal breaker at this point so I’m not going to worry about it at this point.

![Scr8](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr8.png)

Apparently, every time entries in the workspace change, it is necessary to re-source our setup.bash to make sure that the updated ROS_PACKAGE_PATH is used:

```
source ~/jade_workspace/setup.bash
```


<hr>
`ARTICLE 1 - Part B`

To finish creating my package, I need to change over to my sandbox directory:

```
cd ~/jade_workspace/sandbox
```

I try to create my package again and I am still getting that same error!

![Scr10](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr10.png)

It looks like it still made my package but I need to make sure.

![Scr11](https://raw.githubusercontent.com/wsc2016/cmpt395-assignment-one/master/images/scr11.png)

It looks like my package has been created even though I am getting recurring errors that are not covered in the tutorial documentation.  This has been a frustrating experience to say the least and gives me the impression that ROS is very much a work in progress in need of contributors.

I hope to be able to help in the future as I get a better understanding of the project.
