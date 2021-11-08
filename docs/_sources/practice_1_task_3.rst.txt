P1 Task 3 - Obstacle Avoidance
==============================

.. note:: When finished, submit the iRobot project code of your solution in Moodle

The goal of this task is to **avoid hitting the obstacles** (required) and **do this until the robot reaches the end of the playground** (required). If you zoom out in the simulation environment, 
you can find five blocks that you can move around (see figure 3). Place those blocks into the environment and program the robot to change its course when it hits an obstacle.
Use the bumber sensors (``@event(robot.when_bumped)``) to detect whether the robot has touched an obstacle. Use the ``colour_scanned`` event to detect
when the robot reached the end of the playground. 

.. figure:: /figures/irobot_root/p1_t3.gif
    :scale: 60%
    :align: center

    **Figure. 3:** Outcome of task 3
 