A Docker stack running Wordpress over MySQL, connected via PHP-FPM to an SSL-enabled Nginx server. Assumes use of a self-signed cert for local development. (Production will replace local certs with Certbot or similar.)

To stand up a new project:
- uncomment lines in .gitignore as indicated
- change "example.com" in etc/nginx/nginx.conf to project domain
- generate keys and ciphers via openssl
- assign appropriate values to variables in .env
- give network in docker-compose.yml a project-specific name (to distinguish from other active docker networks)
- `docker-compose up -d` to initialize database and fetch Wordpress code
- connect to WP instance to complete project init

Refs:
- [Install/configure Wordpress on Docker](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose) - uses Certbot
- [Create self-signed certs for Nginx](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-18-04)
- [Use dnsmasq](https://www.stevenrombauts.be/2018/01/use-dnsmasq-instead-of-etc-hosts/) to resolve a fake TLD for local development and avoid having to make repeated changes to /etc/hosts
