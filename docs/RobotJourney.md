## Mechanical Systems

I started my CAD journey a while back in sophmore year as I was super exited for this project, but I will do my best to re-track my steps to show how the CAD came to be.

I started off my design by drawing out what I wanted the robot to look like, what parts I could use, etc. At the start, I was thinking about using 2x4 wooden board due to them being cheep, accesible, and sturdy. However, I decided to use 80/20 due to it's modularity and robustness



### Programming Systems

I started off the coding of the Raspberry Pi Brain by installing the Raspberry Pi AI Camera and followed the instructions from the [Raspberry Pi AI Camera Documentation](https://www.raspberrypi.com/documentation/accessories/ai-camera.html). After setting up the IMX 500 Library, I ran the example object dection code with the following terminal command:
``` rpicam-hello -t 0s --post-process-file /usr/share/rpi-camera-assets/imx500_mobilenet_ssd.json --viewfinder-width 1920 --viewfinder-height 1080 --framerate 30 ```

This program outputed the live camera feed and projected a bounding box over any detected objects with the object type and certanty. From my testing, I determined that this model would work best for my project because unlike some other models I tested like YOLTOV, which would sometimes not identify humans if they were too close or did sudden movements, this test program almost always had a >50%  certanty in identifying me as a person when I was within 5 feet of the camera lense even if I jumped or moved rapidly.

My next step in developing my control program for the RoboPack was to combine the knowledge of AI, with the example object detection code, to get a simple program that's goal is to use the example code and add in the logic to give motor control instructions to a seperate board.


### Hardware Systems

In order to ensure that my project was feasable and that I would be able to control the level of motors which I desired, I started off by creating a large Bill Of Materials with everything I would need