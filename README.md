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
