# Hydroelectric Power Plant Automation
A simulation project carried out in Siemens Step 7 and WinCC. Programming languages used - Ladder Logic, Functional Block Diagram and Structured Text.

## Project Description
The objective here is to program a control system for a hypothetical hydroelectric power plant. A base program has been provided to simulate a changing environment and it gives analog and digital input signals accordingly. My task was to write a program that incorporates these signals and control various analog and digital devices in order to run the system in a safe and stable manner. Additionally, I created an HMI that will allow a control operator to easily and effectively interact with the control system.

## Theory of Operation
![alt text](https://github.com/Pravin93-Murugesan/Hydroelectric-Power-Plant-Automation/blob/master/Process-Overview.png)
The process parameters in the yellow box are continuously monitored. The parameters in the green box is controlled with a PID.

As shown in the image, the power plant is an impoundment facility in the dam. River water stored in the reservoir is released and flows through a turbine, rotating it, which in turn activates an electromagnetic generator to produce electricity. The water flows through a gate in the intake house that we control via a servo motor. By changing the opening degree of the gate, we speed up or slow down the flow through the turbine resulting in a higher and lower RPM respectively.

As the turbine blades turns faster, the main-shaft bearings heat up. An oil pump controlled by a VFD, pumps oil to the bearings to cool them down. Oil flow and temperature is monitored to ensure that these parameters are within safe limits. Once the power generated gets high enough, an interlock to the energy grid is closed. This allows the generator to produce power and send it to the power station. If anything goes wrong, an alarm is notified to the perator in the control room. The system has an emergency stop push button.

## Inputs & Outputs
#### Digital Inputs
System start, Emergency stop

#### Digital Outputs (To energize)
Intake house gates servo motor, Oil pump VFD, Alarm horn, Turbine brake, Power station interlock

#### Analog Inputs
Oil flow, Oil temperature, Turbine RPM, Power generated

#### Analog Outputs
Intake house gates servo motor, Oil pump VFD

## Alarm Conditions
Alarms are set to turn on when process parameters exceed certain limits. They are for:
 - Low oil flow
 - High oil flow
 - High oil temperature
 - Turbine overspeed
 - Turbine brake failure
 - Emergency stop

## System Modes and Sequence of Operation
The different modes are briefed below and occur sequentially as listed. They are set up as steps of the sequence in a GRAPH program block. 
#### Warmup Mode
When Start pushbutton is pressed, the sequence begins with this step. Allows the turbine to turn at a speed of 30 RPM and runs the oil pump at a low output level (5 GPM) until the oil temperature reaches 150 degree celsius. Once this is established and maintained for at least 10 seconds, the system transitions into the next mode.

#### Stabilize Mode
Turbine should speed up and result in the generator producing a desired kW output. Once that is stable within (+/-) 5 kW of the setpoint for at least 10 seconds, the system transitions into the next mode.

#### Generation Mode
Keep everything running and close the power station interlock. Now power is supplied to the energy grid.

#### Cooldown Mode
Once the Stop button has been pushed, power station interlock is opened, turbine turns at a low speed of 20 RPM, and a high oil flow is maintained to the main-shaft bearings until the oil temperature is below 150 degree celsius. Once this is established and maintained for at least 10 seconds, the system transitions into the idle mode.

#### Idle Mode
Power station interlock and intake house servo motor are deenergized and the turbine brake is engaged. In addition, when an alarm is triggered, the sequence should be aborted and the system should go into Idle mode.

## Other project details
I have also added blocks of code for the following:
 - Initializing the simulation (all the setpoints, delay time, push buttons are configured at the start)
 - Hand-Off-Auto / Local-Off-Remote pushbuttons set up for the devices (Intake house gates servo motor, Oil pump VFD, Alarm horn, 
   Power station interlock, Turbine brake)
 - A hourmeter to keep track of power supplied to energy grid when system enters generation mode.

## Program code
They are listed in a seperate folder called 'PLC Programs'. Code in a different language (Functional Block, GRAPH or Ladder Logic) can be found in the pdf file called 'Print - PLC (2)'.

## HMI details
Can be found in a seperate folder called 'HMI'. For more information, look into the pdf file called 'Print - HMI'.
