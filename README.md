# Ex.05 Design a Website for Server Side Processing
# Date: 27/10/2024
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
calculate.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
</head>
<body>
    <h1>Lamp Filament Power Calculator</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Calculate Power</button>
    </form>

    {% if power is not None %}
        <h2>Calculated Power: {{ power }} Watts</h2>
    {% endif %}
</body>
</html>

views.py
from django.shortcuts import render
from .forms import PowerCalculationForm

def calculate_power(request):
    power = None
    if request.method == 'POST':
        form = PowerCalculationForm(request.POST)
        if form.is_valid():
            intensity = form.cleaned_data['intensity']
            resistance = form.cleaned_data['resistance']
            power = intensity ** 2 * resistance  # P = I^2 * R
    else:
        form = PowerCalculationForm()

    return render(request, 'calculate.html', {'form': form, 'power': power})

urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('', views.calculate_power, name='calculate_power'),
]

```
# SERVER SIDE PROCESSING:
![ssp ph](https://github.com/user-attachments/assets/238261d9-a4cd-40ff-8226-b83194cb754d)


# HOMEPAGE
![Screenshot 2024-12-06 121519](https://github.com/user-attachments/assets/aad60fc5-c82a-4e75-834a-d06ae8bf05e0)


# RESULT:
The program for performing server side processing is completed successfully.
