Weekly activities


Week_3

Ros2 humble version installation (ubuntu_22.04)

# First of all I make sure that I have a locale which supports UTF-8

1_STEP

ros2@ros2ubuntu:$ locale LANG=en_US.UTF-8 LANGUAGE=en_US: LC_CTYPE="en_US.UTF-8" LC_NUMERIC=ko_KR.UTF-8 LC_TIME=ko_KR.UTF-8 LC_COLLATE="en_US.UTF-8" LC_MONETARY=ko_KR.UTF-8 LC_MESSAGES="en_US.UTF-8" LC_PAPER=ko_KR.UTF-8 LC_NAME=ko_KR.UTF-8 LC_ADDRESS=ko_KR.UTF-8 LC_TELEPHONE=ko_KR.UTF-8 LC_MEASUREMENT=ko_KR.UTF-8 LC_IDENTIFICATION=ko_KR.UTF-8 LC_ALL= ros2@ros2ubuntu:$ sudo apt update && sudo apt install locales [sudo] password for ros2: Sorry, try again. [sudo] password for ros2: Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:2 http://kr.archive.ubuntu.com/ubuntu jammy InRelease
Get:3 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB] Fetched 1,672 kB in 9s (178 kB/s)
Reading package lists... Done systemd-hwe-hwdb Use 'sudo apt autoremove' to remove it. 0 upgraded, 0 newly installed, 0 to remove and 143 not upgraded. ros2@ros2ubuntu:$ sudo locale-gen en_US en_US.UTF-8 Generating locales (this might take a while)... en_US.ISO-8859-1... done en_US.UTF-8... done Generation complete. ros2@ros2ubuntu:$ sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 ros2@ros2ubuntu:$ export LANG=en_US.UTF-8 ros2@ros2ubuntu:$ locale LANG=en_US.UTF-8 LANGUAGE=en_US: LC_CTYPE="en_US.UTF-8" LC_NUMERIC=ko_KR.UTF-8 LC_TIME=ko_KR.UTF-8 LC_COLLATE="en_US.UTF-8" LC_MONETARY=ko_KR.UTF-8 LC_MESSAGES="en_US.UTF-8" LC_PAPER=ko_KR.UTF-8 LC_NAME=ko_KR.UTF-8 LC_ADDRESS=ko_KR.UTF-8 LC_TELEPHONE=ko_KR.UTF-8 LC_MEASUREMENT=ko_KR.UTF-8 LC_IDENTIFICATION=ko_KR.UTF-8 LC_ALL=



2_STEP



# I add the ROS2 repository to the system. Before that I check whether the Ubuntu Universe repository is enabled or not :


ros2@ros2ubuntu:$ apt-cache policy | grep universe 500 http://kr.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages release v=22.04,o=Ubuntu,a=jammy,n=jammy,l=Ubuntu,c=universe,b=amd64 ros2@ros2ubuntu:$ sudo apt install software-properties-common Reading package lists... Done Building dependency tree... Done Reading state information... Done The following package was automatically installed and is no longer required: systemd-hwe-hwdb Use 'sudo apt autoremove' to remove it. Processing triggers for gnome-menus (3.36.0-1ubuntu3) ... Processing triggers for libglib2.0-0:amd64 (2.72.1-1) ... Processing triggers for man-db (2.10.2-1) ... ros2@ros2ubuntu:~$ sudo add-apt-repository universe Adding component(s) 'universe' to all repositories. Press [ENTER] to continue or Ctrl-c to cancel. Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:2 http://kr.archive.ubuntu.com/ubuntu jammy InRelease
Hit:3 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease Hit:4 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease Reading package lists... Done

# I add ROS2 apt repository to the system. Before I authorze the GPG key wth that apt command :

ros2@ros2ubuntu:$ sudo apt update && sudo apt install curl gnupg lsb-release Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease Hit:2 http://kr.archive.ubuntu.com/ubuntu jammy InRelease Hit:3 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease Hit:4 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease Reading package lists... Done Building dependency tree... Done Reading state information... Done 140 packages can be upgraded. Run 'apt list --upgradable' to see them. Reading package lists... Done Unpacking curl (7.81.0-1ubuntu1.4) ... Setting up libcurl4:amd64 (7.81.0-1ubuntu1.4) ... Setting up curl (7.81.0-1ubuntu1.4) ... Processing triggers for man-db (2.10.2-1) ... Processing triggers for libc-bin (2.35-0ubuntu3.1) ... ros2@ros2ubuntu:$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# I add the repository to the source list :


