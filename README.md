Create Storage Class:
A StorageClass in Kubernetes is used to define different types of storage available in your cluster. This step involves creating a StorageClass to provision storage for MongoDB.
kubectl apply -f createStorageClass.yaml

Deploy Persistent Volume:
PVs in Kubernetes are storage resources provisioned by an administrator. This step deploys a PersistentVolume, which is a piece of storage in the cluster that has been provisioned by an administrator.
kubectl apply -f createPersistentVolume.yaml

Deploy Persistent Volume Claim:
PersistentVolumeClaim are requests for storage by a user. This step deploys a persistentVolumeClaim, which is a request for storage by a user. PVCs consume PV resources and are used by pods.
kubectl apply -f createPersistentVolumeClaim.yaml

Install MongoDB:
This step involves deploying MongoDB onto the Kubernetes cluster. You can either set it up as a standalone instance or as a replica set, depending on your requirements. The YAML file (createDeployment.yaml) should contain the necessary configurations for MongoDB deployment.
kubectl apply -f createDeployment.yaml

Deploy Service:
Services in Kubernetes provide a way to expose your application to external traffic or other applications within the cluster. This step deploys a Service for MongoDB to allow other parts of your application to communicate with the database.
kubectl apply -f createService.yaml

Check the Database:
After deploying MongoDB, it's crucial to ensure its proper functionality. A common method to verify this is by accessing the MongoDB instance through tools such as MongoDB Compass. The login credentials (username and password) specified in the deployment file, along with the designated port (32000) outlined in the service file, should be utilized for authentication and connection. This process allows us to confirm the database's operational status and ensure it's ready for use by your application.

Deploy Configuration and Secrets:
Configuration files and secrets are essential for managing the settings and sensitive information needed by your application. This step involves deploying a ConfigMap and a Secret to provide configuration settings and credentials for MongoDB.
kubectl apply -f createConfigMap.yaml
kubectl apply -f createMongoDbSecret.yaml

Deploy StatefulSet:
A StatefulSet in Kubernetes is used for managing stateful applications, like databases. This step involves deploying a StatefulSet for MongoDB, which defines a replica set with multiple pods running MongoDB instances. This ensures high availability and data redundancy.
kubectl apply -f createStatefulSet.yaml

Deploy Headless Service:
A headless Service in Kubernetes is used when you don't need load balancing or a single stable IP. This step is optional and involves deploying a headless Service for MongoDB if needed.
kubectl apply -f createHeadlessService.yaml
Verification:

kubectl get pods
Ensure all MongoDB replicas are running without issues.
