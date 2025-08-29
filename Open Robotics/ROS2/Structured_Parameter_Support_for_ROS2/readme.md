Prerequisites: Basic Knowledge of the `rclcpp`. `No need for specialized hardware`.
Programming Skills: Familiarity with C++, YAML, Python and CMake.
Difficulty Level: Medium
Potential Mentors: Janosch Machowinski
Expected Size: 175 hours
Expected Outcome: Ability to Use Structured Parameters in `rclcpp`

Detailed Description: 
- Currently the ROS2 Parameter Interface only Supports ‘basic’ Datatypes, or Arrays of Basic Datatypes. 
- (Eg. `int, std::string, float, std::vector<int>, std::vector< std::string >, std::vector<float> etc`) 
- The scope of this task would be, to Add Support for Structured Parameters, this is to say C++ `structs` as Parameters,

E.g.
```
struct MyConfigData 
{ 
int id; 
std::string interfaceName; 
std::vector<struct SomeOtherData> data; 
};
```

To Achieve this Goal, the following tasks need to be Completed:

- Modify ParameterValue -- A new member needs to be added to [ParameterValue Messages](https://github.com/ros2/rcl_interfaces/blob/rolling/rcl_interfaces/msg/ParameterValue.msg). The new member shall contain a structured parameter in the form of a YAML serialized structure.
- Modify rclcpp -- Currently there a checks in place, that forbid passing of complex structures as parameters, these need to be removed.
- Update parameter value -- The rclcpp::ParameterValue needs to be modified to return the serialized YAML structure.
- Convenience methods -- Add convenience functions to convert the serialized structure to a ROS message. ROS messages have a built-in introspection feature. This feature shall be used, to auto serialize the YAML blob into a ROS message. The introspection feature allows to iterate the ROS message. Therefore one can run over a given ROS message and check, if the YAML blob contains entries for all the members in the ROS message. One can also check, if no additional entries are present in the YAML blob. As the ROS message contains the data type of each member, and a generic function to write it, the deserialization of individual message members can also be implemented in a generic way.
- Stretch goal -- Implement tooling to generate YAML ‘layouts’ from a given ROS message. The goal is to implement a simple command line tool, for generating empty YAML structures for a given ROS message. These empty yaml structures are supposed to be used as templates / copied into configuration files.
