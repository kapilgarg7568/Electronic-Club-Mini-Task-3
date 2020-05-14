# MicroMouse Maze
**Problem Statement**: To make a fully autonomous bot which can solve the maze without hitting the wall.

## Required Components
**Square shape board of Plastic for Chassis**:Easily available and can be drilled easily.

**2 DC motors with encoders and wheels:** I think should do the job for us as the encoder will detect the speed of motor, direction of rotation, distance it hs travelled and its feedback data enables us to control motor speed and direction efficiently.

**Castor ball wheel**

**Ultrasonic HC-SR04 rangefinder**:We need 3 HC-SR04 sensors for this project one in the front and two on the the sides. It provides 2 to 400 cm non contact measurement with a ranging accuracy of 3mm. It is easy to set up and has additional control circuitry that can prevent inconsistent bouncy data.

[ HC-SR04 Datasheet ](https://cdn.sparkfun.com/)

**Small piece of Breadbord**: As it will be handy for us to make connection of three ultrasonic sensor, dc motor to Arduino.

**Arduino UNO**:Its easy to use and much cheaper in compared to Arduino Nano and ESP32. It's not that big in size and fulfil our requirement for this projecet.

**Arduino Motor Shield**:Its based on L298 and can be used to drive two DC with Arduino board, controlling the speed and direction of each one independently.

More information on [ L298 ](https://www.st.com/en/motor-drivers/l298.html)

**Power Supply**: A 5V batery with 2000mAh should work for our project requirement.

## Overall Structure
Complete structure will look like a cuboid. On the upper part of chassis battery will be palced and in the middle part of chassis there will be arduino with arduino motor shield, all three ultrasonic sensor and wiring connections. Under the chassis 2 DC motors with wheels on side and a castor ball wheel in front will be attached.

## Algorithm
There are various maze solving algorithm out there but we have to selelct one which suits best for us.
**Random Mouse**:It is trivial method of solving a maze in which it proceed the current passage untill a junction is reached and then make a random decision about the direction to follow(as  the name suggests).Its quite unintelligent way and inefficient.

**Wall Follower**:If the maze's walls are simply connected then keeping contact with one wall of the maze solver is guaranteed not to get lost but if if walls are conected differntly then it may be deformed into a loop.
and we cant use this method as it is clearly written in problem statement that simple wall following micromouse wont be able to solve the maze so we have to opt for a differnt algorithm.

**Pledge Algorithm**: In this method of solving maze firstly it goes into an arbitrarily choosen direction and then when an obstacle is met, one hand is kept along the obstacle or wall while angles turned are counted and it takes its further actions on the basis of 'sum of turns made' and 'current heading'.

**FloodFill Algorithm**:Flood Fill algorithm is one of the best maze solving algorithms. The flood fill algorithm involves assigning values to each of the cells in a maze where these values represent the distance from any cell on a maze to the destination cell. So we shall go with it.

More information on [ FloodFill Algorithm ](https://www-freecodecamp-org.cdn.ampproject.org/v/s/www.freecodecamp.org/news/flood-fill-algorithm-explained/amp/?amp_js_v=a3&amp_gsa=1&usqp=mq331AQFKAGwASA%3D#aoh=15894031810366&csi=1&referrer=https%3A%2F%2Fwww.google.com&amp_tf=From%20%251%24s&ampshare=https%3A%2F%2Fwww.freecodecamp.org%2Fnews%2Fflood-fill-algorithm-explained%2F)







