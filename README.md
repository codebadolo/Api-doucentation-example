# API Documentation

This documentation provides an overview of the available API endpoints, HTTP methods, required fields, and example `curl` commands for interacting with the API.


Here is a simplified section for the **"How to Run the Project"** part of your `README.md`:

```markdown
# How to Run the Project

Follow these steps to set up and run the Django project locally.

### Prerequisites

- Python 3.x
- Django
- PostgreSQL (or another database)
- pip (Python package installer)
- A virtual environment (recommended)

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/yourproject.git
cd yourproject
```

### 2. Create and Activate a Virtual Environment

It's recommended to use a virtual environment to manage dependencies.

For Windows:
```bash
python -m venv env
env\Scripts\activate
```

For Linux/Mac:
```bash
python3 -m venv env
source env/bin/activate
```

### 3. Install Dependencies

Install all necessary dependencies from the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### 4. Configure the Database

1. Open the `settings.py` file in your Django project.
2. Update the `DATABASES` setting to configure your database (e.g., PostgreSQL):

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

3. Create the database in PostgreSQL:
```bash
psql -U your_db_user -c "CREATE DATABASE your_db_name;"
```

### 5. Apply Migrations

Run the following commands to apply database migrations:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create a Superuser

To create an admin user, run the following command and follow the prompts:

```bash
python manage.py createsuperuser
```

### 7. Run the Development Server

Start the Django development server:

```bash
python manage.py runserver
```

Now, open your browser and go to `http://127.0.0.1:8000/` to view the project.
```

This section includes all the steps necessary to run the project locally, covering environment setup, dependency installation, database configuration, and running the development server.

---

## **1. Register a User**
- **URL**: `/register/`
- **HTTP Method**: `POST`
- **Description**: Register a new user with the required fields.
- **Required Fields**:
  - `username`: string
  - `password`: string
  - `email`: string (optional)
  
- **cURL Example**:
  ```bash
  curl -X POST "http://127.0.0.1:8000/register/" \
  -H "Content-Type: application/json" \
  -d '{"username": "newuser", "password": "password123", "email": "user@example.com"}'


---

## **2. Change User Password**
- **URL**: `/change-password/`
- **HTTP Method**: `PUT`
- **Description**: Update the authenticated user's password.
- **Required Fields**:
  - `old_password`: string
  - `new_password`: string
  
- **cURL Example**:
  ```bash
  curl -X PUT "http://127.0.0.1:8000/change-password/" \
  -H "Authorization: Bearer <your_token>" \
  -H "Content-Type: application/json" \
  -d '{"old_password": "oldpassword123", "new_password": "newpassword123"}'
  ```

---

## **3. Update User Profile**
- **URL**: `/update-user/`
- **HTTP Method**: `PUT`
- **Description**: Update the authenticated user's profile information.
- **Required Fields**:
  - `phone_number`: string (optional)
  - `address`: string (optional)
  - `city`: string (optional)

- **cURL Example**:
  ```bash
  curl -X PUT "http://127.0.0.1:8000/update-user/" \
  -H "Authorization: Bearer <your_token>" \
  -H "Content-Type: application/json" \
  -d '{"phone_number": "123456789", "address": "123 Main St", "city": "Sample City"}'
  ```

---

## **4. Logout User**
- **URL**: `/logout/`
- **HTTP Method**: `POST`
- **Description**: Log out the user and blacklist the refresh token.
- **Required Fields**:
  - `refresh_token`: string
  
- **cURL Example**:
  ```bash
  curl -X POST "http://127.0.0.1:8000/logout/" \
  -H "Authorization: Bearer <your_token>" \
  -H "Content-Type: application/json" \
  -d '{"refresh_token": "<your_refresh_token>"}'
  ```

---

## **5. Get JWT Token**
- **URL**: `/token/`
- **HTTP Method**: `POST`
- **Description**: Obtain an access token and refresh token by providing username and password.
- **Required Fields**:
  - `username`: string
  - `password`: string
  
- **cURL Example**:
  ```bash
  curl -X POST "http://127.0.0.1:8000/token/" \
  -H "Content-Type: application/json" \
  -d '{"username": "newuser", "password": "password123"}'
  ```

---

## **6. Refresh JWT Token**
- **URL**: `/token/refresh/`
- **HTTP Method**: `POST`
- **Description**: Refresh the access token using the refresh token.
- **Required Fields**:
  - `refresh`: string (your refresh token)
  
- **cURL Example**:
  ```bash
  curl -X POST "http://127.0.0.1:8000/token/refresh/" \
  -H "Content-Type: application/json" \
  -d '{"refresh": "<your_refresh_token>"}'
  ```

---

## **7. Get List of Users**
- **URL**: `/users/`
- **HTTP Method**: `GET`
- **Description**: Retrieve a list of all users. Requires authentication.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/users/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## **8. Get User Details**
- **URL**: `/users/<id>/`
- **HTTP Method**: `GET`
- **Description**: Retrieve details of a specific user by ID. Requires authentication.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/users/1/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## **9. Get List of Accounts**
- **URL**: `/accounts/`
- **HTTP Method**: `GET`
- **Description**: Retrieve a list of all accounts. Requires authentication.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/accounts/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## **10. Get Account Details**
- **URL**: `/accounts/<id>/`
- **HTTP Method**: `GET`
- **Description**: Retrieve details of a specific account by ID. Requires authentication.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/accounts/1/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## **11. Get List of Shops**
- **URL**: `/shops/`
- **HTTP Method**: `GET`
- **Description**: Retrieve a list of all shops for the authenticated user.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/shops/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## **12. Get Shop Details**
- **URL**: `/shops/<id>/`
- **HTTP Method**: `GET`
- **Description**: Retrieve details of a specific shop by ID.
  
- **cURL Example**:
  ```bash
  curl -X GET "http://127.0.0.1:8000/shops/1/" \
  -H "Authorization: Bearer <your_token>"
  ```

---

## Notes:
- All authenticated requests require a valid JWT token in the `Authorization` header.
- Replace `<your_token>` and `<your_refresh_token>` with the actual token strings.
- Adjust the URLs based on your server environment (e.g., `http://127.0.0.1:8000/`).
```

### How to Use

1. **Create a `README.md` file** in the root directory of your project.
2. **Update the placeholder values** (`<your_token>`, `<your_refresh_token>`, `<id>`) with actual values when interacting with the API.
3. **Deploy the API** and replace `http://127.0.0.1:8000/` with the actual base URL of your API.

This documentation now covers all your remaining API endpoints with `curl` examples and descriptions, ready to be added to your project.
