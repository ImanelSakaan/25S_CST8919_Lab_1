

# CST8919 Lab 1: Flask + Auth0 Authentication

A Python web application built with Flask that integrates Auth0 for secure user authentication. This project demonstrates implementing login/logout functionality and protecting routes with authentication.

---
🎥 Demo Video

YouTube Demo Link - 5 Minute Walkthrough
https://youtu.be/TN4TDb8YhuI

## 🚀 Features

- **User Authentication**: Secure login/logout using Auth0  
- **Protected Routes**: Pages that require authentication to access  
- **Session Management**: Maintains user sessions securely  
- **Responsive UI**: Bootstrap-styled interface  
- **User Profile Display**: Shows authenticated user information  

---

## 🛠️ Technologies Used

- **Flask**: Python web framework  
- **Auth0**: Authentication and authorization platform  
- **Authlib**: OAuth client library  
- **Bootstrap**: Frontend styling  
- **python-dotenv**: Environment variable management  

---

## 📋 Prerequisites

- Python 3.7+
- Git
- Auth0 account (free)

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/ImanelSakaan/25S_CST8919_Lab_1.git
cd 25S_CST8919_Lab_1
```

### 2. Create Virtual Environment

```bash
# Create a virtual environment
python -m venv venv

```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Configure Auth0

### 1. Create Auth0 Account

Go to [auth0.com](https://auth0.com) and sign up.

### 2. Create Application

- Go to **Applications → Create Application**
- Choose **"Regular Web Applications"**
- Select **Python** as the technology

### 3. Configure Application Settings

- **Allowed Callback URLs**: `http://localhost:5000/callback`  
- **Allowed Logout URLs**: `http://localhost:5000`  
- Save settings.

### 4. Get Credentials

Note the following:

