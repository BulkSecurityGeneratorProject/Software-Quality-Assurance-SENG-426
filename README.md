# acme

## Setup
Here are the setup instructions for us. Clone this repo into a folder on your computer. From inside this folder run 'npm install' to get the node_modules folder. The node_modules folder is in the .gitignore file so we don't commit it since its "fucking massive". Once you've done that check the src/main/resources/config/application-dev.yml and edit the db info to the correct stuff for whatever machine you are on. You will then need to create a run configuration in Eclipse to run the JUnit tests for the files in the test folder. JUnit usually comes installed in Eclipse so you can just tell it what folder to run on (src/test/java/com/acme). Ask Justin for more details. 

## Development

#### Required Software

1. Java 8 or greater
2. NPM 2.13 or greater
3. Maven 3.3 or greater
4. MySQL 5.5 or greater

#### Configuration

To configure the system:

1. Run `npm install` from inside the application's folder
2. Create database schema for the application with the name of your preference (the tables are created and populated automatically during the first run)
3. Open the configuration file `src/main/resources/config/application-dev.yml` and set:
   1. `spring.datasource.url` with the database host, port and schema (defaults to **localhost**, **3306** and **acme** respectively).
   2. `server.port` with server port (defaults to **8080**)
#### Building package


After that execute `mvn spring-boot:run` from _inside_ the application's folder to run the application and navigate to [http://localhost:8080](http://localhost:8080) in your browser (note the port number might be different according to your configuration and sudo might be necessary for ports below 1024).

## Distribution

To build a distribution package:

1. Run `mvn clean package`
2. Copy `target/acme-1.0.1.war` file to a new folder
3. Inside this folder create two subfolders, one called `config` and one called `mediaResources`
4. Copy `src/main/resources/config/application-dev.yml` into the `config` folder

#### Running package

To run the distribution packaged application:

1. Create database schema for the application with the name of your preference (the tables are created and populated automatically during the first run)
2. Configure the database and server port in the `config/application-dev.yml` file as explained above
3. Run `java -jar acme-1.0.1.war` (sudo might be necessary if configured with a port below 1024)

Finally navigate to [http://localhost:8080](http://localhost:8080) in your browser (note the port number might be different according to your configuration and deployment environment).
