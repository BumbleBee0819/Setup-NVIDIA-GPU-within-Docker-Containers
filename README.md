[![GitHub issues](https://img.shields.io/github/issues/Naereen/StrapDown.js.svg)](https://github.com/BumbleBee0819/PsychophysicsExperiment_PairedComparison/issues/)
[![License](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Total visitor](https://visitor-count-badge.herokuapp.com/total.svg?repo_id=docker_gpu)
![Visitors in today](https://visitor-count-badge.herokuapp.com/today.svg?repo_id=docker_gpu)
> Author: Wenyan Bi

> since 2019-11-04


# Setup NVIDIA GPU within Docker Containers for Deep Learning
<div>
    <p align="center"> Docker architecture </strong></p>
    <p align="center"><img src="https://lh6.googleusercontent.com/OLNkuRtYmA-8DwJ1-gSM9HL4Uxu56ae3yX5deu9997DXNtNEFbaAnuwSTlKFbAlmwH8GqJohKNow8gpDbUj_LPqW1sfXBu7CLDFB2cL5jqCuuLiOc89AKdH2yiYkq-37EdnePetq"  display= block width=50%></p>
</div>


## 1. Install docker ##
   - 1). For different operating systems
    : [Mac](https://docs.docker.com/docker-for-mac/install/)
    | [Windows](https://docs.docker.com/docker-for-windows/install/)
    | [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    | [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
    | [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   - 2). Check whether the docker has been successfully installed
        ```bash
        $ nvidia-docker version
    
        ```
## 2. Get the docker image ##
   - 1). To pull the bethgelab deep learning docker image from github
        ```bash
        $ nvidia-docker pull bethgelab/deeplearning:cuda9.0-cudnn7
    
        ```
   - 2). [Optional] To list all existing docker images
        ```bash
        $ nvidia-docker images
    
        ``` 
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/docker.png"  display= block width=50%></p>
        </div>
        
   - 3). [Optional] To remove an existing docker image
        ```bash
        $ nvidia-docker rmi <Image ID>
    
        ```  
## 3. Run the downloaded image as a container ##       
   - 1). To run the downloaded image as a container (a container is the instance of a docker image)
        ```bash
        $ nvidia-docker run  -it bethgelab/deeplearning:cuda9.0-cudnn7  bash
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/run%20container.png"  display= block width=50%></p>
        </div>   
        
   - 2). Exit the current container
        ```bash
        $ exit
    
        ```    
   - 3). List all the docker containers and find your container ID (must exit the container first)
        ```bash
        $ nvidia-docker ps -a
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/list%20container.png"  display= block width=70%></p>
        </div>  
        
   - 4). Save the container's file changes/settings into a new docker image. Next time you can open the image with the [new image name].  
        ```bash
        $ nvidia-docker commit <Container ID> <new image name>:<new image tag>
    
        ``` 
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/save%20image.png"  display= block width=70%></p>
        </div> 


## 4. Create the container and make changes inside it ## 
   - 1). Run the container in the interactive mode
        ```bash
        $ nvidia-docker run -it -v <local_dir>:<container_dir> <image repository>:<image tag> bash
    
        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/interactive.png"  display= block width=70%></p>
        </div>  
        
   - 2). [Optional] If the default python is python2, change it to python3. 
        -  Check the directory of python3
        ```bash
        $ which python3
        /usr/bin/python3
        ```  
        -  Change the default python version
        1) open the .bashrc file
        ```bash
        $ vim ~/.bashrc
        ```   
        2) append the following commands to the end of the .bashrc file; save and exit
        ```bash
        $ alias python='/usr/bin/python3'
        ``` 
        3) reload the bash_profile
        ```bash
        $ source ~/.bashrc
        ``` 
        4) type "python -V" in the terminal, it should now display python3
        
   - 3). [Optional] Install the opencv and keras
        ```bash
        $ pip3 install opencv-python
        $ pip3 install keras==2.2.0
        ```   
   - 4). Exit the current container
        ```bash
        $ exit
    
        ```         
   - 5). Commit the changes made in the container
        ```bash
        $ nvidia-docker commit <container-id> <image repository>:<image tag>
    
        ```  
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/commit.png"  display= block width=70%></p>
        </div>    
   
## 5. Reopen the existing container ##  
   - 1). To run the existing container in the interactive mode
        ```bash
        $ nvidia-docker exec -ti <container-ID> bash
        ```    
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/reopen%20container.png"  display= block width=70%></p>
        </div> 
   - 2). If the above step arises error that the container has stopped, you have to restart the container first, then try the above step again.
        ```bash
        $ nvidia-docker container restart <container-ID>
        ```    
## 6. Run the container in the detachable mode and submit jobs to it## 
### If you don't have a running container ### 
   - 1). To run the container in the detached mode
        ```bash
        $ nvidia-docker run -dit -v <local_dir>:<container_dir> <image repository>:<image tag> bash

        ```   
        <div>
            <p align="left"><img src="https://github.com/BumbleBee0819/Setup-NVIDIA-GPU-within-Docker-Containers/blob/master/img/detachable%20container.png"  display= block width=70%></p>
        </div> 
   - 2). To exit the container, press "Ctrl+p+q" (exit the container without terminating it)
   - 3). To reopen the existing container
        ```bash
        $ nvidia-docker attach <container-ID>

        ```  
 ### If you already have a running container ### 
   - 1). Enter the container
        ```bash
        $ nvidia-docker attach <container-ID>

        ```   
   - 2). Run the python script backend        
        ```bash
        $ python test.py &

        ```   
   - 3). Exit the container        
         Ctrl+p+q
   - 4). Check the GPU usage in the base root      
        ```bash
        $ nvidia-smi

        ```
        
## 7. Common errors ##  
   - 1). (Graphviz error) FileNotFoundError: [Errno 2] "dot" not found in path.
        ```bash
        $ sudo add-apt-repository universe
        $ sudo apt update
        $ sudo apt install graphviz

        ```  
   - 2). If the GPU can't be recognized, double check that you run the docker with "nvidia-docker run" rather than "docker run".
   - 3). Setup File Zilla for file transfer:
         Site Manager -> 
         Click New site and set the following: In protocol, select "SFTP"; 
                                               HOST: [172.25.250.112]; 
                                               Port: [60222]; 
                                               User: [wbi]
   
## Contact
If you have any questions, please contact "wb1918a@american.edu".
   
   

 