ros2@ros2ubuntu:~$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null


# I update caches just after setting up the repository. I use the apt command again :



ros2@ros2ubuntu:$ sudo apt update Hit:1 http://kr.archive.ubuntu.com/ubuntu jammy InRelease Hit:2 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease
Get:5 http://packages.ros.org/ros2/ubuntu jammy InRelease [4,673 B] Get:6 http://packages.ros.org/ros2/ubuntu jammy/main amd64 Packages [737 kB] Fetched 742 kB in 6s (131 kB/s)
Reading package lists... Done Building dependency tree... Done Reading state information... Done 142 packages can be upgraded. Run 'apt list --upgradable' to see them. ros2@ros2ubuntu:$ sudo apt upgrade Reading package lists... Done Building dependency tree... Done Reading state information... Done Calculating upgrade... Done The following packages have been kept back: python3-catkin-pkg python3-rosdistro python3-rospkg The following packages will be upgraded:

ros2@ros2ubuntu:~$ sudo apt upgrade Reading package lists... Done Building dependency tree... Done Reading state information... Done Calculating upgrade... Done The following packages have been kept back: Setting up gnome-shell (42.4-0ubuntu0.22.04.1) ... Processing triggers for libc-bin (2.35-0ubuntu3.1) ...

# I instal the full dektop then :


ros2@ros2ubuntu:$ sudo apt install ros-humble-desktop [sudo] password for ros2: Reading package lists... Done Building dependency tree... Done Reading state information... Done Preparing to unpack .../890-vdpau-driver-all_1.4-3build2_amd64.deb ... Unpacking vdpau-driver-all:amd64 (1.4-3build2) ... Selecting previously unselected package proj-bin. Preparing to unpack .../891-proj-bin_8.2.1-1_amd64.deb ... Unpacking proj-bin (8.2.1-1) ... Errors were encountered while processing: /tmp/apt-dpkg-install-jJpAHP/559-python3-catkin-pkg-modules_0.5.2-1_all.deb /tmp/apt-dpkg-install-jJpAHP/598-python3-rospkg-modules_1.4.0-1_all.deb /tmp/apt-dpkg-install-jJpAHP/599-python3-rosdistro-modules_0.9.0-1_all.deb E: Sub-process /usr/bin/dpkg returned an error code (1) ros2@ros2ubuntu:$ sudo apt install ros-humble-ros-base [sudo] password for ros2: Reading package lists... Done Building dependency tree... Done Reading state information... Done ros-humble-ros-base is already the newest version (0.10.0-1jammy.20220909.041039)


# I do the sourcing in th bash file :


ros2@ros2ubuntu:$ source /opt/ros/humble/setup.bash ros2@ros2ubuntu:$


# After installing all of these packages I try to code with an example: with talker, and listener commands :

