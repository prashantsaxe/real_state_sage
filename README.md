Real Estate Sage
Real Estate Sage is a full-stack web application designed to facilitate property listings, user management, and property enquiries for a real estate platform. The backend is built with Django and Django REST Framework, while the frontend is developed using React with Redux for state management. The application is containerized using Docker and includes a comprehensive setup for development and production environments.
Table of Contents

Features
Technologies
Project Structure
Setup Instructions
Running the Application
Testing
Environment Variables
Contributing
License

Features

User authentication and profile management
Property listing, searching, and filtering
Enquiry system for properties
Rating system for properties
Admin panel for managing users, properties, and enquiries
Responsive frontend with React and Redux
RESTful API with Django REST Framework
Containerized setup with Docker and Docker Compose
Celery for asynchronous task processing
Nginx as a reverse proxy for production

Technologies

Backend: Python, Django, Django REST Framework, Celery, PostgreSQL
Frontend: React, Redux, JavaScript, Tailwind CSS
DevOps: Docker, Docker Compose, Nginx
Testing: Pytest, Factory Boy
Others: Redis (for Celery), Gunicorn (for WSGI)

Project Structure
prashantsaxe-real_state_sage/
├── README.md               # Project documentation
├── conftest.py             # Pytest configuration
├── docker-compose.yml      # Docker Compose configuration
├── Makefile                # Automation scripts
├── manage.py               # Django management script
├── pyproject.toml          # Python project configuration
├── pytest.ini              # Pytest settings
├── requirements.txt        # Python dependencies
├── setup.cfg               # Setup configuration
├── .dockerignore           # Docker ignore file
├── .env.example            # Example environment variables
├── apps/                   # Django apps
│   ├── common/             # Shared utilities
│   ├── enquiries/          # Property enquiry management
│   ├── profiles/           # User profile management
│   ├── properties/         # Property listing and management
│   ├── ratings/            # Property rating system
│   └── users/              # User authentication and management
├── client/                 # React frontend
│   ├── public/             # Static assets
│   ├── src/                # React source code
│   │   ├── app/            # Redux store
│   │   ├── components/     # Reusable components
│   │   ├── features/       # Feature-based slices (auth, properties)
│   │   ├── images/         # Image assets
│   │   └── pages/          # Page components
│   └── docker/             # Frontend Docker configuration
├── docker/                 # Backend Docker configuration
│   ├── local/              # Local development Docker files
│   │   ├── django/         # Django Dockerfile and scripts
│   │   └── nginx/          # Nginx configuration
├── real_estate/            # Django project settings
│   └── settings/           # Environment-specific settings
├── sample_images/          # Sample images for properties
└── tests/                  # Test suites
    ├── profiles/           # Profile tests
    └── users/              # User tests

Setup Instructions
Prerequisites

Docker and Docker Compose
Node.js (for local frontend development)
Python 3.8+ (for local backend development)
Make (optional, for using Makefile)

Steps

Clone the repository:
git clone https://github.com/prashantsaxe/real_state_sage.git
cd prashantsaxe-real_state_sage


Copy the environment file:
cp .env.example .env

Update the .env file with your configuration (e.g., database credentials, secret keys).

Install frontend dependencies (optional, for local development):
cd client
npm install
cd ..


Build and start Docker containers:
docker-compose up --build


Apply Django migrations:
docker-compose exec django python manage.py migrate


Create a superuser (optional, for admin access):
docker-compose exec django python manage.py createsuperuser



Running the Application

Development:
docker-compose up


Backend: http://localhost:8000
Frontend: http://localhost:3000
Admin Panel: http://localhost:8000/admin
Celery Flower: http://localhost:5555 (for monitoring tasks)


Production:Update docker-compose.yml to use production settings and run:
docker-compose -f docker-compose.yml up --build



Testing
Run tests using Pytest:
docker-compose exec django pytest

Or, for local development:
pip install -r requirements.txt
pytest

Environment Variables
The .env.example file lists required environment variables, including:

DJANGO_SECRET_KEY: Django secret key
DATABASE_URL: PostgreSQL connection string
REDIS_URL: Redis connection string
ALLOWED_HOSTS: Comma-separated list of allowed hosts
DEBUG: Set to True for development, False for production

Contributing

Fork the repository.
Create a feature branch (git checkout -b feature/YourFeature).
Commit your changes (git commit -m 'Add YourFeature').
Push to the branch (git push origin feature/YourFeature).
Open a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

