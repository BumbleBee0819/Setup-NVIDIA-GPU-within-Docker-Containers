[![GitHub issues](https://img.shields.io/github/issues/Naereen/StrapDown.js.svg)](https://github.com/BumbleBee0819/PsychophysicsExperiment_PairedComparison/issues/)
[![License](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Total visitor](https://visitor-count-badge.herokuapp.com/total.svg?repo_id=docker_gpu)
![Visitors in today](https://visitor-count-badge.herokuapp.com/today.svg?repo_id=docker_gpu)
> since 2019-11-04


# Setup NVIDA GPU within Docker Containers for Deep Learning
<div>
    <p align="center"> Docker architecture </strong></p>
    <p align="center"><img src="https://lh6.googleusercontent.com/OLNkuRtYmA-8DwJ1-gSM9HL4Uxu56ae3yX5deu9997DXNtNEFbaAnuwSTlKFbAlmwH8GqJohKNow8gpDbUj_LPqW1sfXBu7CLDFB2cL5jqCuuLiOc89AKdH2yiYkq-37EdnePetq"  display= block width=50%></p>
</div>


## 1. Install docker ##
   - For different operating system
    : [Mac](https://docs.docker.com/docker-for-mac/install/)
    | [Windows](https://docs.docker.com/docker-for-windows/install/)
    | [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    | [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    | [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   - Check whether the docker has been successfully installed
        ```bash
        $ docker version
    
        ```
**2. Get the docker image**
   - To pull the bethgelab deep learning docker image from github
        ```bash
        $ docker pull bethgelab/deeplearning:cuda9.0-cudnn7
    
        ```
   - [Optional]To list all existing docker images
        ```bash
        $ docker images
    
        ``` 
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/docker.png"  display= block width=50%></p>
        </div>
        
   - [Optional]To remove an existing docker image
        ```bash
        $ docker rmi <Image ID>
    
        ```  
**3. Run the downloaded image as a container**        
   - To run the downloaded image as a container (a container is the instance of a docker image)
        ```bash
        $ docker run  -it bethgelab/deeplearning:cuda9.0-cudnn7  bash
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/run%20container.png"  display= block width=50%></p>
        </div>   
        
   - Exit the current container
        ```bash
        $ exit
    
        ```    
   - List all the docker containers and find your container ID (must exit the container first)
        ```bash
        $ docker ps -a
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/list%20container.png"  display= block width=70%></p>
        </div>  
        
   - Save the container's file changes/settings into a new docker image. Next time you can open the image with the [new image name].  
        ```bash
        $ docker commit <Container ID> <new image name>:<new image tag>
    
        ``` 
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/save%20image.png"  display= block width=70%></p>
        </div> 


**4. Use the container** 
   - To run the container in the interactive mode
        ```bash
        $ docker run -it -v <local_dir>:<container_dir> <image repository>:<image tag>
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/interactive.png"  display= block width=70%></p>
        </div>  
        
   - If the default python is python2, change it to python3. 
        -  Check the directory of python3
        ```bash
        $ which python3
        /usr/bin/python3
        ```  
   - Change the default python version
        ```bash
        $ vim ~/.bashrc
        ```   
        append the following commands to the end of the .bashrc file; save and exit
        ```bash
        $ alias python='/usr/bin/python3'
        ``` 
        reload the bash_profile
        ```bash
        $ source ~/.bashrc
        ``` 
        type "python -V" in the terminal, it should now display python3
        
   - Install the opencv and keras
        ```bash
        $ pip3 install opencv-python
        $ pip3 install keras==2.2.0
        ```   
 
## Contact
If you have any questions, please contact "wb1918a@american.edu".
   
   

 
