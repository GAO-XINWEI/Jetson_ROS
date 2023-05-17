# Build New ROS2 Project

## Setting Up Your Workspace
Create a new directory for your workspace and a src directory inside it. The src directory will hold your packages.
```bash
mkdir -p ~/Project/ROS/ros2_ws_test/src
cd ~/Project/ROS/ros2_ws_test/src
```

## Creating a New Package
Use the ros2 pkg create command to create a new Python package. Here's how you can create a package named my_package:
```bash
ros2 pkg create --build-type ament_python my_package_test
```

## Adding Nodes
1. Create a talker.py script inside the my_package_test/my_package_test directory
2. Create a listener.py script inside the my_package_test/my_package_test directory 

## Updating setup.py
In order for ros2 run to find your scripts, you need to install them. This is done by listing them in the setup.py file.
Open the setup.py file located at my_package/setup.py and modify it to look like this:
```bash
...
entry_points={
    'console_scripts': [
        'talker = my_package.talker:main',
        'listener = my_package.listener:main',
    ],
},
...
```

## Building Your Package
Go back to your workspace directory and build your package using colcon build:
After building, you need to source your workspace:
```bash
cd ~/Project/ROS/ros2_ws_test/
colcon build --packages-select my_package_test
```

## Running Your Nodes
Finally, you can run your nodes using the ros2 run command. Open two terminals and source the workspace in each. In one terminal, start the talker node:
```bash
ros2 run my_package talker
```
In the other terminal, start the listener node:
```bash
ros2 run my_package listener
```
