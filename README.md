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


Step_2 : Writing the publisher node

Navigate into ros2_ws/src/py_pubsub/py_pubsub
![image](https://user-images.githubusercontent.com/114398078/202094631-616d2b32-c3b5-4138-bd82-b549032e0de1.png)

Download the code using this command :

wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py

Now there will be a new file named publisher_member_function.py adjacent to init.py. In order to see them we type ls and we can see publisher_member_function.py and init.py files on terminal. In order to open the files just type open before the name of the files :
![image](https://user-images.githubusercontent.com/114398078/202095092-db9eecf3-87c1-426f-86cc-3fdf21d41cb6.png)
![image](https://user-images.githubusercontent.com/114398078/202095125-030bbaec-78ac-479e-8028-cada6dba5ecc.png)

Step_3 : Adding dependencies :

Navigate to ros2_ws/src/py_pubsub and there is package.xml file. Open the file using open package.xml command :

After that set the file by filling with my email and licence in my repository
![image](https://user-images.githubusercontent.com/114398078/202095225-2f89de62-a0ea-47f3-983c-d90d98d5f894.png)

And we add the dependencies after that :

![image](https://user-images.githubusercontent.com/114398078/202095305-bf41bade-7473-4bad-b54e-73a75eef5a96.png)

Add an entry point

We open the setup.py file and match the maintainer, maintainer_email, description and license fields to your package.xml:

![image](https://user-images.githubusercontent.com/114398078/202095418-c40b8c9f-97d4-4dbf-8402-b0b02a0abdca.png)

After that the contents of the setup.cfg file should be correctly populated automatically, like so:
![image](https://user-images.githubusercontent.com/114398078/202095503-8aa8f7ff-cedd-4cb0-8fc5-27adc762bb2b.png)


Step_4 Write the subscriber node

we navigate to ros2_ws/src/py_pubsub/pysub, and enter the following command :

wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py

![image](https://user-images.githubusercontent.com/114398078/202095699-cdc0c5cb-fa7b-4af4-a0f6-4f28d81a5c94.png)

we open init.py, publisher_member_function.py, subscriber_member_function.py and fill the dependencies :
![image](https://user-images.githubusercontent.com/114398078/202095755-409a2d1f-27a9-4021-9d89-519f70b41bd9.png)

Step_5 Build and Run

To run rosdep in the root of your workspace (ros2_ws) to check for missing dependencies before building :

(from now on I am using another wmware terminal just because of some problems in my 'ro2@ros2ubuntu' named terminal. Please do not be in doubt with another named terminal, this is also mine.)
![image](https://user-images.githubusercontent.com/114398078/202095823-d440b956-0c50-41e3-b725-b04409e2ce68.png)

Then we build a new package in the root of ros2_ws

colcon build --packages-select py_pubsub

After that open a new terminal and source the setup files

. install/setup.bash
![image](https://user-images.githubusercontent.com/114398078/202095896-49532f75-394f-4d37-b3fc-e97d27feb5fa.png)

We run the talker node with the command :

ros2 run py_pubsub talker

![image](https://user-images.githubusercontent.com/114398078/202095957-e4496383-be11-4b5b-81ed-e5ebd7f03f5c.png)
![image](https://user-images.githubusercontent.com/114398078/202095977-14089b0b-9e4a-4c8a-a3e2-50e9fb19d09e.png)

Open another terminal, source the setup files from inside ros2_ws again, and then start the listener node:

ros2 run py_pubsub listener The listener will start printing messages to the console, starting at whatever message count the publisher is on at that time, like so:

![image](https://user-images.githubusercontent.com/114398078/202096251-2ec1f1bb-847b-4554-83f2-8e125f77bb63.png)
![image](https://user-images.githubusercontent.com/114398078/202096273-73ba64ac-b661-4dc5-a29f-0986a93cd587.png)


Week_6 Write a Simple Service and Client

Step 1

#Recall that packages should be created in the src directory, not the root of the workspace. Navigate into ros2_ws/src and create a new package:

![image](https://user-images.githubusercontent.com/114398078/202096383-3b69c9a8-45a4-4818-8bd3-1f67cabfeac1.png)

Step 2

make sure to add the description, maintainer email and name, and license information to package.xm :

![image](https://user-images.githubusercontent.com/114398078/202096489-ea7e633f-5dc9-4052-ae4d-b9edf440f42d.png)
![image](https://user-images.githubusercontent.com/114398078/202096513-1c832130-b25e-4614-89c6-c3e6b87cf65f.png)

Step 3

#Adding an entry point :

![image](https://user-images.githubusercontent.com/114398078/202096593-bb4c49ea-757d-4f3a-ae5b-20fdcd3d59f0.png)

Step 4

Write the client node

create a new file called client_member_function.py and paste the following code :

![image](https://user-images.githubusercontent.com/114398078/202096712-c741fa5a-e446-4a70-abb7-1f357d5568b7.png)

Step 5

Add an entry point The entry_points field of your setup.py file should look like this :

![image](https://user-images.githubusercontent.com/114398078/202096792-e9417937-edd7-4d46-8669-03903a0e4956.png)

Step 6

Build and Run

in the root of your workspace (ros2_ws) to check for missing dependencies before building :

rosdep install -i --from-path src --rosdistro humble -y

Navigate back to the root of your workspace, ros2_ws, and build your new package :
colcon build --packages-select py_srvcli

Open a new terminal, navigate to ros2_ws, and source the setup files :

. install/setup.bash

Now run the service node:

ros2 run py_srvcli service

Open another terminal and source the setup files from inside ros2_ws again. Start the client node, followed by any two integers separated by a space :

ros2 run py_srvcli client 2 3

Part_2

Creating custom msg and srv files

Step 1

Create a new package
Navigate to ros2_ws/src and install a package named "tutorial interfaces" :

ros2 pkg create --build-type ament_cmake tutorial_interfaces

![image](https://user-images.githubusercontent.com/114398078/202096933-bb5dbf86-efb6-432a-9a8d-6b7dc9b9fd26.png)

Then create two new folders :

![image](https://user-images.githubusercontent.com/114398078/202097011-3120f8ac-97eb-422d-9619-f0e0b94247f2.png)

Step msg definition

In the tutorial_interfaces/msg directory you just created, make a new file called Num.msg with one line of code declaring its data structure:
int64 num

![image](https://user-images.githubusercontent.com/114398078/202097134-104ae913-1b28-4fbd-8b59-17f7b5d039b8.png)


And next to the Num.msg, create a file called Sphere.msg

![image](https://user-images.githubusercontent.com/114398078/202097197-70380bcc-e048-425f-9b60-d3ccc2d4c90a.png)

Step 3 srv definition

Back to tutorial_interfaces/srv directory and make a new file called AddThreeInts.srv with the following request and response structure :

![image](https://user-images.githubusercontent.com/114398078/202097365-9962aeaa-47b9-4c6b-9044-c6a170dff8fc.png)

int64 a int64 b int64 c
int64 sum

![image](https://user-images.githubusercontent.com/114398078/202097487-57971284-c297-453f-8b3c-b1b14a04fe8a.png)


Step 4

CMakeLists.txt

To convert the interfaces you defined into language-specific code (like C++ and Python) so that they can be used in those languages, add the following lines to CMakeLists.txt :
find_package(geometry_msgs REQUIRED) find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} "msg/Num.msg" "msg/Sphere.msg" "srv/AddThreeInts.srv" DEPENDENCIES geometry_msgs # Add packages that above messages depend on, in this case geometry_msgs for Sphere.msg )

Step 5

package.xml

Add the following lines to package.xml
geometry_msgs

<build_depend>rosidl_default_generators</build_depend>

<exec_depend>rosidl_default_runtime</exec_depend>

<member_of_group>rosidl_interface_packages</member_of_group>

Step 6

Build the tutorial_interfaces package

All the parts of custom interfaces package are in place, you can build the package. In the root of workspace (~/ros2_ws), run the following command:
colcon build --packages-select tutorial_interfaces

Step 7

Confirm msg and srv creation

n a new terminal, run the following command from within your workspace (ros2_ws) to source it :
. install/setup.bash

It is time to confirm that interface creation worked by using the ros2 interface show command :
ros2 interface show tutorial_interfaces/msg/Num

It returns :
int64 num

And
ros2 interface show tutorial_interfaces/msg/Sphere

geometry_msgs/Point center float64 x float64 y float64 z float64 radius

And
ros2 interface show tutorial_interfaces/srv/AddThreeInts

And
int64 a int64 b int64 c
int64 sum

Step 8

Testing Num.msg with pub/sub

Publisher :
#include #include

#include "rclcpp/rclcpp.hpp" #include "tutorial_interfaces/msg/num.hpp" // CHANGE

using namespace std::chrono_literals;

class MinimalPublisher : public rclcpp::Node { public: MinimalPublisher() : Node("minimal_publisher"), count_(0) { publisher_ = this->create_publisher<tutorial_interfaces::msg::Num>("topic", 10); // CHANGE timer_ = this->create_wall_timer( 500ms, std::bind(&MinimalPublisher::timer_callback, this)); }

private: void timer_callback() { auto message = tutorial_interfaces::msg::Num(); // CHANGE message.num = this->count_++; // CHANGE RCLCPP_INFO_STREAM(this->get_logger(), "Publishing: '" << message.num << "'"); // CHANGE publisher_->publish(message); } rclcpp::TimerBase::SharedPtr timer_; rclcpp::Publisher<tutorial_interfaces::msg::Num>::SharedPtr publisher_; // CHANGE size_t count_; };

int main(int argc, char * argv[]) { rclcpp::init(argc, argv); rclcpp::spin(std::make_shared()); rclcpp::shutdown(); return 0; }

Subscriber :
#include #include

#include "rclcpp/rclcpp.hpp" #include "tutorial_interfaces/msg/num.hpp" // CHANGE

using std::placeholders::_1;

class MinimalSubscriber : public rclcpp::Node { public: MinimalSubscriber() : Node("minimal_subscriber") { subscription_ = this->create_subscription<tutorial_interfaces::msg::Num>( // CHANGE "topic", 10, std::bind(&MinimalSubscriber::topic_callback, this, _1)); }

private: void topic_callback(const tutorial_interfaces::msg::Num & msg) const // CHANGE { RCLCPP_INFO_STREAM(this->get_logger(), "I heard: '" << msg.num << "'"); // CHANGE } rclcpp::Subscription<tutorial_interfaces::msg::Num>::SharedPtr subscription_; // CHANGE };

int main(int argc, char * argv[]) { rclcpp::init(argc, argv); rclcpp::spin(std::make_shared()); rclcpp::shutdown(); return 0; }

CMakeLists.txt :
#...

find_package(ament_cmake REQUIRED) find_package(rclcpp REQUIRED) find_package(tutorial_interfaces REQUIRED) # CHANGE

add_executable(talker src/publisher_member_function.cpp) ament_target_dependencies(talker rclcpp tutorial_interfaces) # CHANGE

add_executable(listener src/subscriber_member_function.cpp) ament_target_dependencies(listener rclcpp tutorial_interfaces) # CHANGE

install(TARGETS talker listener DESTINATION lib/${PROJECT_NAME})

ament_package()

package.xml:
Add the following line :
tutorial_interfaces

After making the above edits and saving all the changes, build the package :

colcon build --packages-select cpp_pubsub

And I open two new terminals, source ros2_ws in each, and run :
ros2 run cpp_pubsub talker

ros2 run cpp_pubsub listener

![image](https://user-images.githubusercontent.com/114398078/202097612-8844ce52-1346-45bd-9ea5-ea49e79925e9.png)

[INFO] [minimal_publisher]: Publishing: '0' [INFO] [minimal_publisher]: Publishing: '1' [INFO] [minimal_publisher]: Publishing: '2'

Step 9

Testing AddThreeInts.srv with service/client

Change the original two integer request srv to a three request integer request srv :
Service :
#include "rclcpp/rclcpp.hpp" #include "tutorial_interfaces/srv/add_three_ints.hpp" // CHANGE

#include

void add(const std::shared_ptr<tutorial_interfaces::srv::AddThreeInts::Request> request, // CHANGE std::shared_ptr<tutorial_interfaces::srv::AddThreeInts::Response> response) // CHANGE { response->sum = request->a + request->b + request->c; // CHANGE RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "Incoming request\na: %ld" " b: %ld" " c: %ld", // CHANGE request->a, request->b, request->c); // CHANGE RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "sending back response: [%ld]", (long int)response->sum); }

int main(int argc, char **argv) { rclcpp::init(argc, argv);

std::shared_ptrrclcpp::Node node = rclcpp::Node::make_shared("add_three_ints_server"); // CHANGE

rclcpp::Service<tutorial_interfaces::srv::AddThreeInts>::SharedPtr service = // CHANGE node->create_service<tutorial_interfaces::srv::AddThreeInts>("add_three_ints", &add); // CHANGE

RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "Ready to add three ints."); // CHANGE

rclcpp::spin(node); rclcpp::shutdown(); }

Client :
#include "rclcpp/rclcpp.hpp" #include "tutorial_interfaces/srv/add_three_ints.hpp" // CHANGE

#include #include #include

using namespace std::chrono_literals;

int main(int argc, char **argv) { rclcpp::init(argc, argv);

if (argc != 4) { // CHANGE RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "usage: add_three_ints_client X Y Z"); // CHANGE return 1; }

std::shared_ptrrclcpp::Node node = rclcpp::Node::make_shared("add_three_ints_client"); // CHANGE rclcpp::Client<tutorial_interfaces::srv::AddThreeInts>::SharedPtr client = // CHANGE node->create_client<tutorial_interfaces::srv::AddThreeInts>("add_three_ints"); // CHANGE

auto request = std::make_shared<tutorial_interfaces::srv::AddThreeInts::Request>(); // CHANGE request->a = atoll(argv[1]); request->b = atoll(argv[2]); request->c = atoll(argv[3]); // CHANGE

while (!client->wait_for_service(1s)) { if (!rclcpp::ok()) { RCLCPP_ERROR(rclcpp::get_logger("rclcpp"), "Interrupted while waiting for the service. Exiting."); return 0; } RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "service not available, waiting again..."); }

auto result = client->async_send_request(request); // Wait for the result. if (rclcpp::spin_until_future_complete(node, result) == rclcpp::FutureReturnCode::SUCCESS) { RCLCPP_INFO(rclcpp::get_logger("rclcpp"), "Sum: %ld", result.get()->sum); } else { RCLCPP_ERROR(rclcpp::get_logger("rclcpp"), "Failed to call service add_three_ints"); // CHANGE }

rclcpp::shutdown(); return 0; }

CMakeLists.txt:
Add the following lines (C++ only):
#...

find_package(ament_cmake REQUIRED) find_package(rclcpp REQUIRED) find_package(tutorial_interfaces REQUIRED) # CHANGE

add_executable(server src/add_two_ints_server.cpp) ament_target_dependencies(server rclcpp tutorial_interfaces) # CHANGE

add_executable(client src/add_two_ints_client.cpp) ament_target_dependencies(client rclcpp tutorial_interfaces) # CHANGE

install(TARGETS server client DESTINATION lib/${PROJECT_NAME})

ament_package()

package.xml:
Add the following line:
tutorial_interfaces

After editing and saving all changes, we build the package :
colcon build --packages-select cpp_srvcli

Then we open two new terminals, source ros2_ws in each, and run:
ros2 run cpp_srvcli server

ros2 run cpp_srvcli client 2 3 1

Week_7

Writing an action server and client

Step 1

Writing an action server

Open a new file in your home directory, let’s call it fibonacci_action_server.py, and add the following code :

![image](https://user-images.githubusercontent.com/114398078/202097689-1ca6c07c-92a0-4e2d-9561-cb8f85c60414.png)

And we try to run our action server :
python3 fibonacci_action_server.py

![image](https://user-images.githubusercontent.com/114398078/202097751-2ec43cc9-c8c5-4233-af48-6ac0f039eeaa.png)

In another terminal, we can use the command line interface to send a goal :

ros2 action send_goal fibonacci action_tutorials_interfaces/action/Fibonacci "{order: 5}"

![image](https://user-images.githubusercontent.com/114398078/202097825-5d4f3ca2-c7f3-4b7b-ac75-11ce1d85a958.png)

Now let’s make our goal execution actually compute and return the requested Fibonacci sequence:

![image](https://user-images.githubusercontent.com/114398078/202097881-9ca385ba-0637-4eb1-b6bb-891e61444042.png)

Step 2

Publishing feedback

We’ll replace the sequence variable, and use a feedback message to store the sequence instead

![image](https://user-images.githubusercontent.com/114398078/202097948-d5e25abb-fde3-4f41-93fd-a064e7db47f3.png)

Step 3

Writing an action client

We’ll also scope the action client to a single file. Open a new file, let’s call it fibonacci_action_client.py, and add the following boilerplate code :

![image](https://user-images.githubusercontent.com/114398078/202098006-0699da56-d8d0-4ef8-b396-20a411c11301.png)

Let’s test our action client by first running the action server built earlier :

python3 fibonacci_action_server.py

![image](https://user-images.githubusercontent.com/114398078/202098050-5ff8e5b4-08e3-41a3-9028-0c19a3d4b7b9.png)


And in another terminal we run the action client :

python3 fibonacci_action_client.py

The action client should start up, and then quickly finish. At this point, we have a functioning action client, but we don’t see any results or get any feedback :

![image](https://user-images.githubusercontent.com/114398078/202098126-4ce38e3f-b6b4-460f-b3c7-d13f7900b553.png)


Step 4

Getting a result

Here’s the complete code for this example :
import rclpy from rclpy.action import ActionClient from rclpy.node import Node

from action_tutorials_interfaces.action import Fibonacci

+jkjjhhj h
class FibonacciActionClient(Node):

def __init__(self):
    super().__init__('fibonacci_action_client')
    self._action_client = ActionClient(self, Fibonacci, 'fibonacci')

def send_goal(self, order):
    goal_msg = Fibonacci.Goal()
    goal_msg.order = order

    self._action_client.wait_for_server()

    self._send_goal_future = self._action_client.send_goal_async(goal_msg)

    self._send_goal_future.add_done_callback(self.goal_response_callback)

def goal_response_callback(self, future):
    goal_handle = future.result()
    if not goal_handle.accepted:
        self.get_logger().info('Goal rejected :(')
        return

    self.get_logger().info('Goal accepted :)')

    self._get_result_future = goal_handle.get_result_async()
    self._get_result_future.add_done_callback(self.get_result_callback)

def get_result_callback(self, future):
    result = future.result().result
    self.get_logger().info('Result: {0}'.format(result.sequence))
    rclpy.shutdown()
    
    
    
    +
    +


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
![Screenshot (41)](https://user-images.githubusercontent.com/114398078/201792401-0faf7e26-126d-4480-8032-eec4a4d37143.png)
![Screenshot (42)](https://user-images.githubusercontent.com/114398078/201792493-2586abf0-7cd3-40cc-b4c7-2f02c9403571.png)


# Install Navigation2


sudo apt install ros-foxy-navigation2

![Screenshot (43)](https://user-images.githubusercontent.com/114398078/201792761-a7f8fc6a-4078-4499-94c3-3dc75213d2cf.png)
![Screenshot (44)](https://user-images.githubusercontent.com/114398078/201792893-0f78cfc5-d742-4a3d-9772-806724b7ec77.png)

sudo apt install ros-foxy-nav2-bringup

![Screenshot (45)](https://user-images.githubusercontent.com/114398078/201793155-ca77c475-7435-44f1-8fe8-e347f71ebf9d.png)
![Screenshot (46)](https://user-images.githubusercontent.com/114398078/201793261-0daff8b9-0a83-4d4c-bafc-498139833957.png)




Install TurtleBot3 Packages



# Install TurtleBot3 via Debian Packages.

source ~/.bashrc
sudo apt install ros-foxy-dynamixel-sdk

![Screenshot (47)](https://user-images.githubusercontent.com/114398078/201793611-2d355971-6807-4d2b-81ec-b55d4f992916.png)

sudo apt install ros-foxy-turtlebot3-msgs

![Screenshot (48)](https://user-images.githubusercontent.com/114398078/201793760-5850082e-ea4f-40f7-9906-62885fc36b97.png)

sudo apt install ros-foxy-turtlebot3

![Screenshot (49)](https://user-images.githubusercontent.com/114398078/201793885-0271e80b-5b90-4c3a-936b-89a1f11b97c1.png)
![Screenshot (50)](https://user-images.githubusercontent.com/114398078/201793982-12336089-b48b-463f-a4f8-13745fd75ed1.png)


Environment Configuration


# Set the ROS environment for PC

echo 'export ROS_DOMAIN_ID=30 #TURTLEBOT3' >> ~/.bashrc
source ~/.bashrc


![Screenshot (51)](https://user-images.githubusercontent.com/114398078/201794607-793e0b0e-aa19-4288-a1df-a992c3363784.png)


### PC Setup finished.



SBC Setup





