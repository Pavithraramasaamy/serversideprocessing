# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Clone the respiratory from Github


### Step 2:
Create Django Admin project.


### Step 3:
Create a New App.


### Step 4:
Create python program for views and urls


### Step 5:
Create a HTML file of forms


### Step 6:

Publish the website in the given URL.

## PROGRAM :
```
server.html

<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Rectangle</title>
<meta name='viewport' content='width=device-width,initial-scales=1'>
<style>
body {
background-color: cyan;
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed lime;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color: purple;
}
.formelt{
color: red;
text-align: center;
margin-top: 5px;
margin-bottom: 5px;
}
h1{
color: yellow;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Area of a Rectangle</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Length : <input type="text" name="length" value="{{l}}"></input>(in m)<br/>
<div clss="formelt">
Breadth : <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
</div>
<div class="formelt">
<input type="submit" value="calculate"></input><br/>
</div>
<div class="formelt">
Area :  <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>

views.py
from django.shortcuts import render
def rectarea(request):
    context={}
    context['area']="0"
    context['l']="0"
    context['b']="0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/server.html',context) 

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```




## OUTPUT:
![OUTPUT](./out.png)
![out](https://user-images.githubusercontent.com/118596964/212574180-2a0748be-d792-4c17-be2e-42d73725eeec.png)
/home/sec/Pictures/Screenshots/out.png
### Home Page:
![HomePage](./home.png)
![home](https://user-images.githubusercontent.com/118596964/212574153-b260b9be-b47a-41c5-a65d-9cdfcf009823.png)

## Result:

The program for implementing server side processing is completed successfully

