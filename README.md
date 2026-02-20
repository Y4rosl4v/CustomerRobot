# CustomerRobot
Разработка ПО для мобильного робота-манипулятора с техническим зрением в задаче комплектации заказа для продуктового магазина

Developing software for a mobile robotic manipulator with machine vision for grocery order picking is an ambitious and challenging task, embracing the latest advances in machine learning, motion planning, and systems integration. The project's primary challenge lies not in implementing a single function, but in reliably integrating navigation, perception, and manipulation into a single, real-time system.

## Key technology stacks and components that can be used
### Framework
Robot Operating System 2 (ROS2). This industry standard ensures modularity, code repeatability, and communication between subsystems.
### Task Management
Behavior Trees. A more flexible and modular alternative to finite-state machines for managing action sequences (navigation -> search -> grasp -> placement).
### Navigation
ROS2 Nav2 (for navigating the store) and model-predictive control (MPC) for precise positioning at shelves, often using visual markers (e.g., ArUco) for odometry correction.
### Vision
Object Detection: Lightweight single-stage detectors such as YOLO (the latest family of models) for identifying products on the shelf.
### Pose and Grasp Estimation
Hybrid approaches (RGB + Depth). For example, a fast 2D detector defines the region of interest, after which classic computer vision algorithms (PCL, OpenCV) analyze the point cloud to accurately calculate the grasp point and gripper orientation.
### Motion Planning
MoveIt 2 using Task Constructors to generate collision-free manipulator trajectories.

## Work plan (lab1)
### Stage 1: Requirements Analysis and Architecture Design
Specification: Clearly define the product range (geometry, weight, packaging type). This will determine the choice of gripper type (parallel/vacuum) and gripping algorithms.
System Design: Develop a general diagram of the system nodes in ROS2: navigation, perception (machine vision), manipulator control, and master nodes (Behavior Tree) for orchestration.
Technology Stack Selection: Finalize versions of ROS2 (Humble/Iron), simulator (Gazebo), and libraries (OpenCV, PyTorch/TensorFlow).
### Stage 2: Modeling and Simulation
Creating a Digital Twin: Assembling a robot model (URDF/XACRO) in the simulator (Gazebo) along with a store model (shelves, products).
Navigation Practice: Implementing robot movement between points (warehouse-rack) using ROS2 Nav2. Creating a room map.
Perception Simulation: Setting up placeholders for cameras (RGB-D) that emulate data for subsequent replacement with real algorithms.
### Stage 3: Vision Core Development (in simulation and on test data)
Dataset Creation: Collecting and labeling product images (or synthesizing data in the simulator).
Detector Training: Training a YOLO model (or similar) to detect products and, possibly, determine free space on a shelf.
Grip Planning Development: Creating a node that, using a 2D box and depth map, calculates the 3D position of a product and generates an optimal grasping trajectory.
### Stage 4: Integration and debugging on a real robot (or in advanced simulation)
Calibration: Fine-tuning the transformations (tf2) between the camera, gripper, and robot base coordinate systems. This is a critical step for successful grasping.
Behavior Integration: Assembling the full puzzle in the Behavior Tree: navigate to shelf -> activate vision -> grasp -> navigate to stowage location -> stowage.
Error Handling: Adding rescheduling logic if an item is not found or the grasp fails on the first attempt.
### Stage 5: Testing, Optimization, and Deployment
Load Testing: Verifying the search-grab cycle time (target < 5 seconds).
Runtime Testing: Verifying performance under different lighting conditions, partial object occlusion, and navigation failures.
Documentation and Deployment: Preparing documentation and creating the final software image.
