# Ex.05 Design a Website for Server Side Processing
# Date:12-04-2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```

math.html

<!DOCTYPE html>
<html>
<head>
  <title>Power Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 400px;
      margin: 50px auto;
      padding: 20px;
      border: 2px solid #ddd;
      border-radius: 10px;
      background-color: #f9f9f9;
    }
    h2 {
      text-align: center;
    }
    label, input, button {
      display: block;
      width: 100%;
      margin-top: 10px;
    }
    #result {
      margin-top: 20px;
      font-weight: bold;
      text-align: center;
    }
  </style>
</head>
<body>

  <h2 align="center">Power Calculator</h2>

  <form action="{% url 'home' %}" method="post">
    {% csrf_token %}

    Intensity:
    <input type="text" name="intensity_input"><br>

    Resistance:
    <input type="text" name="resistance_input"><br>

    <button type="submit"> Calculate</button>
    <p align="center"> The Power is : {{ output }}</p>


  </form>

</body>
</html>


views.py

from django.shortcuts import render

def power(request):
    if request.method == 'POST':
        intensity_value=int(request.POST.get('intensity_input'))
        resistance_value=int(request.POST.get('resistance_input'))
        power=(intensity_value**2)*resistance_value
        return render(request,'mathapp/math.html',{'output':power})
    return render(request,'mathapp/math.html')

 urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views


urlpatterns = [
    #path('admin/', admin.site.urls),
    path('',views.power,name='home'),
]  

```
# SERVER SIDE PROCESSING:


![Screenshot 2025-04-12 210453](https://github.com/user-attachments/assets/52e60b73-5ac6-4723-9ae4-477638181535)

# HOMEPAGE:

![Screenshot 2025-04-12 210507](https://github.com/user-attachments/assets/5a4d4704-3901-4764-8d96-137b13820a01)


# RESULT:
The program for performing server side processing is completed successfully.
