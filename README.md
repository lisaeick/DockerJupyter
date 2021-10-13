# DockerJupyter
Docker container for running Jupyter
These Dockerfiles are intended to create a tensorflow integrated Jupyter environment on which older packages like XG-boosted tree can run. For this purpose, several Dockerfiles developed by the Jupyter Development Team (https://github.com/jupyter/docker-stacks) were adapted and rewritten to fit the requirements.

# Important data of the environment:
-**Use of conda** (Makes the image big but the dependencies simple)
-**Python: 3.6** (can be changed in the base image)
-**scikit-learn**= Version: 0.23 (necessary for certain packages)

## base-image
The basic environment of the machine is implemented in the base image. In addition, executable programs that are needed to start Jupyter are loaded into Docker:
### Base environmant: 
**Ubuntu 18.04**
**Conda 4.10.3**
**Python 3.6**

## middle-image
Here the necessary packages and dependencies are installed that are needed for Data Science. 

## final-image
The final image is intended for your own changes and specifications.
If you want to create your own environment, I suggest writing your own final image which builds on the middle image. 
In this image, specific adjustments are made. The scikit-learn version is set to 0.23 and eli5 us shap is installed. 

## Application

**1. To use this env you have to install docker:**

- Install docker (https://docs.docker.com/engine/install/ubuntu/)

**2. This will create an image on you computer based on the "final-image" dockerfile:**
```
- sudo docker pull lisaeick/dockerjupyter-final
```
**2,5. This will rename the tag, so that the tag becomes more handy (no necessary step):**
```
- sudo docker tag lisaeick/dockerjupyter-final final-jupyter
```
**3. If you want the Environment beeing able to have access to your data and code you have to create a directory:**

- /path/to/my/Code

**4. You have to change the rights of that folder and all subfolder, so that it is changeable for everyone:**
```
- chmod -R 777 path/to/my/Code
```
**5. This will start the container:**
```
- sudo docker run --user root -v /path/to/my/Code:/home/jovyan -e GRANT_SUDO=yes -it --rm -p 8888:8888 final-jupyter
```
**6. Now go to your browser and type in:**

- http://localhost:8888/

Have fun coding!
