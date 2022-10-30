Deploy a python web application on GKE. if you need to know more about app you can go and read this readme file https://github.com/atefhares/DevOps-Challenge-Demo-Code in short its python app depend on redis

1. we need to build our image using docker and push it to GCR
Build image and upload to GCR
docker build -t <img-name> .
docker tag <img-name> gcr.io/<project-id>/<img-name>
docker push gcr.io/<project-id>/<img-name>
now we need to build infrastructure by
cd terraform/
terraform init
terraform apply 
