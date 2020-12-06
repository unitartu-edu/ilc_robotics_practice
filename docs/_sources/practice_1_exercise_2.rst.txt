P1 Exercise 2 - Variables
=========================

Ultimately as a robot programmer or any kind of programmer for that matter, the faster you can work with your code, 
the better. The concept of variables is great in that regard. For example, have a look at the figure 2.1. 
In that depicted example the robot is programmed to follow a triangular path, where each side of the triangle is equal. 
Now a variable is introduced for the length of the triangle’s side called ``distance`` and also a variable for the 
triangle’s ``angles``. Through those variables we could easily define a larger triangular path by just changing the 
value of the ``distance`` variable, instead of modifying all the ``robot.move`` commands.

In a larger program, one could easily have tens or even hundreds of instances, where a certain value is needed, such 
as the size of the robot’s wheel. If the robot’s wheel is changed, the programmer could easily modify the code for the 
new wheel size by just changing the according variable. 

.. warning:: Initialize your variables below the ``robot.whenProgramStarted()`` line, otherwise the iRobot environment will crash (screen goes gray), see figure 2.2

.. figure:: /figures/irobot_root/irobot_tutorial_variables.gif
    :width: 650px
    :align: center

    **Figure. 2.1:** An example use of variables. iRobot project code RU8DA 

|

.. figure:: /figures/irobot_root/irobot_tutorial_variables_bug.gif
    :scale: 70%
    :align: center

    **Figure. 2.2:** iRobot environment crashes if you try to initialize the variables above the ``robot.whenProgramStarted()`` line, where the variables are defined
 
 