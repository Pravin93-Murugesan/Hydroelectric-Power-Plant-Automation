# Hydroelectric-Power-Plant-Automation
A simulation project carried out in Siemens Step 7 and WinCC. 

## Poject Description:
The objective here is to program a control system for a hypothetical hydroelectric power plant. A base program has been provided to simulate a changing environment and it gives analog and digital input signals accordingly. My task was to write a program that incorporates these signals and control various analog and digital devices in order to run the system in a safe and stable manner. Additionally, I created an HMI that will allow a control operator to easily and effectively interact with the control system.

## Theory of Operation
![alt text](https://github.com/Pravin93-Murugesan/Hydroelectric-Power-Plant-Automation/blob/master/1.png)
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


