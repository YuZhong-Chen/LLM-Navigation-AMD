# LLM-Navigation-AMD

> To avoid dependency issues among various apps, we place each app in its own Docker container.

Before starting to test our application, it is strongly recommended to thoroughly understand our architecture diagram. This will help you better comprehend the purpose of each step.

To enhance the possibility of reproduction, we provide Dockerfile and Docker Compose to help set up the environment. However, due to variations in the actual robot configurations, some Docker settings may need to be adjusted manually.

Below is the complete list of workspaces along with a brief introduction to each workspace.

- hydra_ws
  - Generate the scene graph.
- kobuki_ws
  - Bring up the kobuki robot.
- realsense_ros1_ws
  - Setup the Intel Realsense camera.
- ros1_bridge_ws
  - Message exchanging between ROS1 noetic and ROS2 humble.
- vlplidar_ws
  - Setup the VLP-16 LiDAR.
- llm_query_ws
  - Query the LLM.

## Step 1: Open the ros1_bridge

Please modify the `ROS_HOSTNAME` and `ROS_MASTER_URI` in the `ros1_bridge_ws/docker/compose.yaml` based on your computer setup. Then, use `docker compose up` to build the Docker image and create the Docker container to tun the ros1_bridge.

## Step 2: Bring-up the Robot

Run the script `run.sh` in `scipts` folder to bring up Kobuki, VLP-16 and Realsense. You may need to modify some settings based on your robot configuration.

## Step 3: Generate the 3D Scene Graph with LLM Guidance

After building the package in `hydra_ws`, use the command `roslaunch hydra_ros run_sg.launch` to generate the 3D scene graph. Then, use the `query.py` script in `llm_query_ws` to query the LLM with the current scene graph.
