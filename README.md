Install Operator
============================
kubectl config set-context --current --namespace=splunk
kubectl apply -f splunk-operator.yaml

After starting the operator, you should see a single pod running within your namespace:

kubectl get pods
NAME                               READY   STATUS    RESTARTS   AGE
splunk-operator-75f5d4d85b-8pshn   1/1     Running   0          5s

To remove all Splunk deployments and completely uninstall the Splunk Operator, run:
============================

kubectl delete standalones --all
kubectl delete licensemasters --all
kubectl delete searchheadclusters --all
kubectl delete indexerclusters --all
kubectl delete spark --all
kubectl delete -f splunk-operator.yaml


Install Search Head Cluster and Indexer Cluster
(make sure you are in the correct namespace)
===========================
kubectl apply -f splunk-cluster-deployment.yaml


To Remove All deployments
============================
kubectl delete SearchHeadCluster splunkkit
kubectl delete IndexerCluster splunkkit


The enterprise.splunk.com/delete-pvc finalizer is optional, and may be used to tell the Splunk Operator that you would like it to remove all the Persistent Volumes associated with the instance when you delete it.
