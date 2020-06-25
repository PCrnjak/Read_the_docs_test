
Electronics and PCB
===========================

.. meta::
   :description lang=en: info about Electronics and PCB.
   
All electronics can also be bought from ebay and similar sites. 

.. Tip::

   From experiance i found out that cheaper stepper drivers tend to make more noise, so if you want quiet robot arm buy more expensive      drivers.


PCB V1
------------
This PCB is first version and has some errors that will be fixed in revision 2.
Board was created in Altium Circuitmaker and all files can be found here:
https://github.com/PCrnjak/Faze4-Robotic-arm/blob/master/Distribution_PCB.zip

.. figure:: ../docs/images/plocica_v1.jpg
    :figwidth: 400px
    :target: ../docs/images/plocica_v1.jpg

Upper section of PCB are Inputs for limit switches and inductive sensors. All inputs on top are isolated with optocouplers. I did that since all wires of the arm are going thur same spot, that means "high voltage" stepper wires were near low voltage limit switch wires. That caused promblems where steppers induced enough voltage on limit switch wires to trigger interupts on teensy. That is why limit switches and sensors are connected to 24v.

left side is for stepper outputs. There are also 2 stepper outputs on bottom right side.

Bottom right side has 5V input and 24V input. You need both for arm to work. In the middle we have few extra serial ports and OLED display.

When wiring stepper drivers to the PCB i used TB6600  driver pinout as reference.I planned for all drivers to be connected like picture below. HIGH signal on ENABLE + pin would enable stepper drivers. Now i made some mistakes and not all drivers can be connected like that. In 

.. figure:: ../docs/images/stepper_connection.png
    :figwidth: 400px
    :target: ../docs/images/stepper_connection.png
    
Now i made some mistakes and not all drivers can be connected like that. In picture below you can see how to connect all drivers. As you can see for joint 5 (connector below top one) i switched enable and puls pins. That means that puls5 pin ( pin 38 on teensy) is connected to puls pin on stepper driver. I also skipped Port that has no 5V level shifters since it didnt work well.

.. figure:: ../docs/images/sim_plocica_with_labels.png
    :figwidth: 400px
    :target: ../docs/images/sim_plocica_with_labels.png


