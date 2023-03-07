# CNC_milling_tool_project

Problem Statement
A series of machining experiments were run on 2" x 2" x 1.5" wax blocks in a CNC milling machine in the System-level Manufacturing and Automation Research Testbed (SMART) at the University of Michigan. Machining data was collected from a CNC machine for variations of tool condition, feed rate, and clamping pressure. Each experiment produced a finished wax part with an "S" shape - S for smart manufacturing - carved into the top face, as shown in test_artifact.jpg

Application
The dataset can be used in classification studies such as:
(1) Tool wear detection --- Supervised binary classification could be performed for identification of worn and unworn cutting tools. Eight experiments were run with an unworn tool while ten were run with a worn tool (see tool_condition column for indication).
(2) Detection of inadequate clamping --- The data could be used to detect when a workpiece is not being held in the vise with sufficient pressure to pass visual inspection (see passed_visual_inspection column for indication of visual flaws). Experiments were run with pressures of 2.5, 3.0, and 4.0 bar. The data could also be used for detecting when conditions are critical enough to prevent the machining operation from completing (see machining_completed column for indication of when machining was preemptively stopped due to safety concerns).

Features
The features available in the machining datasets are:
* X1_ActualPosition: actual x position of part (mm)
  X1_ActualVelocity: actual x velocity of part (mm/s)
  X1_ActualAcceleration: actual x acceleration of part (mm/s/s)
  X1_CommandPosition: reference x position of part (mm)
  X1_CommandVelocity: reference x velocity of part (mm/s)
  X1_CommandAcceleration: reference x acceleration of part (mm/s/s)
  X1_CurrentFeedback: current (A)
  X1_DCBusVoltage: voltage (V)
  X1_OutputCurrent: current (A)
  X1_OutputVoltage: voltage (V)
  X1_OutputPower: power (kW)
  
* Y1_ActualPosition: actual y position of part (mm)
  Y1_ActualVelocity: actual y velocity of part (mm/s)
  Y1_ActualAcceleration: actual y acceleration of part (mm/s/s)
  Y1_CommandPosition: reference y position of part (mm)
  Y1_CommandVelocity: reference y velocity of part (mm/s)
  Y1_CommandAcceleration: reference y acceleration of part (mm/s/s)
  Y1_CurrentFeedback: current (A)
  Y1_DCBusVoltage: voltage (V)
  Y1_OutputCurrent: current (A)
  Y1_OutputVoltage: voltage (V)
  Y1_OutputPower: power (kW)

* Z1_ActualPosition: actual z position of part (mm)
  Z1_ActualVelocity: actual z velocity of part (mm/s)
  Z1_ActualAcceleration: actual z acceleration of part (mm/s/s)
  Z1_CommandPosition: reference z position of part (mm)
  Z1_CommandVelocity: reference z velocity of part (mm/s)
  Z1_CommandAcceleration: reference z acceleration of part (mm/s/s)
  Z1_CurrentFeedback: current (A)
  Z1_DCBusVoltage: voltage (V)
  Z1_OutputCurrent: current (A)
  Z1_OutputVoltage: voltage (V)
  
* S1_ActualPosition: actual position of spindle (mm)
  S1_ActualVelocity: actual velocity of spindle (mm/s)
  S1_ActualAcceleration: actual acceleration of spindle (mm/s/s)
  S1_CommandPosition: reference position of spindle (mm)
  S1_CommandVelocity: reference velocity of spindle (mm/s)
  S1_CommandAcceleration: reference acceleration of spindle (mm/s/s)
  S1_CurrentFeedback: current (A)
  S1_DCBusVoltage: voltage (V)
  S1_OutputCurrent: current (A)
  S1_OutputVoltage: voltage (V)
  S1_OutputPower: current (A)
  S1_SystemInertia: torque inertia (kg*m^2)

* M1_CURRENT_PROGRAM_NUMBER: number the program is listed under on the CNC
  M1_sequence_number: line of G-code being executed
  M1_CURRENT_FEEDRATE: instantaneous feed rate of spindle
  
 We tried to build a model to predict of tool wear detection.

* After analyzing the dataset, we saw that the distribution of variables is skewed, that there are outliers, and that there is no linearity. We analyzed the variables for missing data, and because the variables there are missing less than 0.2% data, each imputer worked well. We also analyzed discretization variables and performed a scaling analysis.
* We removed empty variables and variables that correlate well with feature selection.
* Trained the model with various hyperparameters, metrics and found that the best model is VotingClassifier.
* The worst model is GaussianNB with an accuracy of 58%
