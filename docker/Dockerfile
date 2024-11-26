# use latest nginx
FROM nginx:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the index.html file from the host into the container
COPY ./index.html .
COPY ./index.html /usr/share/nginx/html

# Add a system user 'webapp' to run the application
RUN useradd -r -m -s /bin/bash webapp

# Switch to the 'webapp' user to avoid running as root
USER webapp

# Expose port 3000
EXPOSE 3000

# Correct the CMD to run nginx
CMD ["nginx", "-g", "daemon off;"]
