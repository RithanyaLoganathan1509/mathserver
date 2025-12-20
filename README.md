# Ex.04 Design a Website for Server Side Processing
# Date:28.11.2025
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
urls.py:

    from django.contrib import admin
    from django.urls import path
    from papp import views



    urlpatterns = [
        path('admin/', admin.site.urls),
        path('',views.power,name='power'),
    ]
```
```
views.py:

    from django.shortcuts import render
    def power(request):
        power=''
        if request.method == "POST":
            intensity = float(request.POST.get("intensity"))
            resistance = float(request.POST.get("resistance"))
            power=intensity**2*resistance
            print(f"Intensity: {intensity}, Resistance: {resistance},Power:{power:.2f}")
        return render(request, 'power.html', {'power': power})
```
```
power.html:

    {% load static %}
    <html>
        <head>
            <title>Power Calculation</title>
            <style>
                .yo{
                    margin-right:auto;
                    margin-left: auto;
                    margin-top:10%;
                    border-radius: 15px;
                    align-content: center;
                    background: rgba(245, 252, 248, 0.1);
                    border: 1px solid rgba(246, 240, 240, 0.2);
                    backdrop-filter: blur(8px);
                    box-shadow: 0px 0px 9px rgba(9, 2, 2, 0.942);
                    border-radius: 20px;
                    padding: 40px;
                    padding-bottom:50px;
                    padding-top:20px;
                    width: 400px; 
                }
                body{
                    text-align: center;
                    background-image: url("{% static 'exp5_img1.jpg' %}");
                    background-repeat: no-repeat;
                    background-size: cover;
                    background-position: center;
                }
                h1{
                    font-size: 45px;
                    color:antiquewhite;
                }
                label{
                    font-size: 26px;
                    color:antiquewhite;
                }
                button{
                    border-radius:5px;
                    font-size:15px;
                    padding:5px;
                    box-shadow: 0px 0px 5px black;
                    background: rgba(255, 255, 255, 0.1);
                    border: 1px solid rgba(255, 255, 255, 0.2);
                    backdrop-filter: blur(8px);
                    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
                    color:antiquewhite;
                }
                button:active{
                    background: rgba(92, 89, 89, 0.255);
                }
                pre{
                    display: inline;
                    font-size: 20px;
                    color:antiquewhite;
                    font-family: 'Times New Roman', Times, serif;
                }

            </style>
        </head>
        <body>
        
            <div class="yo">
            <h1>Power Calculator</h1><br>
            <form method = "POST">
                {% csrf_token %}
                <label>Intensity: 
                    <input type="text" name="intensity" required placeholder="Enter in cd"><br><br>
                </label>
                <label>Resistance:
                    <input type="text" name="resistance" required placeholder="Enter in Ohms"><br><br>
                </label>
                <button type="submit">
                    Calculate 
                </button> <br><br>
                <label>
                    Power: 
                </label>
                <input type="text" value={{power}}> <pre> Watts </pre>
            </form>
            </div> 
        </body> 
    </html>
```
# SERVER SIDE PROCESSING:
![alt text](<exp5/papp/static/Screenshot 2025-12-03 165112.png>)
# HOMEPAGE:
![alt text](<exp5/papp/static/Screenshot 2025-12-03 183027.png>)
# RESULT:
The program for performing server side processing is completed successfully.
