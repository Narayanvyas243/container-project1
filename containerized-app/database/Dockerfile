FROM postgres:16-alpine

# Set environment variables 
ENV POSTGRES_DB=mydb
ENV POSTGRES_USER=myuser
ENV POSTGRES_PASSWORD=mypassword

# Copy initialization script
COPY init.sql /docker-entrypoint-initdb.d/

EXPOSE 5432
