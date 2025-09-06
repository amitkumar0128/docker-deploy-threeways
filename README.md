## 📦 Django-Todo-CICD: Terraform | Ansible | Jenkins

A DevOps demo project showcasing **three different deployment methods** — all building and running a Dockerized Django Todo App using **Docker Compose**.

> 🚀 Whether you're using **Terraform**, **Ansible**, or **Jenkins**, each tool independently provisions or deploys the app — demonstrating modular DevOps practices without tool coupling.

---

### 🛠️ Tech Stack Overview

| Layer          | Tool / Tech                             |
| -------------- | --------------------------------------- |
| App Framework  | Django (Python)                         |
| Containers     | Docker Compose (Nginx + Django + MySQL) |
| IaC            | Terraform                               |
| Provisioning   | Ansible                                 |
| CI/CD          | Jenkins (via `Jenkinsfile`)             |
| Cloud Provider | AWS (EC2 only)                          |

---

## 🌐 Application Architecture

* Django Todo App running in Docker container
* MySQL container as database
* Nginx container as reverse proxy
* All containers are defined and managed in a single `docker-compose.yml`
* App exposed on **port 80** (HTTP)

---

## 🧩 Deployment Options

You can deploy this project in **three different ways**, each isolated from the other.

| Method        | Provisions EC2 | Installs Docker                                 | Deploys App                 | Destroys EC2                    |
| ------------- | -------------- | ----------------------------------------------- | --------------------------- | ------------------------------- |
| **Terraform** | ✅ Yes          | ✅ Yes (remote-exec)                             | ✅ Yes (`docker-compose up`) | ✅ Yes (`terraform destroy`)     |
| **Ansible**   | ✅ Yes          | ✅ Yes (via playbook)                            | ✅ Yes (`docker-compose up`) | ✅ Yes (`destroy-todo-app.yaml`) |
| **Jenkins**   | ❌ No           | ❌ Requires Docker pre-installed on Jenkins host | ✅ Yes (`Jenkinsfile`)       | ❌ No                            |

---

## 📁 Project Structure

```bash
terra-ansible-jenkins-docker/
├── ansible/
│   ├── playbook.yaml
│   └── destroy-todo-app.yaml
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── providers.tf
│   └── terraform.tf
├── docker-compose.yml
├── .env
├── Jenkinsfile
├── manage.py
└── ...
```

---

## ⚙️ Requirements

> Install these tools based on which deployment method you want to use.

| Tool           | Installation Required              |
| -------------- | ---------------------------------- |
| Terraform      | ✅ (for Terraform-based deployment) |
| Ansible        | ✅ (for Ansible-based deployment)   |
| Jenkins        | ✅ (for Jenkins-based deployment)   |
| Docker         | ✅ (Jenkins host and EC2 instances) |
| Docker Compose | ✅                                  |

---

### 🔐 AWS Credentials

To allow Terraform and Ansible to provision EC2 instances:

* Export your AWS credentials as environment variables:

```bash
export AWS_ACCESS_KEY_ID=your_access_key
export AWS_SECRET_ACCESS_KEY=your_secret_key
```

---

## 🚀 1. Deploy Using Terraform

### 🔧 Steps

```bash
cd terraform
terraform init
terraform plan
terraform apply
```

> This will:
>
> * Create EC2 instance + key pair + security group
> * SSH into EC2 using `remote-exec`
> * Clone the repo
> * Install Docker & Docker Compose
> * Run `docker-compose up` to launch the app

### 🧼 Teardown

```bash
terraform destroy
```

---

## ⚙️ 2. Deploy Using Ansible

### 🔧 Steps

1. Run the playbook:

```bash
cd ansible
ansible-playbook playbook.yaml
```

> This will:
>
> * Provision an EC2 instance
> * Install Docker & Docker Compose
> * Clone this repo
> * Run `docker-compose up`

### 🧼 Teardown

```bash
ansible-playbook destroy-todo-app.yaml
```

---

## 🧪 3. Deploy Using Jenkins

### Prerequisites

* Jenkins must be running on a Linux host with:

  * Docker installed
  * Docker Compose installed
* AWS credentials not required (no EC2 provisioning)

### 🔧 Steps

1. Create a **Jenkins pipeline project**
2. Point it to this repo and use `Jenkinsfile` as the pipeline script
3. Run the job

> This will:
>
> * Clone the repo
> * Build & run the app using Docker Compose on the **Jenkins host**

---

## 🧪 App Access

Once deployed (via any method), access the app at:

```
http://<public-ec2-ip>
```

You’ll see the Django Todo App UI.

---

## 🎯 Goal of This Repo

This project is designed to demonstrate:

* Three **independent deployment strategies**
* Usage of **Docker Compose** across tools
* Clean separation between **IaC (Terraform)**, **Provisioning (Ansible)**, and **CI/CD (Jenkins)**
* Real-world DevOps practices for **portfolio** and **job-readiness**

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 🙋‍♂️ Author

**Amit Kumar**
🔗 [GitHub](https://github.com/amitkumar0128)

