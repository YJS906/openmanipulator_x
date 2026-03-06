OpenMANIPULATOR-X 실행 방법

1. OpenCR 사용 시 실제 로봇 연결

OpenMANIPULATOR-X를 OpenCR에 연결한 뒤, 아래 명령어로 하드웨어를 실행한다.

ros2 launch open_manipulator_x_bringup hardware.launch.py port_name:=/dev/ttyACM0

기본 포트를 사용할 경우에는 아래처럼 실행 가능함. 

ros2 launch open_manipulator_x_bringup hardware.launch.py


2. Keyboard Teleoperation 

키보드를 이용해 OpenMANIPULATOR-X를 조작하려면 먼저 servo를 실행한 뒤 teleop 노드를 실행해야함.

ros2 launch open_manipulator_x_moveit_config servo.launch.py
ros2 run open_manipulator_x_teleop open_manipulator_x_teleop

3. RViz 실행 

ros2 launch open_manipulator_x_description model.launch.py

4. Moveit 실행

ros2 launch open_manipulator_x_moveit_config moveit_core.launch.py

5. Gazebo 실행

ros2 launch open_manipulator_x_moveit_config moveit_gazebo.launch.py
