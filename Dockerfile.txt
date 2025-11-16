FROM php:8.2-apache

# Copy your entire project to the container
COPY . /var/www/html/

# Create the registrations.txt file (if not present) and set permissions
RUN touch /var/www/html/registrations.txt && chmod 777 /var/www/html/registrations.txt

# Change Apache to listen on port 8080 instead of 80 (Render requirement)
RUN sed -i 's/80/8080/g' /etc/apache2/ports.conf /etc/apache2/sites-enabled/000-default.conf

# Expose the port Render expects
EXPOSE 8080
