# Building and Deploying a Train Operations Application with Tomcat

## Prerequisites
- **Java Installation:** Ensure that you have Java Development Kit (JDK) installed on your system.
- **Maven Installation:** Make sure you have Apache Maven installed on your system.
- **Tomcat Installation:** Download and install Apache Tomcat 9 from the official website.

## Build the Java Project
- Run the following Maven command to clean and install the project:
  ```bash
  mvn clean install
  ```

## Deploy to Tomcat
- Copy the WAR file generated in the previous step to the `webapps` directory within the Tomcat installation directory:
  ```bash
  cp target/train-operations.war /path/to/tomcat/webapps/
  ```
  Replace `/path/to/tomcat` with the actual path to your Tomcat installation directory.

## Start Tomcat
- Navigate to the `bin` directory within the Tomcat installation directory.
- Start Tomcat using the following command:
  ```bash
  ./startup.sh   # For Unix/Linux
  ```
  ```bash
  startup.bat   # For Windows
  ```

## Accessing the Web Application
- Once Tomcat has started and deployed your application, you can access it via a web browser:
  ```
  http://localhost:8080/train-operations/
  ```
  