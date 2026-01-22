<!--
  howto.md
  A step-by-step guide to integrate MySQL with Syncfusion React Scheduler using Django 
-->

# How to integrate MySQL with Syncfusion React Scheduler using Django

This repository contains a sample full-stack application demonstrating how to synchronize events between MySQL database and the Syncfusion React Scheduler component using Django.The React frontend provides a responsive UI for viewing and managing  events.

## Prerequisites
- Node.js (>= 18.0)
- npm (>= 8.0)
- Python(>= 10.3.1)
- DJango(>= 6.0.1)
- MySQL(>= 8.0.41.0)
- React(>= 18.3)
- A MySQL Database with Username and Password (create at https://dev.mysql.com/downloads/installer/)
- Basic familiarity with React, Python and MySQL Query
- Make sure the ports nothing run on 8000 , 3000

## Project Structure
```
├── README.md                           # This guide
├── backend                             # backend configuration
│   ├── scheduler   
│   │    ├── _init_.py
│   │    ├── asgi.py
│   │    ├── settings.py                # Connect Database
│   │    ├── urls.py
│   │    ├── wsgi.py
│   ├── schedulerCrud  
│   │    ├── migrations
|   │    │    ├──  _init_.py 
│   │    ├── _init_.py
│   │    ├── admin.py
│   │    ├── apps.py
│   │    ├── models.py                 # Table Structure
│   │    ├── serializers
│   │    ├── tests.py
│   │    ├── urls.py
│   │    ├── views.py                  # Process Scheduler CRUD Request
│   ├── manage.py                      # Starting the server
├── public
│    ├── index.html
├── src
│    ├── App.css       
│    ├── App.test.tsx
│    ├── App.tsx                        # Scheduler Configuration
│    ├── index.css
│    ├── index.tsx
│    ├── logo.svg
│    ├── react-app-env.d.ts
│    ├── setupTests.ts  
├── package.json
│── tsconfig.json

```
## Setup


### Cloning the repository
    
- Clone the repository to your local machine

### Backend Setup

### Installation
- Run the following command to install the required packages
    ```
    pip install django-cors-headers
    pip install djangorestframework
    pip install pymysql
    pip install dj-database-url
    pip install mysqlclient
    ```
- Go to the backend directory 
### MySQL Configuration
- Create a MySQL user with a chosen username and password and create a new database`.
- In `backend/scheduler/settings.py` file update the USER, PASSWORD, and DB as per the database configuration.

    ```ini
    NAME=<Your-database-name>
    USER=<your-user-name>
    PASSWORD=<password-for-specific-user>
    ```
- We need to create table in the mysql database. Run the following command to create the table

    ```
   python manage.py makemigrations

   python manage.py migrate

   ```
### Available Endpoints
The Django server (`views.py`) exposes the following REST routes:
| Method | URL                          | Description                         |
| ------ | ---------------------------- | ----------------------------------- |
| GET    | `Home/GetData`    | List events in the given time range |
| POST   | `Home/UpdateData`                | Create a new ,edit and delete event. 

### Frontend Setup

### Installation

1. Open the project directory in terminal to install the required packages. 

    ```bash
    npm install
    ```
### Running the Application
1. Open a terminal and navigate to backend folder
      ```bash
    cd backend
    ```
2. Start the backend server:
    ```bash
    python manage.py runserver
    ```
3. Server started running on `http://localhost:8000`
4. Open another terminal and start the frontend:
    ```bash
    npm start
    ```
5. Navigate to [`http://localhost:3000`](http://localhost:3000) in your browser.

6. You can perform CRUD operation on the scheduler that will be reflected in the MySQL database table.
 

## Output Preview
![Frontend Preview](./Outputs/Frontend.png)
*Image illustrating the Syncfusion React Scheduler*

![Database Preview](./Outputs/Database.png)
*Image illustrating the events of Syncfusion React Scheduler in MYSQL*

## Troubleshooting
- **401 Unauthorized**: Check `NAME` `User` and `Password`.
- **CORS errors**: Ensure frontend calls runs on `localhost:3000`