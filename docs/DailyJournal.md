title: Daily Journal

## 9/16/2025
Today, we learned about Git, Github, Github desktop, and the browser github as well. Specifically, we focused on how changes are stored in Git and the ability to create branches of the repo for development without affecting the original branch.

## 9/17/2025
Today, we practiced with Git and created shared Repo's with eachother to practice with collaborator settings on github.

## 9/24/2025
Today, I decided to order the essential electronics for my project, this included the motor controllers, the batteries, and the safety mechanisms.

## 9/25/2025
Today, we did a soldering activity where we practiced surface mount and through hole soldering using a halloween owl kit which lights up when you touch it. The surface mount soldering, internal components, and the finished product are shown in pictures below.

## 9/26/2025
Outside of class today, I used the AI Claude with the Opus4.1 model to generate some starting code for my project. The programs I had made were a RP2040 Seeed program which will control the motors, and a RaspberryPi + AI Camera program which will hand the tracking aspects and math of the camera. I am using the AI formulated code as a launchpad in order to be more efficient and spend more time on customization and troubleshooting, than have to spend that time on writing the base code myself. However, to ensure I understood the code and would be able to edit and modify it, I made sure to go through each line and ensure that I understood why and what the line did, and how modifing that line of code would impact the overall preformance of the program. The initial prompts I inputed are shown below.

### Prompt for RP2040 Seeed Code
~~~
write me an arduino code for a RP2040 Seeed which will take input from the usb serial coming off a raspberry pi and move 2 drive motors on my robot using pwm(like how servos are controlled) according to the directions. For input directions, there should be a heading which if is outside the middle range set by me in a variable, then the program should turn until the the heading is once again within acceptable values. Another input will be the distance from the target which also should be kept within acceptable range set by me in a variable. Lastly, have a serial monitor where I can input values for left motor and right motors to test if I want. One last thing is whenever motor powers are set, send back what has been set across the usb serial for the Pi to recieve.
~~~

### Prompt for Raspberry Pi Code
~~~
can you now right me a raspberry pi program in pythong prob. that will provide these inputs needed based off a raspberry pi 5 and a raspberry pi AI camera attachment. Also have the raspberry pi host a webserver that allows the user to see the motor power assignements and camera feed. there should be a simple but neat UI for that web page pls
~~~