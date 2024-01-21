# Use the official Nagios XI image
FROM nagios/nagios-xi:latest

# Copy your Nagios configuration files into the container
COPY etc/ /usr/local/nagios/etc/

# Expose the default ports for Nagios web interface and NRPE
EXPOSE 80 5666

# Set environment variables if needed
ENV NAGIOSADMIN_USER=admin
ENV NAGIOSADMIN_PASS=admin_password

