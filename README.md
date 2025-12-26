# Ex.08 Design of Interactive Image Gallery
# Date:12/12/2025
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
views.py
from django.shortcuts import render

def gallery(request):
    return render(request, 'pic.html')
```
```
urls.py
from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.gallery, name='gallery'),
]
```
```
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Image Gallery</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #dfe2e3, #6dd5ed);
            padding: 30px;
            text-align: center;
        }

        h1 {
            margin-bottom: 25px;
        }

        
        #gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 18px;
            max-width: 1600px;
            margin: auto;
        }

        #gallery img {
            width: 450px;
            height: 230px;
            border-radius: 12px;
            box-shadow: 0 6px 14px rgba(27, 26, 26, 0.974);
            transition: transform 0.35s ease, box-shadow 0.35s ease;
            cursor: pointer;
            object-fit: cover;
        }

        #gallery img:hover {
            transform: scale(1.15);
            box-shadow: 0 10px 20px rgba(0,0,0,0.25);
        }

        #modal {
            width: 100%;
            height: 100%;
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.85);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 999;
        }

        #modal img {
             max-width: 100%;
             max-height: 100%;
             width: auto;
             height: auto;
             object-fit: contain;
             border-radius: 14px;
             box-shadow: 0 0 25px rgba(255, 255, 255, 0.25);
             display: block;
        }

        #modal span {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 32px;
            color: white;
            cursor: pointer;
        }
    </style>
</head>

<body>

<h1>hongkong diaries</h1>

<div id="gallery">
    <img src="{% static 'hongkong1.jpg' %}" alt="one">
    <img src="{% static 'hongkong2.jpg' %}" alt="two">
    <img src="{% static 'hongkong3.webp' %}" alt="three">
    <img src="{% static 'hongkong4.jpg' %}" alt="four">
    <img src="{% static 'honkong5.jpg' %}" alt="five">
    <img src="{% static 'honkong 6.jpg' %}" alt="six">
</div>

<div id="modal">
    <span id="close">&times;</span>
    <img id="modalImg" alt="preview">
</div>

<script>
    const gallery = document.getElementById("gallery");
    const modal = document.getElementById("modal");
    const modalImg = document.getElementById("modalImg");
    const closeBtn = document.getElementById("close");

    gallery.onclick = function (e) {
        if (e.target.tagName === "IMG") {
            modalImg.src = e.target.src;
            modal.style.display = "flex";
        }
    };

    closeBtn.onclick = function () {
        modal.style.display = "none";
    };

    modal.onclick = function (e) {
        if (e.target === modal) {
            modal.style.display = "none";
        }
    };
</script>
</body>
</html>
```

# OUTPUT:
![alt text](<Screenshot 2025-12-26 151459.png>)
![alt text](<Screenshot 2025-12-26 151739.png>)
# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
