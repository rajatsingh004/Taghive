## STARTED BY SETTING LOCALENV
Please create and source your virtualenv before beginning.

- So I started by setting an EC2 linux machine in AWS.
- Ran the sudo su - command to become a root user from ec2-user.
- Then install the python3 dependencies and task to run the Taskfile.yml
- Also update the python version to python3 in the Taskfile.yml
- Then I did git clone to bring the devops-assignment folder to my machine.
- Then ran the task run-app to check wheather the apps are running or not. So was able to run both the flask applications.
- Then by running the curl command using the duplicate tab option to check I was able to connect with the server when the flask applications were running. So got the deried output of Hello there.
- Then when ran the ab -m POST -H "Authorization: mytoken" -n 500 -c 4 http://127.0.0.1:5000/jobs and got continous hit to the app till I exited from it. The output generated was something like a table giving the percentage of requests served within a certain time(ms).

### THE ABOVE WAS DONE TO CHECK EVERYTHING WAS WORKING FINE OR NOT.

## ASSIGNMENT
Now the assignment begins.

### Dockerize the two included applications.
- First I install docker on the EC2 machine and started the docker service.
- After that I created the Dockerfiles for both the applications individually.
- Than I created images using them and ran them using the run command.
- Then ran the curl http://127.0.0.1:5000/hello command again after going inside the container for both applications and got the desired output. For the second container when did the curl http://127.0.0.1:5001/hello got the HTML structure with the para being requested url not found.

### Apply OWASP image hardening best practices to both containers.
Created two dockerfiles where mentioned one without OWASP practices and the other incorporated the asked securities.

### Set up automated local static image scans of the resulting images using a tool like Snyk.
- I signed up in the Snyk GUI and integrated the Snyk tool and my dockerhub account. 
- And after building the latest images through Dockerfiles in my EC2 linux system. I pushed those images to Dockerhub using docker login command.
- And after getting the results of the Snyk image test I made few chnages in the Dockerfile of the 2nd app i.e. app_b.

### Create a basic Kubernetes deployment for both applications. The deployment should incorporate any OWASP guidance for running containers.
- Here I created two separate kubernetes deployment files for the two different applications in a new deployments folder.
- The Deployment files also followed the OWASP guidlines which included the kubernetes security sheet. 

### Ensure that all steps (build, scan, and local kubernetes deployment) can be easily performed using the included task file.
- Made changes to the Taskfile provided by adding all the steps which were asked such as the build stage for building of docker images, then scan part of the build images and eventually the kubernetes deployment is to be done based on the first two steps.
