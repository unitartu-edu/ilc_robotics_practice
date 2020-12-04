P1 Exercise 5 - Loops
=====================

Loops are yet another technique to automate repetitive behaviours, thus making you code and development time shorter. 
There are different types of loops, and here we’re going to introduce for-loops, while-loops and nested loops.

For-Loops
---------

For-loops are used when something has to be repeated for a fixed number of periods. Figure 5.1 shows a use-case 
of a for-loop, where the task is to draw a limited number of dashes. Each cycle of the for-loop draws one dash but the 
loop is repeated for 5 times, resulting in this neat little dashed line.

.. figure:: /figures/irobot_root/irobot_tutorial_for_loop.gif
    :width: 650px
    :align: center

    **Figure. 5.1:** An example of a for-loop. iRobot project code DXZHV
 

While-Loops
-----------

While-loops are useful if the robot must do something while a specific condition is true. For example have a look at 
figure 5.2. When the program is started, a couple of variables are initialized, most importantly a variable 
called ``move_robot``. Then the program enters the while-loop and stays in there while the ``move_robot`` is equal to ``true``. 
The robot would be in this loop forever unless something changed the ``move_robot`` variable to ``false``, which is done 
in the ``robot.whenTouched`` event (see the events exercise).

.. figure:: /figures/irobot_root/irobot_tutorial_while_loop.gif
    :width: 650px
    :align: center

    **Figure. 5.2:** An example of a while-loop. iRobot project code Y2KQK

Nested Loops
------------

Nested loop is when you have one loop inside another. This is useful for programming behaviours like “*For every floor 
in this building, clean up every room on each floor*”. An example of a nested loop can be seen on figure 5.3, 
where the robot draws a dashed octagon.

.. figure:: /figures/irobot_root/irobot_tutorial_nested_loop.gif
    :width: 650px
    :align: center

    **Figure. 5.3:** An example of a nested loop. iRobot project code ZSKAN