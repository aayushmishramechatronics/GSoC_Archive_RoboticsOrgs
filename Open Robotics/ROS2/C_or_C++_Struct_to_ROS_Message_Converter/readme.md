- Prerequisites: Basic Knowledge of the `rclcpp`. `No need for specialized hardware`.
- Programming Skills: Familiarity with `C++, jinja, YAML, Python and CMake`.
- Difficulty Level: Medium - Hard
- Expected Size: 175 hours
- Expected Outcome: Automatic wrapping and unwrapping of C++ structures to ROS messages!
  
Detailed Description:
- The goal of this proposal is to enable a workflow with ROS2, were one only needs write C/C++ structures and ROS2 tooling takes care of the generation of intermediate message generation and serialization. 
- This tooling would greatly reduce the amount of boilerplate code needed to transfer a given structure from one node to another node.
  
The outcome we desire would be a tool that can take input of the form:
```
struct Foo { 
  int a; 
  float b; 
}; 

struct Bar { 
  std::vector<Foo> foos; 
};
```

and automatically generate the following two ROS messages along with the corresponding typeAdapters:
```
Foo.msg: 
Int a 
Float32 b 

Bar: 
Foo[] foos
```

- This goal shall be archived by the usage of `castxml , Python and jinja`. [Castxml]() is a tool, that converts C++ headers to an xml abstract syntax tree representation, without the hassle of parsing C/C++ code. 
Therefore castxml enables simple Python scripts to perform C++ introspection. Jinja is template code generation library, that can be used from Python. 
Combining castxml with jinja therefore allows us to parse arbitrary C++ structures, introspect them, and generate matching ROS message. 
It also allows for generation of serialization code from the structure to the ROS message and back.

- Stretch goal: opaque type support

- Opaque types are types, for which no automatic serialization and intermediate message can be generated For example, `Eigen::Vector2d`
would be opaque, as some members are private. Therefore there should be the option, to register handlers for these opaque types. The handlers shall enable the user to specify custom messages and converter functions for the given opaque type. Library support would be a secondary stretch goal. The system shall generate installable files, that register (if included / loaded) known types as opaques. The auto-generated ‘library opaques’ should just refer to the already generated messages and converters of the originating library. This would effectively suppress type generation for types from other libraries.
