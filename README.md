# Robot_Toolpath_Demo

![Cobot Welding Setup](images/cobot%20welding%20setup2.png)


## Overview

A simulation-only workflow to generate and test robotic welding-style motion over STL-derived toolpaths using a 6-axis Universal Robot in RoboDK.

## Inspiration

Inspired by [this video](https://youtu.be/3THLTQsrem0?si=78Qb_iuWX5MGSNpV), which showcases a KUKA robotic arm performing large-scale additive manufacturing (welding/deposition), I set out to prototype a similar approach using a Universal Robot model. While the hardware differs, the same principles of motion planning and deposition path simulation apply.

## Workflow

1. **Model Acquisition**

   * I sourced a print of the 75-4-106 part, obtained its dimensions, and modeled it in Fusion 360.
   * Exported the model as an STL file for toolpath generation.

2. **Toolpath Generation**

   * Used the slicer application **Slic3r** to convert the STL into G-code representing layer-by-layer deposition paths.
   * Imported the G-code into RoboDK to generate a robot-followable toolpath.

3. **Robot & Tool Setup**

   * Loaded a 6-axis Universal Robot from the RoboDK library for its simplicity and ease of integration.
   * Defined and calibrated a Tool Center Point (TCP) to mimic a welding torch.

4. **Motion Programming**

   * Assigned path-following behavior to the robot.
   * Configured motion settings such as orientation, speed, and approach/retract distances.

5. **Simulation Execution**

   * Simulated the deposition motion in RoboDK.
   * Validated robot reachability, joint limits, and tool alignment across layers.

6. **Welding Config Planning**

   * Planned deposition sequence, direction, and simulated welding signals.
   * Prepared logic for arc-on/arc-off behavior in a real-world setup.

7. **Limitations**

   * Due to RoboDK license limitations, the project remained within simulation.
   * Real-world post-processing and robot code export were not executed.

## Skills Demonstrated

| Area                  | Description                                          |
| --------------------- | ---------------------------------------------------- |
| 3D Model Integration  | CAD modeling in Fusion 360, STL export               |
| G-code Generation     | Used Slic3r to slice STL into additive-style G-code  |
| G-code Interpretation | Converted G-code into curve-based robot paths        |
| Robot Programming     | Offline simulation of Universal Robot with TCP setup |
| Motion Control        | Path orientation, speed, and process planning        |
| Process Planning      | Simulated WAAM-style robotic deposition              |
| Licensing Awareness   | Operated effectively within RoboDK trial limitations |

## Notes

This simulation project provides a base for future real-world robotic welding or additive manufacturing applications. The use of a Universal Robot simplified setup and motion testing, making it ideal for fast prototyping within RoboDK.
