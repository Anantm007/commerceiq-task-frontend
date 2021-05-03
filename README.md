# commerceiq-task-frontend

#### Deployed Application:

https://commerceiq-task-frontend.vercel.app/

## About the Project

This repository contains code for a minimal chat window application made using Vue.js (https://vuejs.org/) to recieve user's messages and display all back along with the timestamps. This project is made as a part of SDE internship assesment at Commerce IQ. The technologies used here are Vue.js and Bootstrap 4 (for styling).

## Project setup

```
1. Clone the repo
2. cd commerceiq-task-frontend
3. npm install
4. npm run serve
5. Open the project on localhost:8080
```

## Features of the Application

1. As soon as the app loads, we make a request to the backend to fetch all the existing "messages" from the DB, and show them from the admin side.

2. A custom welcome message is displayed at the top.

3. The rest of the messages are displayed in sequential order along with the timestamps.

4. There is an option to add a new message.

5. After the user inputs the message, we make some checks and send it the server to add the message into the DB.

6. When we get back a successful response, we display all the messages (including this new one) from the admin side again.

7. The same message is also displayed from the user's side also.

8. The code has been neatly diivided into components for scalability and readability.

## Technology Stack

- Vue.js v3.0.0
- Bootstrap 4.4.1 (for styling)

#### Dependencies

- vue: The frontend framework

#### Backend API (made with Node and express):

- Code: https://github.com/Anantm007/commerceIq-task

- README: https://github.com/Anantm007/commerceIq-task/blob/master/README.md

- Sample_Requests_Collection: https://documenter.getpostman.com/view/7916291/TzJvcbbK
