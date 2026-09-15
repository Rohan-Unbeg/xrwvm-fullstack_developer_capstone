# xrwvm-fullstack_developer_capstone

## Best Cars Dealership: Full Stack Developer Capstone

Best Cars Dealership is a national car retailer in the United States. This project is its web application, where visitors can browse dealership branches across the country, filter them by state, read customer reviews of each dealer, and, after signing up and logging in, post their own reviews.

### Architecture

- **Django app** (`server/`): user registration, login and logout, car makes and models stored in SQLite, the admin site, and the proxy views that the frontend calls
- **React frontend** (`server/frontend/`): dealers list, dealer details with reviews, post review, login and sign-up pages
- **Dealership and review database service** (`server/database/`): Node.js and Express API backed by MongoDB, run with Docker
- **Sentiment analyzer** (`server/djangoapp/microservices/`): Flask service using NLTK VADER, deployed on IBM Cloud Code Engine
- **CI/CD**: GitHub Actions lints the Python and JavaScript code on every push

### Running locally

```
# database service (MongoDB + Express)
cd server/database
docker build . -t nodeapp
docker compose up -d

# sentiment analyzer
cd ../djangoapp/microservices
docker build . -t sentianalyzer
docker run -d -p 5050:5000 sentianalyzer

# React frontend
cd ../../frontend
npm install
npm run build

# Django
cd ..
pip install -r requirements.txt
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py runserver
```
