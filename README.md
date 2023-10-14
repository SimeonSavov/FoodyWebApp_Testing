# FoodyWebApp_Testing
Welcome to the Foody Web Application Testing repository. This repository documents my comprehensive testing efforts on the Foody web application. As a manual tester, my primary goal is to ensure that the application functions seamlessly as per the specified use cases. This involves creating test cases, identifying and thoroughly documenting any discovered bugs, and maintaining detailed records using the provided Test Management and Bug Tracker Template.

## Overview 

The primary objective of this testing effort is to ensure that the Foody web application functions as expected according to the provided use cases outlined in the SRS document. This involves creating manual test cases for each use case and identifying and documenting any bugs or issues that are discovered during the testing process.

## Software Requirements

### Introduction

The objective of this document is to provide a description of the Foody application (also referred to as Foody or The App). It will present an overview of the key functionalities.

### Scope
This document includes high-level descriptions of the basic functionalities of Foody, such as user registration, login, profile editing, food creation, and management. It does not cover any special user (Administrator) functionalities.

### Overall Description

#### System Environment 

Foody hosts two primary actors: unregistered/non-logged users and registered/logged users. Both can access their respective parts of the application via the internet on the following URL: [FoodyApp URL](http://softuni-qa-loadbalancer-2137572849.eu-north-1.elb.amazonaws.com:85/)

#### Key Features

-   Unregistered/non-logged users have access only to the Home page of The App, with the option to either SIGN UP or LOG IN.
-   Registered/logged users have access to main functionalities, including Profile editing, Food creation, and Food management.

#### Use Cases

1.  **Use Case 1 (Home Page):** Users should be able to access The Foody App from its designated URL via the Internet, which should load the Home page, appropriate to the user's logged-in status (unregistered/non-logged or registered/logged).
    
2.  **Use Case 2 (User Registration):** Unregistered users should be able to successfully go through the Sign-Up process. This involves the utilization of fields such as Username, Email, First name, Middle Name, Last name, Password, and Repeat Password, all subject to their respective constraints and character type acceptance.
    
3.  **Use Case 3 (User Sign In):** Registered users should be able to successfully go through the Log-In process. They should be able to log in using Username and Password.
    
4.  **Use Case 4 (Profile Management):** Upon successful Log-In, logged users should be able to navigate to their Profile page, edit their profile details, and view their Foods count. This involves the changing of profile picture inserted via URL, and editing of user data fields including First Name, Middle Name, Last Name, About, and About Food.
    
5.  **Use Case 5 (Food Creation):** Logged users should be able to navigate to the Add Food page, where they can create a new food with a Title, Description, and a Picture (URL). After the food creation process, users should be redirected to the Home page, where the newly created food should be present.
    
6.  **Use Case 6 (Food Management):** On the Home page, logged users should see all their foods listed. Each food should have options for View, Edit, and Delete. If no foods have been created yet, a "There are no foods :(" message should be displayed. Users also should have the option to search for foods, based on food titles.
    

## Testing Process

### Test Cases 

All test cases created for the Foody web application are documented in the 'Test Cases' directory of this repository. Each test case is designed to validate a specific functionality or use case described in the SRS document.

[Test Cases](https://github.com/SimeonSavov/FoodyWebApp_Testing/tree/main/TestCases)

### Bug Tracking

Any bugs or issues identified during the testing process are logged and tracked in the 'Bug Reports' directory of this repository. Each bug report includes detailed information about the issue, steps to reproduce it.

[Bug Reports](https://github.com/SimeonSavov/FoodyWebApp_Testing/tree/main/BugReports)

## API Testing with Postman

This section provides information about API testing of the Foody Web Application. It will guide you on how to interact with the Foody API using Postman.

### API Queries

The following API queries and endpoints are supported:

1. **User**
    - **POST /api/User/Create:** Create a new user by sending a JSON object in the request body with attributes like `"userName"`, `"firstName"`, `"midName"`, `"lastName"`, `"email"`, `"password"`, and `"rePassword"`.
    - **POST /api/User/Authentication:** Log in an existing user by sending a JSON object in the request body with `"userName"` and `"password"`. When a user logs in, the response format is a JSON object with an `"accessToken"` field, which is essential for all food requests.

2. **Food**
   All of the following requests require authorization.
    - **GET /api/Food/All:** List all foods (empty request body).
    - **GET /api/Food/Search:** Search for foods by their name using a query parameter like `?keyword=foodName`.
    - **POST /api/Food/Create:** Create a new food by sending a JSON object in the request body with attributes `"name"`, `"description"`, and `"url"`.
    - **PATCH /api/Food/Edit/foodId:** Change the title of an existing food using a JSON object with the path and value to replace.
    - **DELETE /api/Food/Delete/foodId:** Delete an existing food.

### Foody API Tasks: Postman Requests

Your task is to write API requests with Postman for certain RESTful API endpoints. You should organize your requests in a collection.
[API](https://github.com/SimeonSavov/FoodyWebApp_Testing/tree/main/API)

1. **Log in to the API**
    - Send a POST request with your username and password, created in the Foody Web App. After a successful request, you will receive your access token as part of the response body. Use this token as a Bearer Token in the Authorization section for the following requests.

2. **Create a New Food**
    - Send a POST request with attributes required for creating a new food. The JSON body should include `"name"`, `"description"`, and `"url"`. The URL attribute is not mandatory, meaning you can create a food only with a title and description. If you decide to use the URL attribute, ensure it points to a picture format or leave it blank.

3. **Search for the Food You Created**
    - Send a GET request to search for the food you just created by its title.

4. **Change the Title of the Food You Created**
    - Send a PATCH request with the attributes needed to replace the title of the food you created.

5. **Delete Food**
    - Send a DELETE request with the attributes required to delete the food you just patched.
