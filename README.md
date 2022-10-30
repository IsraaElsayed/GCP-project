Deploy Python Application ![Project link] (https://github.com/atefhares/DevOps-Challenge-Demo-Code
###############################
    • Docrize python web application using docker
    • Pull redis image from docker Hub
    • push 2 image to gcr on GCP
    
                     gcloud auth configure-docker gcr.io
                    docker tag python-app gcr.io/project-id/python-app
                     docker push gcr.io/project-id/python-app

                      docker tag redis gcr.io/project-id/redis
                       docker push gcr.io/project-id/redis

###############################
Infrastructure Resoureces on GCP

Create VPC
    • subnets (management subnet & restricted subnet)
    
    • Management subnet has the (NAT gateway , Private vm)
    
    • Restricted subnet has the (Private standard GKE cluster (private control plan)) Notes:
    
    . Restricted subnet must not have access to internet
    
    . All images deployed on GKE must come from GCR or Artifacts registry.
    
    . The VM must be private.
    
    . Deployment must be exposed to public internet with a public HTTP load balancer.
    
    . All infra is to be created on GCP using terraform
    
    . Deployment on GKE can be done by terraform or manually by kubectl tool.
    
    . Don’t use default compute service account while creating the gke cluster, create custom SA and attach it to your nodes.
    
    . Only the management subnet can connect to the gke cluster.
    
To run terraform

     terraform init
     terraform apply
     
     
TO connect cluster

  gcloud container clusters get-credentials mycluster --zone us-central1-a  --project <project id
  
  gcloud compute ssh mymachine --project <project-id> --zone us-central1-a


##################


To deploey in cluster

kubectl apply -f app.yml

kubectl apply -f services.yml
