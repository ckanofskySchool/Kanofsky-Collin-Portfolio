title: Daily Journal

## 9/16/2025
Today, we learned about Git, Github, Github desktop, and the browser github as well. Specifically, we focused on how changes are stored in Git and the ability to create branches of the repo for development without affecting the original branch.

## 9/17/2025
Today, we practiced with Git and created shared Repo's with each other to practice with collaborator settings on github.

## 9/24/2025
Today, I decided to order the essential electronics for my project, which included the motor controllers, the batteries, and the safety mechanisms.

## 9/25/2025
Today, we did a soldering activity where we practiced surface mount and through hole soldering using a Halloween owl kit which lights up when you touch it. The surface mount soldering, internal components, and the finished product are shown in pictures below.

## 9/26/2025
Outside of class today, I used the AI Claude with the Opus4.1 model to generate some starting code for my project. The programs I had made were a RP2040 Seeed program which will control the motors, and a RaspberryPi + AI Camera program which will hand the tracking aspects and math of the camera. I am using the AI formulated code as a launchpad in order to be more efficient and spend more time on customization and troubleshooting, than have to spend that time on writing the base code myself. However, to ensure I understood the code and would be able to edit and modify it, I made sure to go through each line and ensure that I understood why and what the line did, and how modifying that line of code would impact the overall performance of the program. The initial prompts I inputed are shown below.

### Prompt for RP2040 Seeed Code

```write me an arduino code for a RP2040 Seeed which will take input from the usb serial coming off a raspberry pi and move 2 drive motors on my robot using pwm(like how servos are controlled) according to the directions. For input directions, there should be a heading which if is outside the middle range set by me in a variable, then the program should turn until the heading is once again within acceptable values. Another input will be the distance from the target which also should be kept within acceptable range set by me in a variable. Lastly, have a serial monitor where I can input values for left motor and right motors to test if I want. One last thing is whenever motor powers are set, send back what has been set across the usb serial for the Pi to recieve.```


### Prompt for Raspberry Pi Code

```can you now write me a raspberry pi program in Python prob. that will provide these inputs needed based off a raspberry pi 5 and a raspberry pi AI camera attachment. Also have the raspberry pi host a webserver that allows the user to see the motor power assignments and camera feed. There should be a simple but neat UI for that web page pls.```

## 10/6/2025

I have done some thinking and realized that I was going too big on the first code attempt, so I backtracked a bit back to the Raspberry Pi AI Camera Documentation, and completed the instructions as well as ran the example program:
``` rpicam-hello -t 0s --post-process-file /usr/share/rpi-camera-assets/imx500_mobilenet_ssd.json --viewfinder-width 1920 --viewfinder-height 1080 --framerate 30 ```

This program worked amazing and highlighted me with a bounding box as well as providing a percentage of certainty which seemed to stay above 50% consistently.

## 10/7/2025

### Layouts
Today, I worked on the electrical for the robot, mainly trying to get power and control to 1 motor for testing. The layout of main power in my electrical testing setup went as such: 
Battery(12v 15000AmH) --> Breaker(30A) --> MotorController(Koors40 Brushed DC Motor Controller) 
--> Motor(CIM Motor) 

Then, I had to have a separate control setup that would tell the motor controller how to move the motor. I also had to wire up a 5V power source into the receiver because the PWM output from the motor controller didn't provide a 5V port, just signal and ground wires. The layout of the control setup went as such:
Controller(Wireless RC Plane Controller) --> Reciever(RC Plane Reciever) --> MotorControllerPWM(Koors40 Brushed DC Motor Controller)

I haven't built this part yet because I chose to focus on the main power layout.

### Making Connections

The main focus I had when setting up the hardware was modularity. I want to be able to replace components if I need to, or swap them out without having to unsolder or cut wires, so I decided to use Wago connectors, which take to unsoldered raw wire ends, and clamp down a metal plate on the wires forming a connection between the wires on both sides. These connectors worked great, but I sadly only snagged 2 from my robotics team, and I inevitably ended up needing 4, so I put the final wiring on hold until I could get some more Wago connectors.

I also had to do some soldering to make the connection between my battery and the rest of the power system. I soldered on ___ connectors which connected to the battery.

When it came to connecting the wires to the 30Amp breaker, I chose not to crimp or solder the wires into the copper connector that the breaker came with because I was pretty sure that those wires would not be the correct length for the final wires in the finished robot. Instead, I chose to strip a lot of the wire and do a full loop around the head of the bolt, which is where the wire connects, and then clamped it down with the nut, which provided a secure connection when tightened, but long-term holds the risk of wires spraying off and overall potential safety concerns if not treated carefully. However, it will work great and be safe enough for testing since it is only a short-term application.

### Photo Of Full Setup

![]()

## 10/8/2025

Today, I found the GitHub repo for the rpicam-hello program and ran it as a Python file, which allowed me to make edits to the code itself. I then used the AI ChatGPT from OpenAI to add code for outputting where the human is in the serial terminal. I chose to use ChatGPT because Claude didn't seem great at modifying the code without rewriting everything, and that would always end up causing errors. ChatGPT had me edit one of the functions, and everything else stayed the same, so when I tested the new code, it worked great, and I was able to route the output to my computer terminal temporarily, so I could see the output without another device on the other side of the serial connection.

Here is the original code: [rpicam-hello](https://github.com/raspberrypi/picamera2/blob/main/examples/imx500/imx500_object_detection_demo_mp.py)

Here is the updated code, which I developed with AI assistance: [modified rpicam-hello]()

This code worked amazingly and had very similar functions to the example, but a few key modifications to make it more effective and accurate for my use:
- Added a stabilizing function
    - The data would update every frame and the bounding box would move after every update, still correct, but I don't need that much precision of 5 pixel shift to the left or whatever, so I insterted a snipet of code which only changes the detection bounding box if the center point has moved by >25 pixels, or the size has changed by 20%. This helped smooth the detection and give a more stable instruction, which will be easier for the robot to follow.
    
- Added output to Serial for the Seeed board to receive instructions
    - In order to tell the Seeed board where the person is, I outputed a formatted set of data which gives the centerpoint x and y position, as well as the width and height of the bounding box. The format goes like such: x,y,w,l
    - By changing the serial port from 3 to 1, which is the computer's port, I was able to visualize the output on the terminal and confirm that the code was working correctly.

### Video of the Code Functioning



## 10/9/2025

Today, I continued working on the electrical testing setup I started on 10/7/2025. I acquired 4 more Wago connectors from my robotics team and finished up the connections between the motor and the motor controller using them. After finishing the main power setup, I started building the control wiring setup 







