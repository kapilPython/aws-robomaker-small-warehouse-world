# AWS RoboMaker Small Warehouse World

![Gazebo01](docs/images/small_warehouse_gazebo.png)


This Gazebo world is well suited for organizations who are building and testing robot applications for warehouse and logistics use cases. 

## 3D Models included in this Gazebo World

| Model (/models)       | Picture           |
| :------------- |:-------------:|
| **aws_robomaker_warehouse_Bucket_01**    | ![Model: Buckets](docs/images/models_buckets.png)
| **aws_robomaker_warehouse_ClutteringA_01, aws_robomaker_warehouse_ClutteringC_01, aws_robomaker_warehouse_ClutteringD_01**     | ![Model: Box Clusters](docs/images/models_boxes.png) |
| **aws_robomaker_warehouse_DeskC_01**    | ![Model: Desk](docs/images/models_desk.png)
| **aws_robomaker_warehouse_GroundB_01**    | ![Model: Ground Paint](docs/images/models_warehouse_ground_paint.png)
| **aws_robomaker_warehouse_TrashCanC_01**   | ![Model: Humans](docs/images/models_trashcan.png)
| **aws_robomaker_warehouse_Lamp_01**    | ![Model: Ceiling Lamp](docs/images/models_ceiling_lamp.png)
| **aws_robomaker_warehouse_PalletJackB_01**    | ![Model: Pallet Jack](docs/images/models_lift.png)
| **aws_robomaker_warehouse_ShelfD_01, aws_robomaker_warehouse_ShelfE_01, aws_robomaker_warehouse_ShelfF_01**    | ![Model: Pallet Jack](docs/images/models_shelves.png)

## Building and Launching the Gazebo World with your ROS Applications

* Create or update a **.rosinstall** file in the root directory of your ROS workspace. Add the following line to **.rosintall**:
    ```
    - git: {local-name: src/aws-robomaker-small-warehouse-world, uri: 'https://github.com/aws-robotics/aws-robomaker-small-warehouse-world.git', version: master}
    ```
* Change the directory to your ROS workspace and run `rosws update`

* Add the following include to the ROS launch file you are using:
    ```xml
    <launch>
    <!-- Launch World -->
    <include file="$(find aws_robomaker_small_warehouse_world)/launch/small_warehouse.launch"/>
    ...
    </launch>
    ```

* Build your application using `colcon`
    ```bash
    rosws update
    rosdep install --from-paths . --ignore-src -r -y
    colcon build
    ```

## Example: Running this world directly in Gazebo without a ROS application

To open this world in Gazebo, change the directory to your ROS workspace root folder and run:

```bash
export GAZEBO_MODEL_PATH=`pwd`/models
gazebo worlds/small_warehouse.world
```

## Example: Running this world directly using ROS without a simulated robot

To launch this base Gazebo world without a robot, clone this repository and run the following commands. **Note: ROS and gazebo must already be installed on the host.** 

```bash
# build for ROS
rosdep install --from-paths . --ignore-src -r -y
colcon build

# run in ROS
source install/setup.sh
roslaunch aws_robomaker_small_warehouse_world view_small_warehouse.launch
```

**Visit the [AWS RoboMaker website](https://aws.amazon.com/robomaker/) to learn more about building intelligent robotic applications with Amazon Web Services.**

## Notes
- Lighting might vary on different system(s) (e.g brighter on system without CPU and darker on system with GPU)
- Adjust lighting parameters in .world file as you need
