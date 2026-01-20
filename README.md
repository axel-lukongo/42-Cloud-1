# Cloud-1: Automated Infrastructure Deployment with Ansible on AWS

## Overview
This project is an evolution of the **Inception** subject, transitioning from local virtualization to a professional Cloud environment. The objective was to architect and deploy a multi-service Docker infrastructure on a remote instance provided by **AWS**, ensuring full automation and process isolation.

> "There is no cloud, it's just someone else's computer."

## The Core: Professional Automation with Ansible
While the subject allows for various tools, I chose to place **Ansible** at the heart of this project.

### Why Ansible for this Project?
* **Zero Manual Configuration:** The deployment is fully automated; the only assumption is a fresh Ubuntu 20.04 LTS instance with Python and SSH.
* **Scalability:** The scripts are designed to deploy the entire site on multiple servers in parallel.
* **Idempotency:** I leveraged Ansible to ensure the server state remains consistent across multiple runs without unintended side effects.
* **Professional Workflow:** Moving away from manual terminal commands to version-controlled automation scripts.

### Key Ansible Implementation Details:
1.  **System Provisioning:** Automated the installation of Docker, Docker-compose, and necessary dependencies on the AWS EC2 instance.
2.  **Security Hardening:** Configured firewall rules and limited public access to ensure the database is isolated and inaccessible from the internet.
3.  **Docker Orchestration:** Orchestrated the lifecycle of the containers by managing the deployment of the `docker-compose.yml` file.
4.  **Service Configuration:** Automated the setup of WordPress and PHPMyAdmin to connect seamlessly with the SQL database.

## Infrastructure Architecture
The setup follows the strict rule of **one process per container**.

* **Cloud Provider:** AWS (Amazon Web Services).
* **Operating System:** Ubuntu 20.04 LTS.
* **Services Deployed:**
    * **Nginx:** Acting as the entry point with **TLS/HTTPS** support.
    * **WordPress:** A functional site that persists all data (images, users, posts) even after reboots.
    * **MariaDB/MySQL:** The relational database backend.
    * **PHPMyAdmin:** For database management via a web interface.

## Reliability and Persistence
* **Auto-Restart:** All services are configured to restart automatically if the server is rebooted.
* **Data Persistence:** I used Docker volumes to ensure that all WordPress content and database entries survive container or server restarts.
* **Security:** The server is configured to use TLS for secure communication, and sensitive services are kept off the public internet.

## How to Run
To deploy the entire infrastructure from scratch using the Ansible playbook:

```bash
ansible-playbook -i inventories/host.yml playbook.yml
