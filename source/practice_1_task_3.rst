P1 Task 3 - Obstacle Avoidance
==============================

.. note:: When finished, submit the iRobot project code of your solution in Moodle

The goal of this task is to avoid hitting the obstacles and do this until the robot reaches the end of the playground. If you zoom out in the simulation environment, 
you can find five blocks that you can move around (see figure 3a). Place those blocks into the environment and program the robot to change its course when it hits an obstacle 
(see figure 3b). Use the bumber sensors (``@event(robot.when_bumped)``) to detect whether the robot has touched an obstacle. Use the ``colour_scanned`` event to detect
when the robot reached the end of the playground. 

.. figure:: /figures/irobot_root/task_circle_runner.gif
    :scale: 40%
    :align: center

    **Figure. 3:** Outcome of task 3
 