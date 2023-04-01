# 34ml_task
Provided in the repo 3 files, one jenkins file and 2 docker files.
To deploy the Todo app into a docker image, create a pipeline in Jenkins putting the jenkins file in that pipeline.
Make sure that jenkins has all required plugins : NodeJs, Docker 
Important note**: before pasting the jenkins file in Jenkins pipeline, change the following fields in the 3rd stage "Build Release Image and Push to Docker Hub":
                  1-DOCKERHUB_USERNAME ---> change it with your dockerhub username.
                  2-DOCKERHUB_PASSWORD ---> change it with your dockerhub password.
                  3-DOCKERHUB_REPO ----> change it with your dockerhub repository.

Then, you should build the pipeline and the following will happen:
      1- first stage will build a docker image containing the Todo app using the test dockerfile and runing tests on it.
      2- second stage will run the docker image built from stage 1
      3- third stage will build the image using the build dockerfile and push the image to the docker hub repository that you will specify
      
Finally after running the pipeline, a docker image containing the Todo app will be pushed to the dockerhub repo.      
      
