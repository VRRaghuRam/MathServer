# Ex.05 Design a Website for Server Side Processing
## Date:02/12/2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```

math.html

<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>POWER</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-image:linear-gradient(to left,rgb(110, 213, 101),rgb(188, 78, 78));
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    width: 500px;
    min-height: 300px;
    font-size: 10px;
    border-radius: 10px;
    background-image: linear-gradient(to right,#C33764,#1D2671);
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
.inten{
    font-size: 20px;
    font-style: oblique;
    font-weight: bold;
}
.resistance{
    font-size: 20px;
    font-style: oblique;
    font-weight: bold;
}
#inten{
    border-radius: 8px;
    margin-left: 30px;
    text-align: center;


}
#resistance{
    border-radius: 8px;
    margin-right: 10px;
    margin-top: 20px;
    text-align: center;


}
#formlet{
    border-radius: 8px;
    margin-left: 30px;
    text-align: center;
}
.formelt
{
    font-size: 20px;
    font-style: oblique;
    font-weight: bold;
    margin-top: 20px;
    margin-right: 5px;
}
h1 {
    color:white;
    padding-top: 15px;
}
#cal{
    cursor: pointer;
    border: none;
    border-radius: 5px;
    height: 30px;
    width: 80px;
    font-size: medium;
    color: white;
    margin-top: 20PX;
    margin-left: 5px;
    background-color:royalblue;
}

</style>
</head>
<body>
    <center>
    <h2><b>RAGHU RAM .V.R (24900512)</b></h2>
</center>
<div class="edge">
    <div class="box">
        <h1 >POWER CALCULATOR</h1>
        
        <form method="POST">
            {% csrf_token %}
            <div class="inten">
                Intensity: <input type="text" name="intensity" value="{{I}}" id="inten"> Amperes (A)<br/>
            </div>
            <div class="resistance">
                Resistance: <input type="text" id="resistance" name="resistance" value="{{R}}"> Ohm (Ω)<br/>
            </div>
            <div class="formelt">
                Power: <input type="text" id="formlet" name="power" value="{{power}}"> In Watts<br/>
            </div>
            <div class="cal">
                <input type="submit" id="cal"><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>

views.py

from django.shortcuts import render 
def power(request): 
    context={} 
    context['power'] = "0" 
    context['R'] = "0" 
    context['I'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        R = request.POST.get('resistance','0')
        I = request.POST.get('intensity','0')
        print('request=',request) 
        print('resistance=',R) 
        print('intensity=',I) 
        power = int(R) *int(I)* int(I) 
        context['power'] = power
        context['R'] = R
        context['I'] = I
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('power/',views.power,name="calculatepower"),
    path('',views.power,name="calculatepower")
]




```

## SERVER SIDE PROCESSING:

![alt text](<Screenshot (27).png>)

## HOMEPAGE:

![alt text](<Screenshot (28).png>)

## RESULT:
The program for performing server side processing is completed successfully.
