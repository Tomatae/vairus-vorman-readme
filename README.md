# Server

Currently runs on: 213.219.214.108

# Quickstart guide

> Install **terraform**, **kubectl** and **helm** locally. Or at least **terraform** to start an extra server [/terraform-extra](/terraform-extra) and continue configuration from it.

Clone the repository locally and run through the readmes from folders in following sequence:

- Prepare infrastructure [/terraform](/terraform) and possibly [/terraform-extra](/terraform-extra) for additional testing server

- Obtain KUBECONFIG through VK Cloud website. We didn't find any other way to get it.

- Configurate k8s [/k8s-prep](/k8s-prep)

- Modify Ingress [/modify-ingress-logs](/modify-ingress-logs)

- Create a GitLab Runner [/gitlab-runner](/gitlab-runner)

- Modify [.gitlab-ci.yml](.gitlab-ci.yml) if needed.

And you are good to go.

---

# Short description

> This project uses lots of automation and could contain typos.

Terraforms builds two separate cluster using VK Cloud infrastructure. One is dedecated to Postgres Database and another for app deployment. Database could be accessed only from inner network for safety reasons. App Cluster is easily configurable and by default contains 3 master nodes and 3 to 5 worker nodes. There is also a terraform script for a test server.  

This project could use both Shared and Private GitLab Runners for its CI/CD process. CI/CD configuration has 3 stages - build, test and deployment. It is possible to switch servers by adding them suitable tags.

Cluster also has an Ingress Nginx Controller that is configured to log the IP addresses, request time, response time, HTTP refereres, bytes amount, response statuses, and URI requests.

---

## Another usefull stuff

- Use `terraform output -raw ingress_floating_ip` to get ip address if something went wrong.

- The easiest way to load [.sql](sql/flight.sql) is via [test server](/terraform-extra)

- App from the [original repository](https://github.com/mik332/parrot-scbt) was modified due to usage of inaccessible docker registry. To build docker manually simply use `docker build -t mr-vairus-vorman ./app`. Still working great with docker compose or simply runs via `docker run` if you previously specift env vars for database.

- [.kube](.kube) directory contains config with sensitive data that could easily be removed but still usefull for test runs. Has to be removed before prod.

