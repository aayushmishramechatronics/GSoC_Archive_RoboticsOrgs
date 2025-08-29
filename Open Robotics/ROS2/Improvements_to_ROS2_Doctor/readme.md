- Prerequisites: Ubuntu and ROS 2 Development Environment, `No Need for Specialized Hardware.`
- Programming Skills: Familiarity with C/C++/Python, CMake, ABI/API.
- Difficulty Level: Medium.
- Expected Size: 100 hours to 150 hours.
- Expected Outcome: A ROS 2 command line interface ros2cli with doctor sub-command and ros2_documentation.
  
Detailed Description: 
- Currently, the ROS2 Doctor subcommand, ROS2 Doctor, is lacking a lot of useful information, such as `ROS Environment Variables`, `RMW-Specific Environment Variables`, and `Configuration and Service Information (Number of Endpoints, QoS Compatibility Status, etc.)`. 
- This information is really important and useful for debugging issues with ROS2, and would greatly improve our ability to support issues reported by our user community. 
- In other words, adding this new information to our existing ROS2 Doctor command would accelerate community communication and make bug reports much more precise! 
- Aligned with `ros2cli` development, this project also targets the implementation of improved documentation on how to create an issue report with a new issue template.

Reference Pull Requests: [Add Default Github Issue Templates](https://github.com/ros2/.github/pull/3)
, [Add: Get Clients, Servers Info](https://github.com/ros2/rmw/pull/371)
