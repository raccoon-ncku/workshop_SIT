# Workshop SIT 2023
## Robotic application hands-on session- SIE 3015 Automation and control in building
The session will introduce the workflow of simulating industrial robots in CAD(Rhino) with ROS (Robot Operating System) as the backend. 

## Session rundown
* (10 min) A brief introduction to ROS: a platform for robot projects.
* (20 min) A brief introduction to Docker: a light-weight virtualization technique to deploy app/services + examples
* (15 min) Robotic fundamentals
* (20 min) Hands-on: Robot simulation in Rhino with ROS
* (20 min) Hands-on: Robotic fabrication and simulation in Rhino with ROS

## Computer Setup
### Program List
* Windows 10 Pro or above / Mac OS Sierra 10.12 or above
* [miniconda 3](https://docs.conda.io/en/latest/miniconda.html)
* [Docker Desktop](https://www.docker.com/products/docker-desktop) 
* [Rhino 6 or 7](https://www.rhino3d.com/download)
* [Visual Studio Code](https://code.visualstudio.com/)

### Initialize Developing Environment in Rhino
The developing environment in Rhino need to be initialized before installing Python modules. This only needs to be done once on every computer. To do that, open Rhino and navigate to `Tools > PythonScript > Edit...`. Once the script editor shows up, the environment is successfully initialized, and Rhino could be closed.

### Python and Installation

We use `conda` to make sure we have clean, isolated environment for Python and dependencies.

First, open `Anaconda Powershell Prompt (miniconda3)` (Windows) or `Terminal` (macOS).

Then, execute the following commands:
```sh
conda config --add channels conda-forge
conda create -n SIE3015 compas compas_fab compas_view2 -y
conda activate SIE3015
```

> [!IMPORTANT]  
> The commands above might take up to 20-30 minutes to finish.

Finally, depending on your installed Rhino version, execute one of the flollowing:

#### Rhino 6
```sh
python -m compas_rhino.install -v 6.0 -c
```

#### Rhino 7
```sh
python -m compas_rhino.install -v 7.0 -c
```
### Visual Studio Setup

Open Visual Studio Code and install the following extensions:
* ms-python.python
* ms-azuretools.vscode-docker


## Verify Installation
### Docker
Please open `Docker Desktop`, then open `PowerShell`(Windows) or `Terminal`(macOS) and execute the command:

```sh
docker run hello-world
```

and it should return

```text
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete
Digest: sha256:88ec0acaa3ec199d3b7eaf73588f4518c25f9d34f58ce9a0df68429c5af48e8d
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

### Python and Rhino
Check if the tab COMPAS exists in Grasshopper. Place the `info` component on the canvas to get more information.
![compas_installed_in_rhino](assets/img/compas_installed_in_rhino.png)

## Docker Image
A docker image file around 3GB needs to be deployed to the computer before the session. Please download the docker image (open source) via the google drive link below in every PC in SR-3D and 3E.
[Google Drive Link](https://drive.google.com/drive/folders/1159IfPik13sScniSJwjBX9LQlO-e-gGp?usp=sharing)

Once downloaded, please follow the steps below to load the image into Docker:

- If Google Drive compress the file into a `.zip` file, please unzip it first. The file should be named `rccn-ros-x64.tar`, and don't unzip the `.tar` file.
- open Docker Desktop, make sure the docker engine is running.
- open PowerShell, and navigate to the folder where `rccn-ros-x64.tar` is located
- type in `docker load -i .\rccn-ros-x64.tar` then press enter, wait for the command to finish.

After the command above is finished, open docker desktop and navigate to the image tab, check if there is a image named "rccn-ros". If thas is the case, its okay to delete the `.tar` file.

## Final verification
Open this repository in Visual Studio Code, find the file `docker-compose
.yml` in the `docker_compose
/ros-rccn/` folder in vscode, right click on the file and select `Compose Up`. Then, open the example file `216_forward_kinematics_ros.ghx` in `/examples/robot_simulation/` in Grasshopper, and double click the `connect` toggle then click the `load` button on the top left corner of the Grasshopper window. If a robot appears in the Rhino window, the installation is successful.

## Note
The computer should have access to the internet(at least github.com) during the session.