- **Domain** (e.g., `dev-8yrl8ckvj10hkhyi.us.auth0.com')
- **Client ID** (e.g., `kvJjzumMo1aOpy4UKmWpcwRW91ebOyBF')
- **Client Secret** (e.g., `SGwjdJWFmUXzPvGS_qPt6w9MKXp7-pZtyGAykw8QTnWA0mCARf6UiOf41b9Sgf6t')

---

## 5. Environment Configuration

### 1. Copy the environment template

```bash
cp .env.example .env
```

### 2. Edit `.env` with your credentials

```env
# Auth0 Configuration
AUTH0_CLIENT_ID=kvJjzumMo1aOpy4UKmWpcwRW91ebOyBF
AUTH0_CLIENT_SECRET=SGwjdJWFmUXzPvGS_qPt6w9MKXp7-pZtyGAykw8QTnWA0mCARf6UiOf41b9Sgf6t
AUTH0_DOMAIN=dev-8yrl8ckvj10hkhyi.us.auth0.com

# Flask Configuration (generate a random secret key)
APP_SECRET_KEY=your_random_secret_key_here
```

---

## 6. Run the Application

```bash
python app.py
```

Access the app at: [http://localhost:5000](http://localhost:5000)

---

## 🔗 Application Routes

- `/` – Home page (public)
- `/login` – Initiates Auth0 login flow
- `/logout` – Logs out user and clears session
- `/callback` – Auth0 callback URL (handles authentication response)
- `/protected` – Protected page (requires authentication)

---

## 🔐 How Authentication Works

1. **Identity Provider (IdP)**: Auth0 handles user authentication  
2. **Service Provider (SP)**: Your Flask app requests authentication  
3. **Flow**:
   - User clicks **Login** → Redirected to Auth0
   - User enters credentials on Auth0
   - Auth0 validates and returns to app with token
   - App stores user session and grants access

---

## 📁 Project Structure

```
25S_CST8919_Lab_1/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── .env.example           # Environment variables template
├── .env                   # Your actual environment variables (not in git)
├── templates/
│   ├── base.html          # Base template
│   ├── home.html          # Home page
│   └── protected.html     # Protected page
└── README.md              # This file
```

---

## 🧪 Testing the Application

1. Start the app: `python app.py`  
2. Visit: [http://localhost:5000](http://localhost:3000)  
3. Click **Login with Auth0**  
4. Try accessing `/protected` before and after login  
5. Click **Logout** to clear session

---

## 🚨 Troubleshooting

### Common Issues

- **Import Error**: Make sure virtual environment is activated  
- **Auth0 Callback Error**: Verify callback URL in Auth0 dashboard  
- **Environment Variables**: Check `.env` has correct values  
- **Port 3000 Busy**: Change port in `app.py` if needed  

**Debug Mode:**  
The app runs in debug mode by default. Check console for error messages.

---

## 📚 What I Learned

- **OAuth 2.0 Flow**: Understanding how authentication delegation works  
- **Flask Session Management**: Storing and managing user sessions  
- **Route Protection**: Using decorators to protect sensitive routes  
- **Auth0 Integration**: Setting up external identity provider  
- **Security Best Practices**: Environment variables and session security  

---

## 👨‍💻 Development Notes

- **Session Data**: User information is stored in Flask sessions  
- **Protection Decorator**: `@requires_auth` ensures authentication  
- **Environment Security**: Sensitive data kept in `.env`  
- **Error Handling**: Graceful handling of authentication failures  

---

## ✅ Assignment Requirements Completed

- [x] Follow Auth0 Quickstart tutorial  
- [x] Implement login/logout functionality  
- [x] Create protected `/protected` route  
- [x] Redirect unauthenticated users to login  
- [x] Create comprehensive `README.md`  
- [x] Include setup and run instructions  
- [x] Document environment variables  
- [x] Create YouTube demo video  
- [x] Initialize Git repository with meaningful commits  
- [x] Push to public GitHub repository  

---

## 🎬 Demo Video Content

The 5-minute YouTube demo covers:

1. **App Overview**: What the application does  
2. **Login Flow**: Demonstrating Auth0 authentication  
3. **Protected Routes**: Testing access control  
4. **Code Walkthrough**: Key components and learnings  
5. **Security Features**: How authentication is implemented  

---

**Author:** *[Iman]*  
**Course:** CST8919  
**Assignment:** Lab 1 – Flask + Auth0 Authentication  
**Date:** May 2025







# CST8919 Lab 1: Implementing User Login with Flask and Auth0


## Objective

In this lab, you will build a Python web application using Flask and integrate it with **Auth0** for secure authentication.

You will follow the official Auth0 Quickstart guide:
🔗 [Auth0 Python Web App Quickstart](https://auth0.com/docs/quickstart/webapp/python#configure-auth0)

By the end of this assignment, you should have a Flask app that supports login and logout via Auth0, with additional customization.

---
## About Auth0, Identity Provider & Service Provider

### What is Auth0?

**Auth0** is an **authentication and authorization platform** that helps developers add secure login, logout, and identity management features to applications with minimal effort. Instead of building user authentication from scratch, you can use Auth0 to handle login flows, tokens, and user profiles securely.

### Identity Provider (IdP)

An **Identity Provider (IdP)** is the system that verifies user identities. Examples include:
- Auth0
- Google
- Facebook
- Microsoft Entra ID

The IdP is responsible for:
- Handling login screens
- Verifying credentials
- Returning identity information to the app (like name, email, etc.)

### Service Provider (SP) / Relying Party (RP)

A **Service Provider (SP)** or **Relying Party (RP)** is the application or service that the user is trying to access — in this case, **your Flask web app**.

The SP:
- Redirects users to the IdP (Auth0) for login
- Receives authentication tokens from the IdP
- Grants or denies access based on login status

In this lab, **your Flask app is the Service Provider** and **Auth0 acts as the Identity Provider / Relying Party (RP)**.

---

## Tasks

### 1. Follow the Tutorial

- Complete the steps from **"Configure Auth0"** to the end of the Auth0 Quickstart tutorial.
- Ensure the app runs locally and that users can successfully log in and log out.

### 2. Customize the App

Make the following additions to the base tutorial:

- Add a new route `/protected` for a **"Protected Page"** that only authenticated users can access.
- If a user tries to access `/protected` while not logged in, redirect them to the login page.

### 3. Documentation

Include a `README.md` with:

- Instructions for setting up the app, including how to configure Auth0.
- Commands to install dependencies and run the app locally.
- Example `.env` file or instructions for setting environment variables.
- **A link to a 5-minute YouTube video demo** showing:
  - How your app works (login, protected page)
  - A brief explanation of your code and what you learned

### 4. GitHub Repository

- Initialize a Git repository for your project.
- Make **frequent commits** with meaningful commit messages.
- Push your code to a **public GitHub repository**.
- Include the **YouTube demo link in the README.md**.

---

## Submission Instructions

Submit your **GitHub repository link** via Brightspace.

**Deadline**: Wednesday, 28 May 2025

---

## Tips

- Test your app before submitting — especially login, logout, and protected routes.
- Practice your demo before recording to stay within the 5-minute limit.
- Refer to the Auth0 documentation or ask for help if you get stuck.


