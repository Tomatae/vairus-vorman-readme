# Ingress logs
To modify logging with nginx check the conf file.

For now, this configuration logs the IP address, request time, response time, HTTP referer, bytes amount, response status, and URI request.

All client request logs are going to the /var/log/nginx/access.log file inside the Nginx Ingress controller's container. You can also configure the logging to send the logs to an external logging system.

---

To apply current conf use:

`kubectl patch deployment ingress-nginx-controller -n ingress-nginx --patch-file nginx-controller-patch.yaml`

Copy controller name from `kubectl get po -n ingress-nginx` and insert into the following command:

`kubectl logs -f <name> -c controller -n ingress-nginx`

For example:

`kubectl logs -f ingress-nginx-controller-6f7b5448b8-l4bdb -c controller -n ingress-nginx`
