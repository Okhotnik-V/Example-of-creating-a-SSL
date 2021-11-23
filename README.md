# Example-of-creating-a-SSL
<h3>Step by step instructions Docker-compose  (nginx + letsencrypt(certbot) + spring)</h3>
<h4>Let's set everything up for work :)</h4>

1) Install docker and docker-compose on the working operating system (which will serve the server)
2) A convenient way to run your program on the server. (I will use docker-compose)
3) Create a folder for the project (I named nginx)

<h4>Great now you can start serious work!</h4>

4) In this folder we create a docker-compose.yml file (Example https://github.com/Okhotnik-V/Example-of-creating-a-SSL/blob/main/nginx/docker-compose.yml)
<h4>Let's briefly understand how it works. webserver redirects our port and returns the certificate. certbot creates a certificate. Now the question arises how to combine them? It's simple, let's use joint volumes. We also set the configuration file via volumes.<h4>

5) Create a folder nginx, and in it the file nginx.conf. In this file, we redirect from port 80 to 443. We also configure it to return the certificate. And we redirect to our java application. (https://github.com/Okhotnik-V/Example-of-creating-a-SSL/blob/main/nginx/nginx/nginx.conf)
6) Сreate a certificate, command: docker compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ -d you____site.org
7) docker-compose up 
8) Can be enjoyed)
  
<h3>The certificate is valid for only 3 months. To create a new one, run the command: docker compose run --rm certbot renew</h3>
