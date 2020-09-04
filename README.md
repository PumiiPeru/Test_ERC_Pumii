# ERC PUMII Docker Image

This repository contains an example Dockerfile that can be used to build a docker image that will be run on Leo Rover. The ERC repo: https://github.com/fictionlab/erc_docker_img was taken as a template.
It can be used by the teams as a template for developing their custom software for the ERC competitions.

This example image starts the Freedom agent which connects to your account at [Freedom Robotics App](https://app.freedomrobotics.ai/), as well as a launch file from an example package which start a ROS node that let's you save images from topics to PNG files.

## Building

Login to the [Freedom Robotics App](https://app.freedomrobotics.ai/), click on **Add Device** -> **Quick Create** and copy the URL address from the command (not the whole command).

Now execute the following command as the `root` user (replace `<YOUR_URL>` with the address you copied):
```
docker build -t erc_img --build-arg FREEDOM_URL="<YOUR_URL>" .
```
## Lanching

To run the image, simply type:
```
docker run -it --net=host --name erc_img erc_img
```
If you want to use it with ROS running on another machine, pass the `ROS_IP` and `ROS_MASTER_URI` variables:
```
docker run -it --net=host -e ROS_IP=<YOUR_IP> -e ROS_MASTER_URI=<MASTER_URI> --name erc_img erc_img
```
