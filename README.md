---Writing a simple publisher and subscriber using python with ros2 (humble)---

os2 pkg create --build-type ament_python py_pubsub
going to create a new package
package name: py_pubsub
destination directory: /home/ubuntu
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['ubuntu <ubuntu@todo.todo>']
licenses: ['TODO: License declaration']
build type: ament_python
dependencies: []
creating folder ./py_pubsub
creating ./py_pubsub/package.xml
creating source folder
creating folder ./py_pubsub/py_pubsub
creating ./py_pubsub/setup.py
creating ./py_pubsub/setup.cfg
creating folder ./py_pubsub/resource
creating ./py_pubsub/resource/py_pubsub
creating ./py_pubsub/py_pubsub/__init__.py
creating folder ./py_pubsub/test
creating ./py_pubsub/test/test_copyright.py
creating ./py_pubsub/test/test_flake8.py
creating ./py_pubsub/test/test_pep257.py

[WARNING]: Unknown license 'TODO: License declaration'.  This has been set in the package.xml, but no LICENSE file has been created.
It is recommended to use one of the ament license identitifers:
Apache-2.0
BSL-1.0
BSD-2.0
BSD-2-Clause
BSD-3-Clause
GPL-3.0-only
LGPL-3.0-only
MIT
MIT-0
ubuntu@ubuntu-ros2:~$ wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-10-05 22:07:03--  https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.111.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1576 (1.5K) [text/plain]
Saving to: ‘publisher_member_function.py’

publisher_member_fu 100%[==================>]   1.54K  --.-KB/s    in 0s      

2022-10-05 22:07:03 (5.40 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]


---And we add dependencies into package.sxml and setup.py files that have been created in ros2_ws directory---

<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>py_pubsub</name>
  <version>0.0.0</version>
  <description>TODO: Package description</description>
  <maintainer email="12194924@gmail.com">ubuntu</maintainer>
  <license>Apache License 2.0</license>
  
  
  <exec_depend>rclpy</exec_depend>
<exec_depend>std_msgs</exec_depend>


  <test_depend>ament_copyright</test_depend>
  <test_depend>ament_flake8</test_depend>
  <test_depend>ament_pep257</test_depend>
  <test_depend>python3-pytest</test_depend>

  <export>
    <build_type>ament_python</build_type>
  </export>
</package>

--------------------------------------------------

from setuptools import setup

package_name = 'py_pubsub'

setup(
    name=package_name,
    version='0.0.0',
    packages=[package_name],
    data_files=[
        ('share/ament_index/resource_index/packages',
            ['resource/' + package_name]),
        ('share/' + package_name, ['package.xml']),
    ],
    install_requires=['setuptools'],
    zip_safe=True,
    maintainer='ubuntu',
    maintainer_email='12194924@gmail.com',
    description='Examples of minimal publisher/subscriber using rclpy',
    license='Apache License 2.0',
    tests_require=['pytest'],
    entry_points={
        'console_scripts': [ 
                'talker = py_pubsub.publisher_member_function:main',
                'listener = py_pubsub.subscriber_member_function:main',
        ],
    },
)

--- We check dependies with the following command:
rosdep install -i --from-path src --rosdistro humble -y
colcon build --packages-select py_pubsub
. install/setup.bash
---Try to run the talker:---

ros2 run py_pubsub talker

[INFO] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [minimal_publisher]: Publishing: "Hello World: 3"
[INFO] [minimal_publisher]: Publishing: "Hello World: 4"
[INFO] [minimal_publisher]: Publishing: "Hello World: 5"
[INFO] [minimal_publisher]: Publishing: "Hello World: 6"
[INFO] [minimal_publisher]: Publishing: "Hello World: 7"
[INFO] [minimal_publisher]: Publishing: "Hello World: 8"
[INFO] [minimal_publisher]: Publishing: "Hello World: 9"

---Try to run the listener:---

[INFO] [minimal_subscriber]: I heard: "Hello World: 0"
[INFO] [minimal_subscriber]: I heard: "Hello World: 1"
[INFO] [minimal_subscriber]: I heard: "Hello World: 2"
[INFO] [minimal_subscriber]: I heard: "Hello World: 3"
[INFO] [minimal_subscriber]: I heard: "Hello World: 4"
[INFO] [minimal_subscriber]: I heard: "Hello World: 6"
[INFO] [minimal_subscriber]: I heard: "Hello World: 7"
[INFO] [minimal_subscriber]: I heard: "Hello World: 8"
[INFO] [minimal_subscriber]: I heard: "Hello World: 9"


------------------------------------------------------------------------------------------------------------

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

sudo apt update
[sudo] password for ros2: 
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                      
Hit:2 http://kr.archive.ubuntu.com/ubuntu jammy InRelease                                      
Ign:3 http://packages.ros.org/ros/ubuntu jammy InRelease                                       
Hit:4 http://packages.ros.org/ros2/ubuntu jammy InRelease                      
Get:5 http://kr.archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]     
Err:6 http://packages.ros.org/ros/ubuntu jammy Release                                    
  404  Not Found [IP: 64.50.236.52 80]
Get:7 http://kr.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]             
Reading package lists... Done       
E: The repository 'http://packages.ros.org/ros/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
ros2@ubuntu:~$ sudo apt install ~nros-rolling-rqt*
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
ros2@ubuntu:~$ rqt


![Screenshot_3](https://user-images.githubusercontent.com/114398078/192256430-55ce7fd2-1025-4d83-86c5-9da5ac4535ec.png)
![Screenshot_4](https://user-images.githubusercontent.com/114398078/192256433-b7effc8a-db0a-4e47-b24d-38e1e524a57e.png)
[turtle_action.webm](https://user-images.githubusercontent.com/114398078/192256181-ae64c811-02c6-41bd-bcd4-da38c9c3b19b.webm)
# projects_2022
projects
