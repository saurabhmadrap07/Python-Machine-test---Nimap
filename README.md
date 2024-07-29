# 🛠️ Python-Machine-test---Nimap Task

## 📜 Overview

This Django-based web application helps manage clients and projects. The system revolves around three main entities:

1. **👤 User**: Represents system users who can be assigned to projects.
2. **🏢 Client**: Represents clients for whom projects are managed.
3. **📁 Project**: Represents projects associated with clients and assigned to users.

## 🚀 Setup

### 🔧 Prerequisites

- Python 3.12 or above
- Django 5.0.7
- MySQL
- Postman (for testing APIs)

### 🛠️ Installation

1. **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2. **Create and activate a virtual environment:**

    ```bash
    python -m venv venv
    venv\Scripts\activate  # On Windows
    source venv/bin/activate  # On macOS/Linux
    ```

3. **Install the required packages:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Configure the database settings:**

    Ensure the database settings in `nimap_task/settings.py` are correct. Update the `DATABASES` section with your MySQL configuration.

5. **Apply migrations:**

    ```bash
    python manage.py migrate
    ```

6. **Create a superuser:**

    ```bash
    python manage.py createsuperuser
    ```

7. **Run the development server:**

    ```bash
    python manage.py runserver
    ```

## 🌐 API Endpoints

### 🔑 Authentication

To interact with the API, you need to authenticate using JWT. Obtain a token by sending a POST request to `/api/token/` with the following body:

```json
{
    "username": "<your_username>",
    "password": "<your_password>"
}
```

The response will include an `access` token that you can use to access other API endpoints.

### 🏢 Clients

- **List all clients**

    - **GET** `/api/clients/`

    - **Response:**

        ```json
        [
            {
                "id": 1,
                "client_name": "Nimap",
                "created_at": "2019-12-24T11:03:55.931739+05:30",
                "created_by": "Rohit"
            },
            {
                "id": 2,
                "client_name": "Infotech",
                "created_at": "2019-12-24T11:03:55.931739+05:30",
                "created_by": "Rohit"
            }
        ]
        ```

- **Create a new client**

    - **POST** `/api/clients/`
    - **Body:**

        ```json
        {
            "client_name": "<client_name>"
        }
        ```

    - **Response:**

        ```json
        {
            "id": 3,
            "client_name": "company A",
            "created_at": "2019-12-24T11:03:55.931739+05:30",
            "created_by": "Rohit"
        }
        ```

- **Retrieve client information along with projects**

    - **GET** `/api/clients/<id>/`

    - **Response:**

        ```json
        {
            "id": 2,
            "client_name": "Infotech",
            "projects": [
                {
                    "id": 1,
                    "name": "project A"
                }
            ],
            "created_at": "2019-12-24T11:03:55.931739+05:30",
            "created_by": "Rohit",
            "updated_at": "2019-12-24T11:03:55.931739+05:30"
        }
        ```

- **Update client information**

    - **PUT/PATCH** `/api/clients/<id>/`
    - **Body:**

        ```json
        {
            "client_name": "<new_client_name>"
        }
        ```

    - **Response:**

        ```json
        {
            "id": 3,
            "client_name": "company A",
            "created_at": "2019-12-24T11:03:55.931739+05:30",
            "created_by": "Rohit",
            "updated_at": "2019-12-24T11:03:55.931739+05:30"
        }
        ```

- **Delete a client**

    - **DELETE** `/api/clients/<id>/`
    - **Response Status:** `204 No Content`

### 📁 Projects

- **Create a new project**

    - **POST** `/api/clients/<client_id>/projects/`
    - **Body:**

        ```json
        {
            "project_name": "<project_name>",
            "users": [
                {
                    "id": "<user_id>",
                    "name": "<user_name>"
                }
            ]
        }
        ```

    - **Response:**

        ```json
        {
            "id": 3,
            "project_name": "Project A",
            "client": "Nimap",
            "users": [
                {
                    "id": 1,
                    "name": "Rohit"
                }
            ],
            "created_at": "2019-12-24T11:03:55.931739+05:30",
            "created_by": "Ganesh"
        }
        ```

- **List all projects assigned to the logged-in user**

    - **GET** `/api/projects/`

    - **Response:**

        ```json
        [
            {
                "id": 1,
                "project_name": "Project A",
                "created_at": "2019-12-24T11:03:55.931739+05:30",
                "created_by": "Ganesh"
            }
        ]
        ```

## 📝 Created by Saurabh Madrap
