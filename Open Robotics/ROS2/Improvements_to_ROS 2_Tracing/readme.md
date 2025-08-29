- Prerequisites: ROS2 Experience, Some Tracing/LTTng Tracer Experience, Linux, Git
- Programming Skills: C++, Python
- Difficulty Level: Medium to Hard
- Expected Size: 175 Hours to 350 Hours
- Expected Outcome: A solution to allow enabling the ROS2 tracepoints after an application has already been launched.

Detailed Description: 
- [Software Tracing](https://lttng.org/docs/v2.13/#doc-what-is-tracing) is a method of collecting low-level runtime data to understand a system's execution. [`ros2_tracing`](https://github.com/ros2/ros2_tracing) is a collection of tracing instrumentation for ROS2 and tools to configure tracing for ROS 2 applications. 
- See the [`ros2_tracing`](https://github.com/ros2/ros2_tracing) repository and this [`ros2_tracing introduction in the ROS2 docs`](https://docs.ros.org/en/rolling/Tutorials/Advanced/ROS2-Tracing-Trace-and-Analyze.html). Currently, when tracing a ROS2 application, the [tracer has to be configured and tracing has to be started before launching an application](https://github.com/ros2/ros2_tracing#tracing).
- This is because important trace data is generated during the initialization phase of an application; without this information, trace data generated later (e.g., message publication data) cannot be decoded. This means we cannot decide to start collecting trace data for an application that is already running, which makes debugging a system that’s already running harder.
- The first goal of this project is to find a solution to allow configuring tracing at any point after the application has been launched. See [`ros2/ros2_tracing#44`](https://github.com/ros2/ros2_tracing/issues/44). This would also make live tracing easier: live tracing means processing the trace data live, as the application is executing, unlike the typical workflow, which is to process the trace data offline, after the execution.
- A stretch goal for this project would be to improve the tracing configuration tools (ros2 trace command, Trace launch action) to allow configuring a live tracing session. See [`ros2/ros2_tracing#149`](https://github.com/ros2/ros2_tracing/issues/149).
