# Read Me First
The following was discovered as part of building this project:

* The JVM level was changed from '1.8' to '17', review the [JDK Version Range](https://github.com/spring-projects/spring-framework/wiki/Spring-Framework-Versions#jdk-version-range) on the wiki for more details.

# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/3.0.8/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/3.0.8/maven-plugin/reference/html/#build-image)










pipeline {
    agent any

    environment {
        // Define your database connection details
        DB_USER = 'your-database-username'
        DB_PASSWORD = 'your-database-password'
        DB_HOST = 'your-database-host'
        DB_PORT = 'your-database-port'
        DB_SERVICE_NAME = 'your-database-service-name'
    }

    stages {
        stage('Update Stored Procedure') {
            steps {
                script {
                    // Define the SQL script to update your stored procedure
                    def sqlScript = """
                        BEGIN
                            -- Your SQL code to modify the stored procedure here
                        END;
                    """

                    // Save the SQL script to a temporary file
                    def sqlScriptFile = writeFile file: 'update_script.sql', text: sqlScript

                    // Build the SQL*Plus command
                    def sqlplusCmd = """
                        sqlplus ${DB_USER}/${DB_PASSWORD}@//${DB_HOST}:${DB_PORT}/${DB_SERVICE_NAME} @${sqlScriptFile}
                    """

                    // Execute the SQL*Plus command to update the stored procedure
                    def procUpdateResult = bat(script: sqlplusCmd, returnStatus: true)

                    if (procUpdateResult == 0) {
                        echo 'Stored Procedure Updated Successfully!'
                    } else {
                        error 'Failed to Update Stored Procedure. Check logs for details.'
                    }
                }
            }
        }
    }
}

