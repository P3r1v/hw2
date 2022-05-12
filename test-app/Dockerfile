FROM registry.access.redhat.com/ubi8/nginx-118

# Add application sources
ADD test-app/nginx.conf "${NGINX_CONF_PATH}"
ADD test-app/nginx-default-cfg/*.conf "${NGINX_DEFAULT_CONF_PATH}"
ADD test-app/nginx-cfg/*.conf "${NGINX_CONFIGURATION_PATH}"
ADD test-app/*.html .

# Run script uses standard ways to run the application
CMD nginx -g "daemon off;"
ADD --chown 1001:0 app-src /tmp/src
ADD --chown 1001:0 app-src /opt/app-root/src

# Let the assemble script to install the dependencies
RUN /usr/libexec/s2i/assemble

# Run script uses standard ways to run the application
CMD /usr/libexec/s2i/run
