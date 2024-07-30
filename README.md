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
    {
        "id": 1,
        "projects": [],
        "client_name": "Saurabh",
        "created_at": "2024-07-29T06:30:06.008410Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 2,
        "projects": [
            {
                "id": 1,
                "project_name": "nimap_task1",
                "created_at": "2024-07-29T06:33:29.318109Z",
                "client": 2,
                "created_by": 1,
                "users": [
                    1
                ]
            }
        ],
        "client_name": "Tushar",
        "created_at": "2024-07-29T06:32:44.815565Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 3,
        "projects": [],
        "client_name": "Abhi",
        "created_at": "2024-07-29T10:46:12.434892Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 4,
        "projects": [
            {
                "id": 2,
                "project_name": "SMS",
                "created_at": "2024-07-29T12:38:49.839894Z",
                "client": 4,
                "created_by": 1,
                "users": [
                    1
                ]
            }
        ],
        "client_name": "Shubham",
        "created_at": "2024-07-29T10:46:31.368522Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 5,
        "projects": [
            {
                "id": 3,
                "project_name": "Python car game",
                "created_at": "2024-07-29T17:15:48.729328Z",
                "client": 5,
                "created_by": 2,
                "users": [
                    2
                ]
            }
        ],
        "client_name": "Yugal",
        "created_at": "2024-07-29T10:46:42.717151Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 6,
        "projects": [],
        "client_name": "Omkar",
        "created_at": "2024-07-29T10:47:03.638351Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 7,
        "projects": [],
        "client_name": "Yash",
        "created_at": "2024-07-29T10:47:24.877659Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    },
    {
        "id": 8,
        "projects": [],
        "client_name": "Aditya",
        "created_at": "2024-07-29T12:38:15.589046Z",
        "updated_at": "2024-07-30T04:18:29.433861Z",
        "created_by": 1
    }

        ```



## 📝 Created by Saurabh Madrap
