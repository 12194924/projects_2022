ros2@ubuntu:~$ sudo apt update
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
ros2@ubuntu:~$ sudo apt --fix-broken install
eading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cmake-extras python3-rosdep2 python3-rosdistro ros-environment rospack-tools
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python3-catkin-pkg-modules python3-rosdistro-modules python3-rospkg-modules
The following NEW packages will be installed:
  python3-catkin-pkg-modules python3-rosdistro-modules python3-rospkg-modules
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
887 not fully installed or removed.
Need to get 0 B/99.2 kB of archives.
After this operation, 657 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 286122 files and directories currently installed.)
Preparing to unpack .../python3-catkin-pkg-modules_0.5.2-1_all.deb ...
Unpacking python3-catkin-pkg-modules (0.5.2-1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-catkin-pkg-modules_0.5.2-1_
all.deb (--unpack):
 trying to overwrite '/usr/lib/python3/dist-packages/catkin_pkg/__init__.py', which is als
o in package python3-catkin-pkg 0.4.24-2
Preparing to unpack .../python3-rospkg-modules_1.4.0-1_all.deb ...
Unpacking python3-rospkg-modules (1.4.0-1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-rospkg-modules_1.4.0-1_all.
deb (--unpack):
 trying to overwrite '/usr/lib/python3/dist-packages/rospkg/__init__.py', which is also in
 package python3-rospkg 1.3.0-1
Preparing to unpack .../python3-rosdistro-modules_0.9.0-1_all.deb ...
Unpacking python3-rosdistro-modules (0.9.0-1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-rosdistro-modules_0.9.0-1_a
ll.deb (--unpack):
 trying to overwrite '/usr/lib/python3/dist-packages/rosdistro/__init__.py', which is also
 in package python3-rosdistro 0.8.3-2
Errors were encountered while processing:
 /var/cache/apt/archives/python3-catkin-pkg-modules_0.5.2-1_all.deb
 /var/cache/apt/archives/python3-rospkg-modules_1.4.0-1_all.deb
 /var/cache/apt/archives/python3-rosdistro-modules_0.9.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ros2@ubuntu:~$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
ros2@ubuntu:~$ ros2 run turtlesim turtlesim_node
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
[INFO] [1664765260.156450416] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1664765260.170623028] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]


![Screenshot_1](https://user-images.githubusercontent.com/114398078/192256419-125ced48-1998-4a58-a1a1-3756e73537c1.png)


ros2@ubuntu:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.


![Screenshot_2](https://user-images.githubusercontent.com/114398078/192256427-9b907444-8b7d-4380-b4d6-20f3dd90be4c.png)
![Screenshot_3](https://user-images.githubusercontent.com/114398078/192256430-55ce7fd2-1025-4d83-86c5-9da5ac4535ec.png)
![Screenshot_4](https://user-images.githubusercontent.com/114398078/192256433-b7effc8a-db0a-4e47-b24d-38e1e524a57e.png)
[turtle_action.webm](https://user-images.githubusercontent.com/114398078/192256181-ae64c811-02c6-41bd-bcd4-da38c9c3b19b.webm)
# projects_2022
projects
