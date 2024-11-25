# cbiproject


# LIST OF PROGRAMS AND MICROSERVICES CREATED IN THIS PROJECT:
- Postgres instance
- Go containerized microservice
- PGAdmin containerized microservice
- Cloud Build trigger


# INSTALL AND RUN
1. Create a Google Cloud project for which you have organization and administrative privileges
- Ensure you have downloaded and authenticated yourself with Google Cloud CLI
- Enable billing
- Enable the following APIS/services: Cloud Build, Cloud Run, Cloud SQL
- Ensure you have ownership and service-running permissions with the above APIs
2. Create a postgres instance on Cloud SQL
- Open the SQL tab of the google cloud project and hit "Create Instance" using PostgreSQL. Choose the region of your choice.
- Use gcloud command tools to set the instance's default user and password.
- Use gcloud command tools to create a database, chicago-business-intelligence, in the postgres instance on google cloud sql.
3. Create a github repository with the starter documents.
- Ensure the Dockerfile, cloudbuild.yaml, and the required go files are in the repository.
- In the main.go and cloudbuild.yaml files, ensure that your postgres instance connection name are correct, along with the port number and login user/passwords.
4. Create a Cloud Build trigger.
- Navigate to the triggers section of the Cloud Build google cloud console.
- Select "create trigger," and follow the required fields ensuring that this is connected to the github repository created in step 3.
- A build should be triggered; navigate to the Cloud Build logs and wait until it completes.
5. Navigate to the Cloud Run tab of the cloud console and ensure that the two microservices, go-microservice and pg-admin, are up and running.
6. Add the postgres server to PGAdmin4
- Open the pg-admin microservice in the console's Cloud Run tab. Click the url at the top of the service dashboard.
- Log into PGAdmin using the credentials specified in the cloudbuild.yaml file.
- Click the "Add Server" option. Provide any relevant name on the default page. On the "Connections" page, place the host address, username and password information specified in the init() function of the main.go file, and add the server.
7. View the data uploaded to the database you connected.
- Wait for the go-microservice logs to show that rows have been added to one of the three tables in the database you connected in step 6.
- Navigate to the PGAdmin4 site and click "View all rows" on the updated table.
