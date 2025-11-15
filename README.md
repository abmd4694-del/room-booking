# Django Multi-Page Portfolio Website

This project is a multi-page Django website based on a modern responsive HTML template.  
It includes:

- Home Page  
- Portfolio Page  
- About Us Page  
- Contact Section  
- Fully integrated static files (CSS, JS, Images, Videos)  
- Reusable Navbar with Django `{% include %}`  
- Organized project structure  
- Working Django URL routing  

---

## 🚀 Features

### ✔ Fully Responsive Template  
Converted from a premium HTML theme into Django templates.

### ✔ Multiple Pages  
- `Home`  
- `Portfolio`  
- `About Us`

### ✔ Django Static Integration  
All CSS, JS, images, and videos are served using:

{% load static %}
{% static 'path/to/file' %}

yaml
Copy code

### ✔ Organized Code  
- Clean HTML templates  
- Reusable `navbar.html`  
- Consolidated static folder  
- Easy to scale with new pages

---

## 📁 Project Structure

myproject/
│── myapp/
│ │── templates/
│ │ │── index.html
│ │ │── portfolio.html
│ │ │── about.html
│ │ │── navbar.html
│ │
│ │── urls.py
│ │── views.py
│
│── static/
│ │── css/
│ │── js/
│ │── img/
│ │── videos/
│ │── slick/
│ │── font-awesome-4.7.0/
│
│── myproject/urls.py
│── manage.py
│── README.md

yaml
Copy code

---

## ⚙️ Installation

### 1️⃣ Clone the repository

```bash
git clone <your-repo-url>
cd <project-folder>
2️⃣ Create Virtual Environment
bash
Copy code
python -m venv venv
Activate it:

Windows:

bash
Copy code
venv\Scripts\activate
Mac/Linux:

bash
Copy code
source venv/bin/activate
3️⃣ Install Dependencies
bash
Copy code
pip install django
4️⃣ Run Migrations
bash
Copy code
python manage.py migrate
5️⃣ Start Development Server
bash
Copy code
python manage.py runserver
Open:

cpp
Copy code
http://127.0.0.1:8000/
🧭 URL Routing Setup
myapp/urls.py
python
Copy code
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='home'),
    path('portfolio/', views.portfolio, name='portfolio'),
    path('about/', views.about, name='about'),
]
views.py
python
Copy code
from django.shortcuts import render

def index(request):
    return render(request, "index.html")

def portfolio(request):
    return render(request, "portfolio.html")

def about(request):
    return render(request, "about.html")
project/urls.py
python
Copy code
from django.urls import path, include
from django.contrib import admin

urlpatterns = [
    path('', include('myapp.urls')),
    path('admin/', admin.site.urls),
]
🖼 Static Files
Make sure your static folder is structured like:

css
Copy code
static/
    ├── css/
    ├── js/
    ├── img/
    ├── videos/
    ├── slick/
    └── font-awesome-4.7.0/
Enable static in settings.py:

python
Copy code
STATIC_URL = '/static/'
STATICFILES_DIRS = [ BASE_DIR / "static" ]
📄 Templates
Navbar Include
All templates import the navbar:

html
Copy code
{% include 'navbar.html' %}
✨ Future Enhancements
Contact form backend processing

Admin panel editable portfolio

Database-driven blog posts

User authentication

Dark mode toggle

🤝 Contributing
Pull requests are welcome!
Please open an issue first to discuss changes.

📝 License
This project is based on Tooplate free template and is allowed for personal & commercial use.

👨‍💻 Author
Created by Abhiram (Your Name)
Feel free to modify and customize the project.
