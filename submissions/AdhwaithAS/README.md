### **Kubernetes Challenge Submission**

This submission includes the containerization and deployment of the provided Flask app using Docker and Kubernetes (Minikube) using Jenkins CI/CD pipeline.

**Details:**

* **DockerHub Image:** [https://hub.docker.com/repository/docker/adhwaithas/flas-app-test](https://hub.docker.com/repository/docker/adhwaithas/flas-app-test)
* **Deployment YAML:** `deployment.yaml` included in this submission
* **Service YAML:** `service.yaml` included in this submission
* **Screenshots:**

  * Jenkins Overview: `screenshots/jenkins-overview.png`
       ![Pods Running](https://github.com/AdhwaithAS/devOps-challenge-1/blob/main/submissions/AdhwaithAS/screenshot/jenkins-overview.png)

  * Pods running: `screenshots/pods-running.png`
       ![Pods Running](https://github.com/AdhwaithAS/devOps-challenge-1/blob/main/submissions/AdhwaithAS/screenshot/pods.png)
  

  * Minikube Flask Service: `screenshots/service-preview.png`
       ![Minikube Flask Service](https://github.com/AdhwaithAS/devOps-challenge-2/blob/main/submissions/AdhwaithAS/screenshot/service-preview.png)


  * Flask app accessible in browser via NodePort: `screenshots/preview.png`
       ![Flask app accessible in browser via NodePort](https://github.com/AdhwaithAS/devOps-challenge-1/blob/main/submissions/AdhwaithAS/screenshot/preview.png)

**Folder Structure in this Submission:**

```
submissions/AdhwaithAS/
├─ service.yaml
├─ deployment.yaml
├─ Jenkins
├─ screenshots/
   ├─ pods.png
   └─ preview.png
   └─ service-preview.png
   └─ jenkins-overview.png
