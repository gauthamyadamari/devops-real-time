### This file contains information regarding the following DevOps tools:
```
     1. Jenkins
     2. Docker
     3. kubernetes(k8S)
     4. MongoDB
     5. ReactJS
     6. Flask
```
##1.Jenkins: Jenkins is an open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration, and continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat. It supports version control tools, including AccuRev, CVS, Subversion, Git, Mercurial, Perforce, ClearCase, and RTC, and can execute Apache Ant, Apache Maven, and sbt based projects as well as arbitrary shell scripts and Windows batch commands.

Builds: Builds can be triggered by various means, for example:

    (a)a webhook that gets triggered upon pushed commits in a version control system
    (b)scheduling via a cron-like mechanism
    (c)requesting a specific build URL.
    (d)after the other builds in the queue have completed
    (e)invoked by other builds

Plugins: Plugins have been released for Jenkins that extend its use to projects written in languages other than Java. Plugins are available for integrating Jenkins with most version control systems and bug databases
 --some of the plugins are as follows:
 (A) Mailer:
            Allows configuring email notifications for build results. Jenkins will send emails 
            to the specified recipients whenever a certain important event occurs, such as:

            (1)Failed build.
            (2)Unstable build.
            (3)Successful build after a failed build, indicating that a crisis is over.
            (4)Unstable build after a successful one, indicating that there's a regression
 (B) Credentials:
             (1)Allows storing credentials in Jenkins
 (C) SSH agents:
             (1)Open a SSH connection to the specified host as the specified username,
             (2)Check the default version of Java for that user,
             (3) If the default version is not compatible with Jenkins's 
                agent.jar, try to find a proper version of Java
             (4)Once it has a suitable version of Java, copy the latest agent.jar via SFTP (falling 
                back to scp if SFTP is not available),Start the agent process
2.DOCKER:
        (1).Docker is containerization tool that isolates applications and its bins/libs
        (2).Docker is lightweight, It will not have guest operating system
        (3).Docker start/stop time is fast its about 1-2 seconds
        (4).Faster for deployments
        (5).Reduces overall infrastructure and cost(for licenses)
Dockerizing applications:
        (1)To run our application on docker container we should dockerize it
3.Kubernetes:
            Kubernetes is a container orchestration tool 
          (1)Kubernetes offers features like:
                                             (1)Scheduling
                                             (2)Autohealing
                                             (3)Load Balancing:
                                             (4)Automated deployments
                                             (5)Autoscaling
EKS Cluster:
           (1)In the cluster you will have two categories one is master node and another one is worker nodes
(2)First create EKS cluster (This will setup only k8s Control Plane)
(3)Setup one or more node group


4.MongoDB:
MongoDB is a NoSQL database that uses a document data model. This means that data is stored in JSON-like documents, which are flexible and can be easily scaled. MongoDB is popular for its scalability, performance, and ease of use.

 some of the key features of MongoDB:

(1)Document data model: MongoDB stores data in flexible documents, which can be easily scaled and 
   updated.
(2)Horizontal scalability: MongoDB can be scaled horizontally by adding more servers to the 
   cluster.
(3)High performance: MongoDB is designed for high performance, even with large datasets.
(4)Ease of use: MongoDB is easy to install and use, even for developers with no prior NoSQL 
   experience.

MongoDB is a good choice for applications that need to be scalable, performant, and easy to use. It is a popular choice for web applications, mobile applications, and real-time applications  

some examples of how MongoDB can be used:

E-commerce applications: MongoDB can be used to store product information, customer data, and order data.
Social media applications: MongoDB can be used to store user data, posts, and comments.
Real-time analytics applications: MongoDB can be used to store and analyze real-time data, such as sensor data or financial market data.

5.ReactJS:
ReactJS is a JavaScript library for building user interfaces. It is declarative, efficient, and flexible. ReactJS lets you compose complex UIs from small and isolated pieces of code called "components".
some of the key benefits of using ReactJS:

(1)Declarative: ReactJS is declarative, meaning that you describe what you want to render, and 
   ReactJS takes care of the rest. This makes ReactJS code easy to read and maintain.
(2)Efficient: ReactJS is efficient because it uses a virtual DOM to update the UI. The virtual DOM 
   is a lightweight representation of the real DOM, which allows ReactJS to perform updates quickly 
   and efficiently.
(3)Flexible: ReactJS is flexible because it can be used to build a wide variety of UIs, from simple 
   static websites to complex dynamic web applications.

6.Flask:
        Flask is a microframework, which means that it does not come with a lot of built-in 
        functionality. This makes it very lightweight and easy to learn, but it also means that you 
        will need to use third-party libraries to add common features such as database abstraction, 
        form validation, and user authentication.

some of the key features of Flask:

       (1)Flexible: Flask can be used to develop a wide variety of web applications, from simple 
          websites to complex web applications.
       (2) Easy to use: Flask has a simple and intuitive API, making it easy to learn and use.
       (3)Lightweight: Flask is a microframework, which means that it is very lightweight and 
          efficient.
       (4)Extensible: Flask has a large and active community that develops high-quality extensions 
          that can add any functionality you need to your application.



CREATION OF EKS-CLUSTER

PREREQUISTES:
            1. AWS Account
            2. Install AWS CLI
            3. Install kubectl
            4.install eksctl

A. writing [eksctl.yml]  (https://raw.githubusercontent.com/gauthamyadamari/devops-real-time/main/eksctl.yml) file for creating eks cluster and the file is as follows:

 file: eksctl.yml

apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: basic-cluster-1
  region: us-east-1

nodeGroups:
  - name: ng-1
    instanceType: m5.large
    desiredCapacity: 2
  - name: ng-2
    instanceType: m5.xlarge
    desiredCapacity: 2

command for the creatiion of eks cluster:(1) eksctl create cluster -f  <file-name>
                                         (2) eksctl create cluster -f cluster.yaml

command for the  deletion of eks cluster:(1) eksctl delete cluster --name <cluster-name>


B.Creating [pod.yml](https://raw.githubusercontent.com/gauthamyadamari/devops-real-time/main/pod.yml) file :

 apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80

command for the creation of pod.yml file : (1)kubectl apply -f <file-name>
                                           (2) kubectl apply -f pod.yml
