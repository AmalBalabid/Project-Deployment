
# Deploying a Spring Boot app on Heroku


The following steps show how to deploy your project using Git and Heroku CLI.
### You must have a Heroku account
* Create a Heroku account [Heroku’s Signup Page](https://signup.heroku.com/)

### Download Heroku CLI from the Heroku Dev Center: 
* [Heroku Dev Center](https://devcenter.heroku.com/articles/heroku-cli#download-and-install). Heroku CLI is a command line application that allows you to create, publish and manage Heroku applications from the command line.

### Login using your email and password
```
heroku login
```
You will be prompted to enter your Heroku account’s email and password. After login, you can proceed with the deployment.

### Set up your project before deployment

* Add this plugin to your pom.xml file

```
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-compiler-plugin</artifactId>
	<version>3.1</version>
	<configuration>
		<source>1.7</source>
		<target>1.7</target>
	</configuration>
</plugin>
```

* Make sure to target the correct Java runtime environment.

* Then you should create an application.properties file in your project if you're targeting a runtime environment other than Heroku's default JDK 1.8 runtime environment. You can do this by specifying your desired java runtime environment like such:
application.properties:
```
java.runtime.version=11 #change your version here
```

### Set up Git and create a Heroku app

* Create a local Git repository for the project

Run the following commands from the root directory of your project.
```
git init
git add .
git commit -m "deployment"
```
* Then, create a new Heroku app using this command:
```
heroku create <YOUR_PROJECT_NAME>
```
Note: app name must be unique.

### Deploy the app to Heroku
* In this step, you can deploy your project by pushing the code to the remote repository named heroku which was created by the heroku create command.
```
git push heroku master
```
* The deployment will take some time. You should see the build logs on your terminal. Once your project is deployed, you can open it using this command
```
heroku open
```
  
* The app should open in the system’s default browser.

* Finally, you can see the logs of your project anytime by running
```
heroku logs --tail
```