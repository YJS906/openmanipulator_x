ROS2 Humble 기준 Install ROS Packges

```bash
sudo apt install \
  ros-humble-ros2-control \
  ros-humble-moveit* \
  ros-humble-gazebo-ros2-control \
  ros-humble-ros2-controllers \
  ros-humble-controller-manager \
  ros-humble-position-controllers \
  ros-humble-joint-state-broadcaster \
  ros-humble-joint-trajectory-controller \
  ros-humble-gripper-controllers \
  ros-humble-hardware-interface \
  ros-humble-xacro
```

```bash
mkdir -p colcon_ws/src
cd ~/colcon_ws/src/
git clone -b humble https://github.com/ROBOTIS-GIT/DynamixelSDK.git
git clone -b humble https://github.com/ROBOTIS-GIT/open_manipulator.git
git clone -b humble https://github.com/ROBOTIS-GIT/dynamixel_hardware_interface.git
git clone -b humble https://github.com/ROBOTIS-GIT/dynamixel_interfaces.git
cd ~/colcon_ws && colcon build --symlink-install
```

Set the ROS enviroment for PC
```bash
$ echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
$ echo 'source ~/colcon_ws/install/local_setup.bash' >> ~/.bashrc
$ source ~/.bashrc
```

OpenMANIPULATOR-X 실행 방법

1. OpenCR 사용 시 실제 로봇 연결

OpenMANIPULATOR-X를 OpenCR에 연결한 뒤, 아래 명령어로 하드웨어를 실행함.

```bash
ros2 launch open_manipulator_x_bringup hardware.launch.py port_name:=/dev/ttyACM0
```

기본 포트를 사용할 경우에는 아래처럼 실행 가능함. 

```bash
ros2 launch open_manipulator_x_bringup hardware.launch.py
```


2. Keyboard Teleoperation 

키보드를 이용해 OpenMANIPULATOR-X를 조작하려면 먼저 servo를 실행한 뒤 teleop 노드를 실행해야함.
```bash
ros2 launch open_manipulator_x_moveit_config servo.launch.py
ros2 run open_manipulator_x_teleop open_manipulator_x_teleop
```


3. RViz 실행 
```bash
ros2 launch open_manipulator_x_description model.launch.py
```


4. Moveit 실행
```bash
ros2 launch open_manipulator_x_moveit_config moveit_core.launch.py
```


5. Gazebo 실행
```bash
ros2 launch open_manipulator_x_moveit_config moveit_gazebo.launch.py
```

6. OpenManipulator Control GUI
Moveit을 실행시킨 뒤
```bash
ros2 launch open_manipulator_x_moveit_config moveit_core.launch.py
```
실행 
```bash
ros2 launch open_manipulator_x_gui open_manipulator_x_gui.launch.py
```
