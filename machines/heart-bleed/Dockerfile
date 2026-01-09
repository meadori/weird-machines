# Use Debian Wheezy as the base image for Linux x64
FROM debian:wheezy

# Install Nginx and OpenSSL
RUN apt-get update && apt-get install -y \
    nginx \
    openssl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Create a self-signed SSL certificate
RUN mkdir -p /etc/nginx/ssl && \
    openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/nginx.key \
    -out /etc/nginx/ssl/nginx.crt \
    -subj "/C=US/ST=State/L=City/O=Organization/OU=OrgUnit/CN=localhost"

# Configure Nginx to use the SSL certificate
RUN sed -i 's/# listen 443 ssl;/listen 443 ssl;/' /etc/nginx/sites-available/default && \
    sed -i 's/# include snippets\/snakeoil.conf;/ssl_certificate \/etc\/nginx\/ssl\/nginx.crt;\n    ssl_certificate_key \/etc\/nginx\/ssl\/nginx.key;/' /etc/nginx/sites-available/default

# Expose port 443 for TLS
EXPOSE 443

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]