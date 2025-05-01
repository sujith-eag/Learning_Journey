Overview of setting up a Flask application, using a package structure. 
Application setup, models, controllers, and configurations.

### Flask Application Structure

```
your_project/
│
├── application/
│   ├── __init__.py
│   ├── config.py
│   ├── controllers.py
│   ├── database.py
│   └── models.py
│
├── templates/
│   ├── articles.html
│   └── articles_by_author.html
│
├── static/
│   └── (static files like CSS, JS, images)
│
├── main.py
└── requirements.txt
```

### File Details

#### 1. `application/__init__.py`
This file can remain empty but is essential for Python to recognize this directory as a package.

#### 2. `application/config.py`
Configuration settings for different environments:
```python
import os

basedir = os.path.abspath(os.path.dirname(__file__))

class Config:
    DEBUG = False
    SQLITE_DB_DIR = None
    SQLALCHEMY_DATABASE_URI = None
    SQLALCHEMY_TRACK_MODIFICATIONS = False

class LocalDevelopmentConfig(Config):
    SQLITE_DB_DIR = os.path.join(basedir, "../db_directory")
    SQLALCHEMY_DATABASE_URI = "sqlite:///" + os.path.join(SQLITE_DB_DIR, "testdb.sqlite3")
    DEBUG = True
```
More Environments can be set up for production as required.
Password should not be included in code but read from `os.getenv()`

#### 3. `application/database.py`
Setting up the database using SQLAlchemy:
```python {title="databse.py"}
from sqlalchemy.ext.declarative import declarative_base
from flask_sqlalchemy import SQLAlchemy

engine = None
db = SQLAlchemy()
Base = declarative_base()
```

#### 4. `application/models.py`
Define your data models here:
```python
from application.database import db

class User(db.Model):
    __tablename__ = 'user'
    user_id = db.Column(db.Integer, autoincrement=True, primary_key=True)
    username = db.Column(db.String, unique=True)
    email = db.Column(db.String, unique=True)

class Article(db.Model):
    __tablename__ = 'article'
    article_id = db.Column(db.Integer, autoincrement=True, primary_key=True)
    title = db.Column(db.String)
    content = db.Column(db.Text)

class ArticleAuthors(db.Model):
    __tablename__ = 'article_authors'
    id = db.Column(db.Integer, autoincrement=True, primary_key=True)
    article_id = db.Column(db.Integer, db.ForeignKey('article.article_id'))
    user_id = db.Column(db.Integer, db.ForeignKey('user.user_id'))
```

#### 5. `application/controllers.py`
Handling routes and logic for views:
```python
from flask import render_template, request
from application import app
from application.models import Article

@app.route("/", methods=["GET", "POST"])
def articles():
    articles = Article.query.all()
    return render_template("articles.html", articles=articles)

@app.route("/articles_by/<user_name>", methods=["GET"])
def articles_by_author(user_name):
    articles = Article.query.filter(Article.authors.any(User.username == user_name)).all()
    return render_template("articles_by_author.html", articles=articles, username=user_name)
```

#### 6. `main.py`
The entry point for running the Flask application:
```python
import os
from flask import Flask
from application import config
from application.config import LocalDevelopmentConfig
from application.database import db


# def create_app():
#	app = Flask( __name__, template_folder = "templates")
#	if os.getenv('Env', "development") == "production":
#		raise Exception( "Currently no production config is setup." )
#	else:
#		print("Starting Local Development")
#		app.config.from_object(LocalDevelopmentConfig)  # reads configuration
#	db.init_app(app) # sets up the db
#	app.app_context().push()  # pushes the app into context
#	return app
	

def create_app():
    app = Flask(__name__, template_folder="templates")
    app.config.from_object(LocalDevelopmentConfig)
    db.init_app(app)
    
    with app.app_context():
        db.create_all()  # Create database tables
    return app

app = create_app()

# Import controllers after creating the app
from application.controllers import *

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
```

### Templates and Static Files
- **Templates** are stored in the `templates/` directory. Flask will automatically look here for HTML files.
- **Static files** (like CSS and JavaScript) should be placed in the `static/` directory and can be accessed in your templates.

### Notes
- Use environment variables for sensitive data (like passwords) by leveraging `os.getenv()`.
- Consider using Flask Blueprints for larger applications to better organize your routes and controllers.

### Running the Application
1. Install the required packages listed in `requirements.txt`.
2. Run `main.py` to start your Flask application.

This structure provides a clean separation of concerns, making your Flask application easier to maintain and expand as needed.