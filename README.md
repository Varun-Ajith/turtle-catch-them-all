# Turtle catch them all

## Overview
The Turtlesim Catch Them All project is a ROS 2 package that creates a fun simulation where a turtle in the Turtlesim environment chases and catches other turtles that spawn randomly. The package includes nodes for spawning turtles, controlling the main turtle, and managing the catching process.

![turtle](turtle.gif)

### Features
- **Turtle Spawner**: Randomly spawns turtles in the Turtlesim environment at specified intervals.
- **Turtle Controller**: Controls the main turtle, making it chase and catch other turtles based on their proximity.
- **Launch File**: Simplifies the process of launching the Turtlesim node along with the custom nodes.

### Installation
1. Clone the Repository: 
   ```git clone https://github.com/Varun-Ajith/turtlesim_catch_them_all.git ```
2. Build the Package:
Navigate to your ROS 2 workspace and build the package:
```colcon build --packages-select turtlesim_catch_them_all```
3. Source the Workspace:
After building, source your workspace:
```source install/setup.bash```

## Usage
### Launch the Simulation
To launch the Turtlesim node along with the custom nodes for spawning and controlling the turtles, use the following command:
```ros2 launch turtlesim_catch_them_all turtle_catch_them_all.launch.py```
### Node Descriptions
1. **turtle_spawner.py**:
- Spawns turtles at random positions within the Turtlesim environment.
- Publishes the list of alive turtles to the `alive_turtles` topic.
- Responds to requests from the `catch_turtle` service to "kill" a turtle once it's caught.

2. **turtle_controller.py**:
- Subscribes to the main turtle's position and the list of alive turtles.
- Controls the main turtle's movement to chase and catch the closest turtle (or the first turtle in the list, based on parameters).
- Calls the `catch_turtle` service when a turtle is caught.
  
3. **turtle_catch_them_all.launch.py**:

- Launches the Turtlesim node, Turtle Spawner node, and Turtle Controller node together.
- Parameters for spawn frequency, turtle name prefix, and turtle catching strategy can be configured.

### Parameters

- **Turtle Spawner Node** :

1. `spawn_frequency`: Frequency at which new turtles are spawned (default: 1.0).
2. `turtle_name_prefix`: Prefix for the spawned turtle names (default: turtle).
   
- **Turtle Controller Node**:

`catch_closest_turtle_first`: Whether to catch the closest turtle first (default: True).

### Customization
You can customize the behavior of the simulation by modifying the parameters in the `turtle_catch_them_all.launch.py` file.

## Requirements
- ROS 2 Humble
- Turtlesim package
## License
This project is licensed under the [Apache License 2.0](LICENSE).
