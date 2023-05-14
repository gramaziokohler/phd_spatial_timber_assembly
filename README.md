# PhD - Spatial Timber Assembly

This is a gateway repository for the PhD work by Pok Yin (Victor) LEUNG in ETH Zurich, under the supervision of Prof. Matthias Kohler, Prof. Fabio Gramazio (Chair of Architecture and Digital Fabrication) and Prof. Dr. Agathe Koller (Professor of Mechatronics and Automation Technology at the Rapperswil University of Applied Sciences in Switzerland).

The PhD work is a [crossdisciplinary][crossdisciplinary] project that involves architectural design, process design and mechatronic design. In order to keep different code, documentation, experimental data, execution logs, and design files into manageable and maintainable repository, they are separated into different repository that are listed below. 

The rationale for this arrangement:

- Allow collaborators to clone only their relevant repository.
- Simplify gitignore setup for different code types
- Certain repo are reusable and are organized as installable package
- Certain repo were not public until end of PhD

## What is this project about

### Short Version

This project is about using robotic arms in collaboration with custom-designed Distributed Robotic Tools (DiRT) to assemble spatial timber structures. The system can address:

- Inaccurate spatial manipulation that is inherit to large scale robotic platforms.
- Assembly of tight fitting joints that require perfect alignment and large assembly force.

### Research Plan

You can read the [detailed research plan](200408_270_ResearchPlan_Submitted_v7.pdf).

### Thesis Abstract

This thesis investigates the potential of distributed robotics systems in automating the assembly of timber structures, addressing the challenges of large-scale spatial manipulation and tight-fitting timber joint assembly, which are highly relevant for timber construction.

Leveraging the highly automated process of machining timber parts using automatic joinery machines, the thesis investigates the next knowledge gap in the design-to-production workflow - automatic spatial assembly. Using timber frame structures with integral timber joints as a starting point, this thesis proposed a new fabrication system using distributed robotic tools (DiRT) in collaboration with industrial robotic arms. The crucial breakthrough is the modular and remote operation nature of the tools, allowing the system to assemble a wide variety of timber joints and complex structures.

This thesis also investigated an integrated design workflow. Design validation is identified as a critical aspect of the automated assembly process. This research proposes a practical three-tier validation process to evaluate a design, with quick feasibility feedback provided to the designer during the design process. It takes into consideration geometrical conflicts, robot limitations and tool setup to provide visual feedback on various problems to the designer. 

The research provides a proof-of-concept through the development of three full-scale timber frame demonstrators, each assembled using a single robotic arm and a set of custom-designed distributed assembly tools. The assembly tools include robotic clamps and screwdrivers for different types of lap joints, including planar and non-planar varieties. The findings showcased a viable method to assemble timber structures, mitigating well-known problems such as accumulated assembly error and instability during construction. The results also identified key challenges that are limiting the system efficiency, accuracy, reliability and success rate for the automated process, as well as discovering new opportunities for future research. These opportunities include establishing a generalizable DiRT assembly system, and expanding the range of joint types and building components that can be assembled.

The thesis contributes software tools and system design patterns that are generalizable and reusable within the broader digital fabrication and construction automation community. For example, software for remote robot operation and synchronisation; Data structures and algorithms for robotically assembled structures; Methods for automating parsing designs into robotic programmes; and Task and motion planning techniques for assembly problems.

Ultimately, this research contributes to ongoing efforts to harness the potential of robotics for creating more efficient and sustainable timber construction processes. Paving the way for the widespread adoption of automated construction processes within the architectural industry.

## Design Repositories

**[integral_timber_joints](https://github.com/gramaziokohler/integral_timber_joints/)** ![Python Version](https://img.shields.io/badge/Python-cpython%202.x%20%7C%203.x%20%7C%20ironpython%202.7-darkgreen) ![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)

- Library for modeling timber elements and timber joints in a COMPAS friendly data structure. Includes:
  - Conversion from Rhino geometry
  - Visualization in Rhino as Rhino geometry
- Library for computing assembly sequence, assembly direction

**[itj_design_study](https://github.com/gramaziokohler/itj_design_study)** ![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)![JSON](https://img.shields.io/badge/-json-black)

- Repository for digital design studies (also include physical prototypes). Includes Rhino 3D models, robotic simulation and visualization files.
  - Assembly Models are in json format, based on the compas library, requires [integral_timber_joints](https://github.com/gramaziokohler/integral_timber_joints/) library for decoding. 


## Mechatronics Design Repos

**[clamp_hardware](https://github.com/gramaziokohler/clamp_hardware) **![Rhino Version](https://img.shields.io/badge/Rhino-6-darkgreen)

- DiRT Tools Hardware Design (Clamps, Screwdrivers, Grippers, Docking Adapter, Cable Guides, Scaffolding, Screws, Platform)

**[clamp_electronics](https://github.com/gramaziokohler/clamp_electronics)**![Eagle Version](https://img.shields.io/badge/Eagle-9.6-darkgreen)

- Electronics schematics, PCB design for remote controlled clamps.

## Control Repositories

**[itj_process_controller](https://github.com/gramaziokohler/itj_process_controller) **![Python Version](https://img.shields.io/badge/Python-cpython%202.x%20%7C%203.x%20%7C%20ironpython%202.7-darkgreen)

Level 3 Controller to execute planned tasks. It communicates to various Level 2 controllers via ROS:

- RFL Robot Controller (via [compas_rrc_driver](https://github.com/gramaziokohler/compas_rrc_ros)) 
- DiRT Tools Controller backend (via [clamp_controller](https://github.com/gramaziokohler/clamp_controller))
- Vision-Guided Docking Controller

**[clamp_controller](https://github.com/gramaziokohler/clamp_controller)** ![Python Version](https://img.shields.io/badge/Python-cpython%203.x-darkgreen) ![ROS Version](https://img.shields.io/badge/ROS-kinetic-darkgreen) 

- Level 2 Controller for coordinate Distributed Robotic Tools (DiRT) via radio link. It receives commands from Level 3 Controller and relays the commands to a network of distributed tools. It provides a GUI for monitoring telemetry and sending commands to the distributed devices. The lower level controllers are embedded firmware:

**[clamp_firmware](https://github.com/gramaziokohler/clamp_firmware) **![VS Version](https://img.shields.io/badge/Visual%20Studio-2017-darkgreen) ![VisualMicro Version](https://img.shields.io/badge/Visual%20Micro-20.03+-darkgreen) ![Arduino Version](https://img.shields.io/badge/Arduino%20IDE-1.6,%201.8-darkgreen)

Level 1 Embedded Controller (Arduino firmware) for motion control and remote communication.

- Clamp Firmware

- Screwdriver Firmware
- ESP32 Camera Firmware

**[Vision-Guided Docking Controller](https://github.com/gramaziokohler/clamp_controller/tree/master/src/visual_docking)** ![Python Version](https://img.shields.io/badge/Python-cpython%203.x-darkgreen) ![ROS Version](https://img.shields.io/badge/ROS-kinetic-darkgreen) 

Level 2 Vision-Guided Docking Controller for remote marker based 

[crossdisciplinary]: https://www.researchgate.net/post/What_is_difference_between_terms_of_multidisciplinary_transdisciplinary_and_cross_disciplinary_approaches	"What is difference between terms of multidisciplinary, transdisciplinary and cross disciplinary approaches?"

