<!--
  howto.md
  A step-by-step guide to integrate MySQL with Syncfusion React Scheduler using Django 
-->

# How to integrate MySQL with Syncfusion React Scheduler using Django

This repository contains a sample full-stack application demonstrating how to synchronize events between MySQL database and the Syncfusion React Scheduler component. While the React frontend provides a responsive UI for viewing and managing  events.

Syncfusion [React Scheduler](https://ej2.syncfusion.com/react/demos/#/material3/schedule/overview) CRUD Application with Django and MySQL database.

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
├── backend                             # Node.js backend
│   ├── scheduler   
│   │    ├── _init_.py
│   │    ├── asgi.py
│   │    ├── settings.py
│   │    ├── urls.py
│   │    ├── wsgi.py
│   ├── schedulerCrud  
│   │    ├── migrations
|   │    │    ├──  _init_.py 
│   │    ├── _init_.py
│   │    ├── admin.py
│   │    ├── apps.py
│   │    ├── models.py
│   │    ├── serializers
│   │    ├── tests.py
│   │    ├── urls.py
│   │    ├── views.py
│   ├── db.sqlite3
│   ├── manage.py                    
├── public
│    ├── index.html
├── src
│    ├── App.css       
│    ├── App.test.tsx
│    ├── App.tsx                        # Scheduler Integration
│    ├── index.css
│    ├── index.tsx
│    ├── logo.svg
│    ├── react-app-env.d.ts
│    ├── setupTests.ts  
├── package.json
│── tsconfig.json

```
## Backend Setup

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
### Start Backend Server
- Open `backend` folder in terminal and run `python manage.py runserver` command to start the backend server.

    ```
    python manage.py runserver
    ```
    Server is running on http://127.0.0.1:8000/
### Available Endpoints
The Django server (`views.py`) exposes the following REST routes:
| Method | URL                          | Description                         |
| ------ | ---------------------------- | ----------------------------------- |
| GET    | `Home/GetData`    | List events in the given time range |
| POST   | `Home/UpdateData`                | Create a new ,edit and delete event. 

## Frontend Setup

### Start Syncfusion React Scheduler 

- Open another terminal, on the root directory, run the following command to install the required packages
    ```
    npm install
    ```

### Running the Application
1. Navigate to backend folder
      ```bash
    cd backend
    ```
2. Start the backend server:
    ```bash
    python manage.py runserver
    ```
3. Server started running on `http://localhost:8000`
4. Start the frontend:
    ```bash
    npm start
    ```
5. Navigate to [`http://localhost:3000`](http://localhost:3000) in your browser.

6. You can perform CRUD operation on the scheduler that will be reflected in the MySQL database table.
 

## Output Preview
![Frontend Preview](./SampleOutputs/frontend.png)
*Image illustrating the Syncfusion React Scheduler*

![Database Preview](./SampleOutputs/database.png)
*Image illustrating the events of Syncfusion React Scheduler in MYSQL*

## Troubleshooting
- **401 Unauthorized**: Check `NAME` `User` and `Password`.
- **CORS errors**: Ensure frontend calls runs on `localhost:3000`