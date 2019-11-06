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


**1. Install docker**
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
   
   
   
## Contact
If you have any questions, please contact "wb1918a@american.edu".
   
   

 
