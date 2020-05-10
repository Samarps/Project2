# Project2

I am currently pursuing DevOps assembly lines internship training under the world record holder sir Vimal Daga. Vimal Daga sir provided us with this great project, it shows end-to-end automation just by using some tools and technologies like Git, Github, Jenkins.


◉ Project: It contains four jobs linked to each other through chaining. What each job does, find out here:

Job1: I named this job "Github". Once the developer commits the new code through "dev1" branch, it automatically gets pushed to Github (using hooks) & then it triggers this job. Once this job is triggered, Jenkins goes to the remote location i.e., Github & downloads the code in its workspace & then copy the same code into a rhel8 system at location /root/website/dev1/. Then it installs a new OS system using docker which has already configured webserver. This OS is the testing system. During the installation of this container, it also links the document root of the container to /root/website/dev1. This results in deployment of the webpage on this testing system.

Job2: I named this job "Testing". This job checks whether the deployed webpage on the testing system is working or not. It works based on "status code". If the webpage is working it triggers the third job.

Job3: I named this job "Merge". Once this job is triggered it goes to the remote location i.e., Github and merges the "dev1" branch to the "master" branch. When this job completes successfully it triggers the fourth job using Build trigger.

Job4: I named this job "deploy". Once this job is triggered, Jenkins goes to the remote location i.e., Github & downloads the code in its workspace & then copy the same code into a rhel8 system at location /root/website/master/. Then this job installs a fresh OS which acts as a Production system using the docker image. As both the testing as well as production system are installed using the same docker image, therefore making testing perfectly ideal. Again during the installation of this container, it links the document root of the container to /root/website/dev1. This results in deployment of the webpage on this testing system.
