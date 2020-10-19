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
kubectl apply -f event-bus-depl.yaml
kubectl get services
kubectl apply -f posts-depl.yaml
//event-bus
docker build -t hodhod212/event-bus .
docker push hodhod212/event-bus
//posts
docker build -t hodhod212/posts .
docker push hodhod212/posts
kubectl get deployments
kubectl rollout restart deployment posts-depl
kubectl rollout restart deployment event-bus-depl
kubectl get pods
kubectl logs event-bus-depl-5b698fc96-vhgjf
kubectl logs posts-depl-77fc49b8b8-fdj2w
cd ..
cd comments
docker build -t hodhod212/comments .
docker push hodhod212/comments
cd ..
cd moderation
docker build -t hodhod212/moderation .
docker push hodhod212/moderation
cd ..
cd query
docker build -t hodhod212/query .
docker push hodhod212/query
cd ..
cd infra/k8s
kubectl apply -f .
kubectl get pods
cd ..
cd ..
cd event-bus
docker build -t hodhod212/event-bus .
docker push hodhod212/event-bus
kubectl get pods
kubectl logs comments-depl-b7cc6cc67-75mss
kubectl logs moderation-depl-5c7c8656f7-hpqp2
kubectl logs query-depl-54557565bc-lqdcp
//
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.30.0/deploy/static/mandatory.yaml
//
kubectl apply -f ingress-srv.yaml
//
cd ..
cd client
docker build -t hodhod212/client .
docker push hodhod212/client
cd ..
cd infra/k8s
kubectl apply -f client-depl.yaml
cd ..
cd ..
cd client
docker build -t hodhod212/client .
docker push hodhod212/client
kubectl rollout restart deployment client-depl
cd ..
cd posts
docker build -t hodhod212/posts .
docker push hodhod212/posts
kubectl rollout restart deployment posts-depl
cd ..
cd infra/k8s
kubectl apply -f client-depl.yaml
kubectl get pods
