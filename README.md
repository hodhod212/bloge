# bloge

Microservices
////////////
docker build .
docker run bfc37428ce98
//
docker build -t hodhod212/event-bus .
docker run hodhod212/event-bus
///
docker build -t hodhod212/posts:0.0.1 .
//
cd infra/k8s
kubectl apply -f posts.yaml
kubectl get pods
kubectl exec -it posts sh
ls
exit
kubectl logs posts
kubectl delete pod posts
kubectl apply -f posts.yaml
kubectl describe pod posts
//
kubectl apply -f posts.depl.yaml
kubectl get deployments
kubectl describe deployment posts-depl
kubectl delete deployment posts-depl
kubectl apply -f posts.depl.yaml
//
cd ..
cd posts
docker build -t hodhod212/posts:0.0.5 .
cd ..
cd infra/k8s
kubectl apply -f posts.depl.yaml
kubectl get deployments
kubectl get pods
kubectl logs posts-depl-55f786b75c-f2pkb
//after change to version latest
kubectl apply -f posts.depl.yaml
kubectl get deployments
cd ..
cd posts
docker build -t hodhod212/posts .
docker push hodhod212/posts
kubectl rollout restart deployment posts-depl
kubectl get pods
kubectl logs posts-depl-cbf4b44db-smdlr
cd ..
cd infra/k8s
kubectl apply -f posts-srv.yaml
kubectl get services
kubectl describe service posts-srv
cd ..
cd event-bus
docker build -t hodhod212/event-bus .
docker push hodhod212/event-bus
cd ..
cd infra/k8s
kubectl apply -f event-bus-depl.yaml
kubectl get pods
