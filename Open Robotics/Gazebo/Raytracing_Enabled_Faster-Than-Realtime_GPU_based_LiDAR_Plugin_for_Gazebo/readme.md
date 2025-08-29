- Prerequisites: Cursory understanding of what a GPU is and what "ray tracing" means in the context of graphics. Access to a ray tracing enabled GPU on a non-Apple platform (one can be provided remotely if necessary).
- Programming Skills: Familiarity with C++, CMake and an understanding of ABI.
- Difficulty Level: Medium to Hard.
- Expected Size: 175 Hours to 350 Hours.
- Expected Outcome: A source buildable package containing a LiDAR Plugin for Gazebo that exploits Raytracing.

Detailed Description:
- This GSoC project exploits Raytracing GPUs in Gazebo. Recently, GPU manufacturers have been adding raytracing capabilities to their GPUs. This includes Apple, Intel, AMD and NVIDIA. Raytracing has been [shown to be an effective pathway](https://github.com/RobotecAI/RobotecGPULidar) for simulating faster-than-realtime depth sensors. 
- Other simulators that do this only exploit NVIDIA's proprietary OptiX API. Recent work in the Rust wgpu community has made it easy to use the Vulkan APIs for raytracing. Early experiments show the ability to ray trace a 256x256 depth camera at 1000fps on a consumer laptop with a 4 year old GeForce 3090 GPU. 
- A prototype has alreasdy been produced, so this project would be focused on extending the prototype into a complete solution. The prototype builds on the rust `wgpu` package and a thin C wrapper that enables integration into Gazebo. 
- Potential extension work is to support various types of depth sensors including maritime sonars/radars, along with potential publication to a relevant robotics venue.
