# Robot_Toolpath_Demo

![Cobot Welding Setup](images/cobot%20welding%20setup2.png)

---

## Overview

This project showcases a **simulation-only workflow** using RoboDK to generate and test robotic welding motion based on a 3D model. A **6-axis Universal Robot arm** was used to simulate toolpath execution over complex geometry derived from an STL file.

The goal was to demonstrate an understanding of:

* Robotic arm kinematics and joint constraints
* G-code fundamentals and how robotic toolpaths relate to traditional CNC workflows
* STL slicing for layered deposition or path generation
* Tool orientation control for consistent welding simulation
* Offline programming principles common in industrial robot applications

---

## Inspiration

Inspired by [this video](https://youtu.be/3THLTQsrem0?si=78Qb_iuWX5MGSNpV), which showcases a KUKA robotic arm performing large-scale additive manufacturing (welding/deposition), I set out to prototype a similar approach using a Universal Robot model. While the hardware differs, the same principles of motion planning and deposition path simulation apply.

---

## Workflow

1. **Model Acquisition**

   * Sourced a print of the 75-4-106 part and obtained its dimensions.
   * Downloaded the part in Fusion 360 and exported as STL.

2. **Toolpath Generation**

   * Used **Slic3r** to slice the STL file and generate G-code for layer-by-layer deposition.
   * Instead of using RoboDK’s built-in G-code to curve tool, I wrote a custom Python script using the RoboDK API to parse and execute the G-code line by line.
   * This workaround allowed me to visualize and simulate complex G-code motion paths directly in RoboDK without relying on the licensed post-processor.

   ![Shell G-code Path Result](images/shellgcodestlpath.png)

3. **Robot & Tool Setup**

   * Selected a 6-axis Universal Robot from the RoboDK library.
   * Calibrated a Tool Center Point (TCP) to represent a welding torch.

4. **Motion Programming**
   ![Toolpath Execution Animation](images/showcaseshelledgi.gif)
   <p align="center"><i>RoboDK simulation of the parsed G-code shell toolpath using Python</i></p>

   * Assigned curve-following behavior to the robot.
   * Configured motion settings: orientation, travel speed, and retract distances.

5. **Simulation Execution**

   * Simulated the full deposition sequence in RoboDK.
   * Validated joint reachability, tool orientation, and layer alignment.

6. **Welding Config Planning**

   * Planned process logic that could be implemented in real-world code.

7. **Limitations**

   * The project was limited to simulation due to RoboDK license restrictions.
   * Code export and real-world execution were not performed.

---

## Skills Demonstrated

| Area                  | Description                                          |
| --------------------- | ---------------------------------------------------- |
| 3D Model Integration  | CAD modeling in Fusion 360, STL export               |
| G-code Generation     | Used Slic3r to slice STL into additive-style G-code  |
| G-code Interpretation | Used Python + RoboDK API to simulate full paths      |
| Robot Programming     | Offline simulation of Universal Robot with TCP setup |
| Motion Control        | Path orientation, speed, and process planning        |
| Process Planning      | Simulated WAAM-style robotic deposition              |
| Licensing Awareness   | Bypassed export limits by scripting toolpath control |

---

## Notes

This simulation project provides a strong foundation for real-world robotic welding and additive manufacturing. Leveraging RoboDK and a Universal Robot model allowed fast prototyping, toolpath testing, and motion analysis without requiring physical hardware. The addition of custom Python-based G-code parsing showcases a flexible and license-friendly approach to robotic toolpath execution.
