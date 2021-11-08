P2 Task 1 - Obstacle Avoidance (Advanced)
=========================================

.. note:: Practice 2 is optional. You don't have to do it if you don't feel like it. But its way more challenging and hence fun

The objective of this task is to design a controller, that **on average** solves the *"Obstacle Avoidance"* challenge at least 5 seconds quicker than 
the default controller, which is 61 s. So again, the time you have to beat is ``61 s - 5 s = 56 s`` and your controller's performance 
should be evaluated on at least 15 samples (run your best controller for 15 times). In this case we rule out any lucky shots. Scroll down for further 
instructions and tips.

After you are done with your controller, submit the following things in Moodle:
 * your Robotbenchmark username
 * the code of your controller (just a simple copy/paste)

After the submission deadline, the student who submitted the best controller will get a prize!

.. note:: You have to be logged in to the Robotbenchmark.net to save your results

.. figure:: /figures/webots/webots_task_1.png
    :scale: 45%
    :align: center

    **Figure. 1:** Environment for the obstacle avoidance taks

Getting You Going
-----------------

The default controller already might seem too complicated, but take your time and examine what's going on in the code line-by-line. 
Make sure you read the instructions provided in the simulator. Over there you will be told, that the robot has 5 distance sensors which 
are used for detecting obstacles. Each sensor will output a number that signifies the distace between the sensor and 
the closest object in front of it.

The default controller is already avoiding obstacles, but it does not know where it's supposed to go (the robot has to cross the 
red line in the other side of the room). For that, the instructions give you a hint that you can use a compass that's "built-in" 
to the robot. Yet for some it might be bit tricky to set-up the compass in the Python code.

Therefore you will be given a slight advantage: below you can find the default controller with the compass related code 
already included into the script. It's up to you how you use it.

.. code-block:: python

    """Braitenberg-based obstacle-avoiding robot controller."""

    import math                    # Import math Library, we need it to calculate the tangent
    from controller import Robot   # Import the Robot class
    from controller import Compass # import Compass module

    # Get reference to the robot.
    robot = Robot()

    # Get simulation step length.
    timeStep = int(robot.getBasicTimeStep())

    # get robot's Compass device
    compass = robot.getCompass("compass")

    # enable the Compass
    compass.enable(timeStep)

    # Constants of the Thymio II motors and distance sensors.
    maxMotorVelocity = 9.53
    distanceSensorCalibrationConstant = 360

    # Get left and right wheel motors.
    leftMotor = robot.getMotor("motor.left")
    rightMotor = robot.getMotor("motor.right")

    # Get frontal distance sensors.
    outerLeftSensor = robot.getDistanceSensor("prox.horizontal.0")
    centralLeftSensor = robot.getDistanceSensor("prox.horizontal.1")
    centralSensor = robot.getDistanceSensor("prox.horizontal.2")
    centralRightSensor = robot.getDistanceSensor("prox.horizontal.3")
    outerRightSensor = robot.getDistanceSensor("prox.horizontal.4")

    # Enable distance sensors.
    outerLeftSensor.enable(timeStep)
    centralLeftSensor.enable(timeStep)
    centralSensor.enable(timeStep)
    centralRightSensor.enable(timeStep)
    outerRightSensor.enable(timeStep)

    # Disable motor PID control mode.
    leftMotor.setPosition(float('inf'))
    rightMotor.setPosition(float('inf'))

    # Set ideal motor velocity.
    initialVelocity = 0.7 * maxMotorVelocity

    # Set the initial velocity of the left and right wheel motors.
    leftMotor.setVelocity(initialVelocity)
    rightMotor.setVelocity(initialVelocity)

    while robot.step(timeStep) != -1:

        # Read the raw values from the compass and convert them to a heading angle
        compass_raw_values = compass.getValues()
        heading_raw = math.atan2(compass_raw_values[0], compass_raw_values[2]);
        heading = (heading_raw - 1.5708) / 3.1416 * 180.0

        if (heading < 0.0):
            heading = heading + 360.0

        # It is up to you how you use the "heading" to direct the robot. You can print the values to the
        # console but this slows the simulation down significantly. Just have a look at the vaules and then 
        # comment it out

        # print ("heading = " + str(heading))

        # Read values from four distance sensors and calibrate.
        outerLeftSensorValue = outerLeftSensor.getValue() / distanceSensorCalibrationConstant
        centralLeftSensorValue = centralLeftSensor.getValue() / distanceSensorCalibrationConstant
        centralSensorValue = centralSensor.getValue() / distanceSensorCalibrationConstant
        centralRightSensorValue = centralRightSensor.getValue() / distanceSensorCalibrationConstant
        outerRightSensorValue = outerRightSensor.getValue() / distanceSensorCalibrationConstant

        # Set wheel velocities based on sensor values, prefer right turns if the central sensor is triggered.
        leftMotor.setVelocity(initialVelocity - (centralRightSensorValue + outerRightSensorValue) / 2)
        rightMotor.setVelocity(initialVelocity - (centralLeftSensorValue + outerLeftSensorValue) / 2 - centralSensorValue)
