# NGINX Proxy Manager
This repository contains the configuration file for setting up NGINX Proxy Manager, a powerful reverse proxy solution. NGINX Proxy Manager allows you to easily manage proxy hosts and SSL certificates for your domains or subdomains.

## Prerequisites
Before you begin, make sure you have Docker and Docker Compose installed on your system.

## Installation
 
### To install and run NGINX Proxy Manager, follow these steps:

1. Clone this repository to your local machine.
 
2. Open a terminal and navigate to the repository directory.
 
3. Modify the docker-compose.yml file to suit your needs, such as updating the volume paths if desired.
 
4. Run the following command to start NGINX Proxy Manager:
 
```bash
docker-compose up -d
```
 
This command will pull the necessary Docker image and start the NGINX Proxy Manager container.
 
Wait for the container to start successfully. You can check the logs using the command:
 
```bash
docker-compose logs -f
```
 
Once you see the message "Server listening on 0.0.0.0:81" in the logs, NGINX Proxy Manager is up and running.
 
## Accessing NGINX Proxy Manager
 
To access the NGINX Proxy Manager web interface for the first time, you may need to add a firewall rule to allow access from your local machine to the VPS on port 81. This step is necessary if your VPS has firewall rules in place, such as those implemented by platforms like Google Cloud or AWS.
 
### Please follow these steps to add the firewall rule:
 
1. Determine your local machine's IP address. You can do this by searching for "What is my IP address" on any search engine.
 
2. Log in to your VPS and navigate to your firewall or network settings.
  
3. Add a new rule to allow inbound traffic from your local machine's IP address on port 81.
  
Save the changes to apply the new firewall rule.
 
After adding the firewall rule, you can access the NGINX Proxy Manager web interface by opening a web browser and entering the following URL:
 
```bash
http://<vps-ip>:81
```

Replace `<vps-ip>` with the IP address of your VPS. This should allow you to access the NGINX Proxy Manager web interface from your local machine and proceed with the setup.
 
> Note: the first login must be done with the user `admin` and the password `changeme`.
 
Once you have successfully set up the NGINX Proxy Manager and generated the SSL certificate, you can remove the firewall rule allowing access to port 81, as the proxy host will handle the SSL termination and proxy requests to the appropriate services.

## Setting up Proxy Hosts and SSL Certificates

To set up a new proxy host and SSL certificate, follow these steps:

> Make sure your domain or subdomain is already pointing to your VPS IP address with the correct DNS records.
 
1. Access the NGINX Proxy Manager web interface by opening a web browser and entering the following URL:
 
```bash
http://<vps-ip>:81
```
 
2. Log in to the NGINX Proxy Manager using your admin account credentials.

3. Click on "Proxy Hosts" in the top navigation bar.

4. Click on the "Add Proxy Host" button.

5. Fill in the required details, including the domain or subdomain, the forward hostname or IP (where the traffic will be forwarded to), and the forward port.

6. Switch to the SSL tab, enable SSL for the proxy host, and choose the appropriate SSL certificate from the dropdown menu. If you don't have a certificate, you can generate one using Let's Encrypt by selecting

## Conclusion
 
After completing the initial setup and generating the SSL certificate, you can access the NGINX Proxy Manager web interface using the domain or subdomain you have chosen for the proxy host. You no longer need to access it through the IP address and port 81. This allows for a more convenient and consistent access experience when managing your proxy hosts and SSL certificates.
