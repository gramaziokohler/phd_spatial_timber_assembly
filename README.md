# PhD - Spatial Timber Assembly

This is a gateway repository consisting the PhD work by Victor Leung in Gramazio Kohler Research. 

The PhD work is a [crossdisciplinary][crossdisciplinary] project that involves architectural design, process design and mechatronic design. In order to keep different code (C++, Python, Matlab Code), collected data (sensor measurements), documentation (Markdown) and design files (Rhino, Inventor) into manageable and maintainable repository, they are separated into different repository that are listed below. 

The rationale for this arrangement:

- Allow collaborators to clone only their relevant repository.
- Simplify gitignore setup for different code types
- Certain repo are reusable and are organized as installable package

## What is this project about

**Short Version:** This project is about using robotic arms (in RFL) and distributed robotic clamps (designed by me) to assemble timber structures. State of the art automation in this area had only successfully automate flat walls and floor component but not spatially jointed structures (3D instead of 2D). 

This project believes that when a robust lights-out-ready automation is achieved for spatial timber structures, there will be new opportunities for timber structural design.

**Long Version:** You can read the [detailed research plan](200408_270_ResearchPlan_Submitted_v7.pdf).

## Architectural Design Repos

[integral_timber_joints](https://github.com/gramaziokohler/integral_timber_joints/) ![Python Version](https://img.shields.io/badge/Python-cpython%202.x%20%7C%203.x%20%7C%20ironpython%202.7-darkgreen) ![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)

- Library for modeling timber elements and timber joints in a COMPAS friendly data structure. Includes:
  - Conversion from Rhino geometry
  - Visualization in Rhino as Rhino geometry
  - Conversion functions to BTL for fabrication (TODO). 
- Library (TODO) for computing assembly sequence, assembly direction

itj_experiments ![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)

- Repository for physical experiments. Includes 3D models of the designed structure and lab/robot setup.
  - Assembly Experiments
  - Robotic Action Experiments (RFL Robots and Clamps)

[itj_design_study](https://github.com/gramaziokohler/itj_design_study) ![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)

- Repository for digital design studies (occasionally include physical prototypes). Includes 3D models, robotic simulation and visualization files.

## Process Design Repos

[itj_process](https://github.com/gramaziokohler/itj_process) ![Python Version](https://img.shields.io/badge/Python-cpython%202.x%20%7C%203.x%20%7C%20ironpython%202.7-darkgreen)

- COMPAS friendly data structure for describing robotic processes. This is separated into 
  - High level process description (e.g pick up tool, pick up element, let go tool, let go element, etc...)
  - Low level action description (e.g. move robot arm to this pose with MoveJ / MoveL or Along Planned Path, assert IO output, synchronized move for robot and clamps)
- Functions (TODO) to parse high level process description to low level action description. Based on available tool / robot setup and element geometry. 
- Functions (TODO) to optimize process sequence and remove redundant processes.
- Python based process controller (TODO) to execute a sequence of actions.
  - Maintains main event loop for sequential execution of actions, monitoring sensors, handling interrupt.
  - UI for starting, pausing and resetting a process. 
  - Communicate to robotic backends via ROS:
    - RFL robot controller(via [compas_rrc_driver](https://github.com/gramaziokohler/compas_rrc_ros)) 
    - clamp_controller backend (via [clamp_controller](https://github.com/gramaziokohler/clamp_controller))

## Mechatronics Design Repos

[clamp_electronics](https://github.com/gramaziokohler/clamp_electronics) ![Eagle Version](https://img.shields.io/badge/Eagle-9.6-darkgreen)

- Electronics schematics, PCB design for remote controlled clamps.

[clamp_firmware](https://github.com/gramaziokohler/clamp_firmware) ![VS Version](https://img.shields.io/badge/Visual%20Studio-2017-darkgreen) ![VisualMicro Version](https://img.shields.io/badge/Visual%20Micro-20.03+-darkgreen) ![Arduino Version](https://img.shields.io/badge/Arduino%20IDE-1.6,%201.8-darkgreen)

- Arduino firmware for motion control and remote communication.

[clamp_controller](https://github.com/gramaziokohler/clamp_controller) ![Python Version](https://img.shields.io/badge/Python-cpython%203.x-darkgreen) ![ROS Version](https://img.shields.io/badge/ROS-kinetic-darkgreen) 

- Python-based controller to communicate with a network of distributed clamps. The backend can be interfaced through:
  - UI for monitoring and commanding clamps
  - via ROS topic 
- Python functions (via [roslibpy](https://github.com/gramaziokohler/roslibpy)) for process controller to issue clamp commands via ROS.



[crossdisciplinary]: https://www.researchgate.net/post/What_is_difference_between_terms_of_multidisciplinary_transdisciplinary_and_cross_disciplinary_approaches	"What is difference between terms of multidisciplinary, transdisciplinary and cross disciplinary approaches?"

