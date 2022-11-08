# Workshop SIT 2022
## Robotic application hands-on session- SIE 3015 Automation and control in building
The session will introduce the workflow of simulating industrial robots in CAD(Rhino) with ROS (Robot Operating System) as the backend. 

## Session rundown
* (10 min) A brief introduction to ROS: a platform for robot projects.
* (20 min) A brief introduction to Docker: a light-weight virtualization technique to deploy app/services + examples
* (15 min) Robotic fundamentals
* (20 min) Hands-on: Robot simulation in Rhino with ROS
* (20 min) Hands-on: Robotic fabrication and simulation in Rhino with ROS
* (20 min) Hands-on: (WIP) AGV+industrial robot simulation in Rhino with ROS

## Computer Setup
### Program List
* Windows 10 Pro or Mac OS Sierra 10.12
* [miniconda 3](https://docs.conda.io/en/latest/miniconda.html)
* [Docker Desktop](https://www.docker.com/products/docker-desktop) 
* [Rhino 6 or 7](https://www.rhino3d.com/download)
* [Visual Studio Code](https://code.visualstudio.com/)


### Python and Installation

We use `conda` to make sure we have clean, isolated environment for Python and dependencies.

First, open `Anaconda Powershell Prompt (miniconda3)` (Windows) or `Terminal` (macOS).

Then, execute the following commands:
```
conda config --add channels conda-forge
conda create -n SIE3015 compas compas_fab compas_view2
conda activate SIE3015
```
Before the last step, make sure the scripting interface of Rhino has been initialized at least once. This only needs to be done once on every computer. To do that, open Rhino and navigate to `Tools > PythonScript > Edit...`. Once the script editor shows up, the interface is successfully initialized, and Rhino could be closed.

Finally, depending on your installed Rhino version, execute one of the flollowing:

#### Rhino 6
```
python -m compas_rhino.install -v 6.0
```

#### Rhino 7
```
python -m compas_rhino.install -v 7.0
```
### Visual Studio Setup

Open Visual Studio Code and install the following extensions:
* ms-python.python
* ms-azuretools.vscode-docker

## Verify Installation
### Docker
Please open `Docker Desktop`, then open `PowerShell`(Windows) or `Terminal`(macOS) and execute the command:

```
docker run hello-world
```

### Python and Rhino
Check if the tab COMPAS exists in Grasshopper. Place the `info` component on the canvas to get more information.
![compas_installed_in_rhino](assets/img/compas_installed_in_rhino.png)

## note
A docker image file around 4GB needs to be deployed to the computer before the session.

The computer should have access to the internet(at least github.com) during the session.

## Slides
[slides](https://docs.google.com/presentation/d/12ieSXxlZcldEHS5Oq1aI8YYjDYtOCbjdaSPXm2D_5kw/edit?usp=sharing)