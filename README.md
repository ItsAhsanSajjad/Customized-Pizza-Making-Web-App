# Pizzeria Web Application

## Introduction
This is a web application for managing a pizzeria, including customer profiles, order management, pizza customization, order tracking, and reviews.

## Features
- Customer Profile Management
- Order Creation and Management
- Pizza Builder for Custom Pizzas
- Order Tracking
- Review Submission and Display

## Built With
- **Java 23**: The core programming language used for developing the application.
- **Spring Framework**: Used for dependency injection, transaction management, and web MVC.
- **Hibernate**: Used for ORM (Object-Relational Mapping) to interact with the database.
- **PostgreSQL**: The primary database used for storing application data.
- **Apache Tomcat**: The servlet container used for deploying the web application.
- **Thymeleaf**: The templating engine used for rendering dynamic web pages.
- **Maven**: Used for project management and build automation.
- **Log4j**: Used for logging application events.
- **Bootstrap**: Used for responsive UI design.
- **Angular**: Used for building the staff-facing front-end application.

## Prerequisites
- Java 23 or later
- Apache Tomcat 8.5 or later (if not using the embedded web server)
- PostgreSQL database (or any other supported database) 

![Home page](documentation/home.png?raw=true)

The app features a pizza builder that lets the user build a custom pizza from a number of 
ingredients, select a crust, size, bake and cut styles and desired quantity.

![Pizza Builder](documentation/builder.png?raw=true)

The user can also opt for one of the specialty pizzas, and either order one of those predefined templates or customize it however they like.

### Pizza Builder on iPad

![Pizza Builder on iPad](documentation/gifs/builder_ipad.gif?raw=true)

### Pizza Builder on iPhone

![Pizza Builder on iPhone](documentation/gifs/builder_mobile.gif?raw=true)

### Pizza Template

![Pizza Builder for a template](documentation/gifs/builder_template_mobile.gif?raw=true)

### Checkout

![Checkout](documentation/gifs/checkout_as_guest_mobile.gif?raw=true)

### Write a Review

![Write a review](documentation/gifs/write_review_mobile.gif?raw=true)

### Registration

![Registration](documentation/gifs/registration_mobile.gif?raw=true)

### Login

![Login](documentation/gifs/login_mobile.gif?raw=true)

## Design

### High-level Package Diagram

![Package diagram](https://rawgit.com/pzinsta/pizzeria/master/documentation/package_diagram.svg)

### Domain Model Class Diagram

![Domain model class diagram](https://rawgit.com/pzinsta/pizzeria/master/documentation/domain_model_class_diagram.svg)

### Database Schema

![Database schema](https://rawgit.com/pzinsta/pizzeria/master/documentation/database_schema.svg)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

#### 1. [Maven](https://maven.apache.org/download.cgi)
#### 2. [Node.js and npm](https://nodejs.org/en/)
#### 3. [Braintree](https://sandbox.braintreegateway.com/) API keys
1. Go to the [sandbox version](https://sandbox.braintreegateway.com/) of Braintree. 
2. Sign up / log in.
3. Go to Settings - API Keys and get the following:
   1. Merchant ID
   2. Public key
   3. Private key (you'll have to click 'View' to see it)
#### 4. [Google reCAPTCHA](https://www.google.com/recaptcha/admin) keys

1. Go to Google reCAPTCHA and register a new site. 

![recaptcha site registration](documentation/recaptcha_register_site.PNG?raw=true)

2. Get the public (site) and private (secret) keys.

![recaptcha keys](documentation/recaptcha_keys.PNG?raw=true)

The keys above are not valid, so don't try to use them.

### Running the app

#### 1. Clone the repository

```
git clone https://github.com/ItsAhsanSajjad/Customized-Pizza-Making-Web-App.git
```

#### 2. Build the .war file

```
mvn clean package
```

#### 3. Launch the app

The application won't start unless all the following properties are provided.

| Property              | Description |
| --------------------- |-------------|
| braintree.merchantId  | Braintree merchant ID |
| braintree.publicKey   | Braintree public key |
| braintree.privateKey  | Braintree private key |
| recaptcha.public.key  | Google reCAPTCHA public (site) key |
| recaptcha.private.key | Google reCAPTCHA private (secret) key |

We have two options here. 

##### Option 1. Set the properties as environment variables.

If you've set the properties as environment variables, you can run the following command to start the app:

```
java -jar webapp/target/dependency/webapp-runner.jar --port 8081 --path pizzeria webapp/target/*.war
```

##### Option 2. Pass the properties as JVM arguments

In this case the command is going to be a bit more complicated.

```
java -Dbraintree.merchantId=<your Braintree merchant ID> -Dbraintree.publicKey=<your Braintree public key> -Dbraintree.privateKey=<your Braintree private key> -Drecaptcha.private.key=<your reCAPTCHA private key> -Drecaptcha.public.key=<your reCAPTCHA public key> -jar webapp/target/dependency/webapp-runner.jar --port 8081 --path pizzeria webapp/target/*.war
```

You can modify the port and the context path. Also, there are other [options](https://github.com/jsimone/webapp-runner#options) available.

#### 4. Verify

Go to [http://localhost:8081/pizzeria/](http://localhost:8081/pizzeria/) to check that the app is up and running.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

This project was originally created by pzinsta (https://github.com/pzinsta). I have updated and extended the project to include additional features and improvements.
