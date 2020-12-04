P1 Exercise 4 - Events
======================

Events are external processes, such as button presses, that cause the robot to react. So far our code has been written 
linearly, meaning that all functions, such as ``move`` and ``rotate``, are called out in a known sequence. Events on the 
other hand happen … well … whenever they happen. You cannot tell exactly when someone walks into your room, when exactly 
it starts to rain, or when there is an obstacle in front of the robot that triggered a bumper sensor. 

In a programming environment, a specific event is usually associated with a callback function, which is executed whenever 
the event happens. For example in figure 4 you can see two types of callback functions: ``robot.whenTouched`` 
which is called when you press a button on top of the robot, and ``robot.whenBumperPressed`` which is called when you hit 
the robot's bumper.
 

.. figure:: /figures/irobot_root/irobot_tutorial_events.gif
    :width: 650px
    :align: center

    **Figure. 4:** An example of event based robot control. iRobot project code 4NGY4 
 
 