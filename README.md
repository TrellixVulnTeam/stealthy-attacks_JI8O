# Stealthy Attacks Against Robotic Autonomous Vehicles
This project contains simulations for triggering stealthy attacks against robotic vehicles. We use ArduPilot SITL to demonstrate three types of stealthy attacks namely: i) False Data Injection, ii) Artificial Delay, iii) Switch Mode attacks, on copter and rover.

# Building the docker image
Clone the project
```bash
git clone https://github.com/DependableSystemsLab/stealthy-attacks.git
cd stealthy-attacks
```
Build docker image
```bash
docker build -t stealthy-attacks DockerFile/.
```
Run docker Simulator
The simulator can be executed by running the docker image and then following the steps given here http://ardupilot.org/dev/docs/setting-up-sitl-on-linux.html 
For easy execution we have provided a script that will start the simultor. 
```bash
./startSimulatorWithAttack.sh copter --console --map
```
To run a mission, use this command:
```bash
wp load ../Tools/autotest/mission-1.txt
mode guided
arm throttle
takeoff 100
wp set 2
mode auto
```
When the RV reaches its destination, execute the command
```bash
mode land
```

# Running ArduPilot locally
To use a local copy of ArduPilot and trigger the attacks in the simulator use the following steps:
* Clone the Project
* Run ardupilot locally
```bash
cd stealthy-attacks/Simulator/ardupilot-attack-version/ArduCopter
../Tools/autotest/sim_vehicle.py --console --map
```
Follow the steps given here http://ardupilot.org/dev/docs/copter-sitl-mavproxy-tutorial.html for further details. 

# Deploying Firmware in Vehicles
The deployable firmware for Pixhawk2 vehicles are provided. For more information on deploying custom firmware,please follow the instructions given here http://firmware.ardupilot.org/. As firmwares can only be deployed in RVs builton Pixhawk platform, we provide videos showing the effects of the attacks. The demo videos are available here https://bit.ly/2HG9Qnw