![image](https://user-images.githubusercontent.com/114398078/197670316-c0f64a77-92a1-4a1a-9c78-ed92c01df9ef.png)


ros2@ros2ubuntu:$ source /opt/ros/humble/setup.bash ros2@ros2ubuntu:$ ros2 run demo_nodes_py listener

![image](https://user-images.githubusercontent.com/114398078/201555569-331e446a-a75a-49e2-bcac-b478340e0d21.png)



Week_4 Turtlesim Installtion

First I try to install turtlesim packages and update them :
ros2@ros2ubuntu:$ sudo apt update Hit:1 http://packages.ros.org/ros2/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:3 http://kr.archive.ubuntu.com/ubuntu jammy InRelease Hit:4 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease Hit:5 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease Reading package lists... Done Building dependency tree... Done Reading state information... Done 3 packages can be upgraded. Run 'apt list --upgradable' to see them. ros2@ros2ubuntu:$ sudo apt install ros-humble-turtlesim Reading package lists... Done Building dependency tree... Done Reading state information... Done ros-humble-turtlesim is already the newest version (1.4.2-1jammy.20220908.233909). ros2@ros2ubuntu:~$ sudo apt install ros-humble-turtlesim Reading package lists... Done Building dependency tree... Done Reading state information... Done ros-humble-turtlesim is already the newest version (1.4.2-1jammy.20220908.233909). ros-humble-turtlesim set to manually installed.

And I check whether the turtlesim packages is enabled or not :
ros2@ros2ubuntu:$ ros2 pkg executables turtlesim turtlesim draw_square turtlesim mimic turtlesim turtle_teleop_key turtlesim turtlesim_node ros2@ros2ubuntu:$

After successfull done I try to run and see the turtle appears on the screen :
ros2@ros2ubuntu:~$ ros2 run turtlesim turtlesim_node Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway. [INFO] [1665882085.889021444] [turtlesim]: Starting turtlesim with node name /turtlesim [INFO] [1665882085.910151013] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]

![image](https://user-images.githubusercontent.com/114398078/201555606-1fce8dd9-36a6-4632-b19d-e0ecefaa9e91.png)


ros2@ros2ubuntu:~$ ros2 run turtlesim turtle_teleop_key Reading from keyboard
Use arrow keys to move the turtle. Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation. 'Q' to quit.


https://user-images.githubusercontent.com/115865095/196013170-d9d46737-28ed-4296-b1a0-06b655e7a51f.webm

![image](https://user-images.githubusercontent.com/114398078/201555735-30ecbbf7-da03-42e4-8ae0-8e24e18812a2.png)



I do some update and try to run RQT using rqt command :
ros2@ros2ubuntu:$ sudo apt update [sudo] password for ubuntu: Hit:1 http://packages.ros.org/ros2/ubuntu jammy InRelease Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease Hit:3 http://kr.archive.ubuntu.com/ubuntu jammy InRelease Hit:4 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease Hit:5 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease Reading package lists... Done Building dependency tree... Done Reading state information... Done 56 packages can be upgraded. Run 'apt list --upgradable' to see them. ros2@ros2ubuntu:$ ros2@ros2ubuntu:~$ sudo apt install nros-humble-rqt* Reading package lists... Done Building dependency tree... Done Reading state information... Done ros-humble-rqt-bag is already the newest version (1.1.3-2jammy.20220909.040110). ros2@ros2ubuntu:$ rqt


![image](https://user-images.githubusercontent.com/114398078/201555776-4b564ea3-c83e-4379-961c-8125c129136c.png)

As you can see I did some expression I mean I added new coordinates for the turtle to spawn at, x float 1.0, and y float 1.0 like that :

![image](https://user-images.githubusercontent.com/114398078/201555830-dae19e17-116a-4871-890a-f14794792fc3.png)

Week_5

Creating a simple publisher and subscriber (python)

Step_1 : Create a package

ros2 pkg create --build-type ament_python py_pubsub


![image](https://user-images.githubusercontent.com/114398078/201555868-4a0ccd20-93b2-43c1-a877-f3e5c80c46dd.png)






Week_9


PC Setup

Install Ros on remote PC


# Open the terminal with Ctrl+Alt+T and enter below commands one at a time.


wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros2_foxy.sh

![Screenshot (34)](https://user-images.githubusercontent.com/114398078/201788754-086bf91f-bcda-4699-a0d2-16f40f74d5f5.png)


sudo chmod 755 ./install_ros2_foxy.sh

![Screenshot (35)](https://user-images.githubusercontent.com/114398078/201788931-59747988-2188-407d-a4b0-0bc130e10db7.png)


bash ./install_ros2_foxy.sh

![Screenshot (37)](https://user-images.githubusercontent.com/114398078/201789058-11ab29cb-996a-4ba6-8113-1946cf115f2c.png)


Install Dependent ROS 2 Packages


# Open the terminal with Ctrl+Alt+T from Remote PC.
Install Gazebo11

![image](https://user-images.githubusercontent.com/114398078/201791226-e995aa3f-d7b3-4c35-9398-e60a703386a8.png)


#  Install Cartographer

sudo apt install ros-foxy-cartographer

![image](https://user-images.githubusercontent.com/114398078/201791719-3e9b19dc-eeeb-4d46-a70b-6f4417a6c94d.png)
![image](https://user-images.githubusercontent.com/114398078/201791756-32ac0cec-6107-4f23-a7fd-01bc8077ac3a.png)




