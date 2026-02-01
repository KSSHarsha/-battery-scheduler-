# -battery-scheduler-
Battery scheduling algorithm for wearable devices 
Wearable Device Battery Scheduling

Problem Statement
A wearable device with limited battery capacity must execute a sequence of tasks in the given order. Each task consumes battery at a constant rate. Between tasks, the device may enter an idle state, during which the battery recharges at a constant rate. The objective is to determine the minimum total runtime (sum of task durations and idle durations) required to execute all tasks without violating battery constraints. If execution is impossible, the algorithm must return `-1`.

Inputs
- `batteryCapacity`: Maximum battery capacity in mAh  
- `initialBattery`: Initial battery level in mAh  
- `tasks`: List of tasks, where each task is `[duration, drainRate]`  
- `chargeRate`: Recharge rate during idle in mAh per second  

Constraints
- Tasks must be executed in the given order  
- Idle periods may be inserted between tasks  
- Battery level must never go below 0  
- Battery level must never exceed `batteryCapacity`  
- Battery changes continuously over time  

Algorithm
1. Initialize battery level with `initialBattery`.  
2. For each task in order:  
   - Calculate required energy.  
   - If battery is insufficient, insert idle time to recharge until the task can run.  
   - Ensure battery does not exceed `batteryCapacity`.  
   - Execute the task, reducing battery accordingly.  
   - If battery goes below 0, return `-1`.  
3. Accumulate total runtime (task durations + idle durations).  
4. Return the minimum total runtime rounded to one decimal place.  

 Assumptions
- Drain and recharge rates are constant  
- Battery changes linearly with time  
- No energy loss due to inefficiency  

Example
int batteryCapacity = 100;
int initialBattery = 50;
int tasks[2][2] = {{10, 5}, {20, 3}};
int chargeRate = 2;

   Expected Output:
   Minimum Runtime: 35.0
