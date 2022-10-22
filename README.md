# security-headers-for-CMS

Protect your site against enemy

Webserver Configuration (Apache, Nginx, and HSTS)
To configure your webserver, you can apply the settings described below — for Apache, Nginx, and HTTP Strict Transport Security (HSTS).

# Add this to the virtual host configuration in /etc/apache2/sites-enabled/domain.conf or /etc/httpd/sites-enabled/domain.conf:

<VirtualHost *:443>
    Header always set Strict-Transport-Security "max-age=31536000"
    Header always set X-Frame-Options "deny"
    Header always set X-XSS-Protection "1; mode=block"
    Header always set X-Content-Type-Options "nosniff"
    Header always set Content-Security-Policy "default-src 'self'"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
</VirtualHost>


For nginx, you’ll have to update the configuration file. It’s usually located at /etc/nginx/nginx.conf, /etc/nginx/sited-enabled/yoursite.com (Ubuntu / Debian) or /etc/nginx/conf.d/nginx.conf (RHEL / CentOS). 

server {
    add_header Strict-Transport-Security "max-age=63072000; includeSubdomains;" always;
    add_header X-Frame-Options "deny" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Content-Security-Policy "default-src 'self'" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;
}
