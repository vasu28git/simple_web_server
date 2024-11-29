# EX01 Developing a Simple Webserver

# Date:
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
views.py
~~~

from importlib.resources import contents
from django.shortcuts import render

from http.server import BaseHTTPRequestHandler, HTTPServer

content='''
<html>
<head>
    <style> 
       
table.specs-table {
  width: 60%; 
  margin: 40px auto;
  border-collapse: collapse; 
  font-family: 'Roboto', sans-serif; 
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); 
  border-radius: 10px; 
  overflow: hidden; 
}


table.specs-table th {
  background-color: 
  color: #fff;
  padding: 14px 20px;
  text-align: left;
  font-size: 16px;
  font-weight: 600;
  letter-spacing: 0.5px; 
  text-transform: uppercase; 
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}


table.specs-table td {
  padding: 12px 20px; 
  text-align: left;
  border-bottom: 2px solid #f2f2f2; 
  font-size: 14px;
  color: #333; 
  transition: background-color 0.3s ease; 
}


table.specs-table tr:nth-child(even) {
  background-color: #f9fafb; 
}


table.specs-table tr:hover {
  background-color: #e7efff;
}


table.specs-table td:hover {
  background-color: #e1e7f1; 
}

/* Styling the last row */
table.specs-table tr:last-child td {
  border-bottom: none; /* Removes the border from the last row */
}

/* Responsive design for mobile */
@media screen and (max-width: 600px) {
  table.specs-table {
    width: 90%; /* Full width on smaller screens */
    margin: 20px auto; /* Less margin for smaller screens */
  }

  table.specs-table th, 
  table.specs-table td {
    font-size: 13px; /* Slightly smaller text for smaller screens */
    padding: 10px; /* Reduced padding on mobile */
  }
}

    </style>
</head>
<body>

    <table class="specs-table">
        <thead>
            <tr>
                <th colspan="2" style="text-align: center;">Laptop Specs</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Device name</td>
                <td>DESKTOP-MOHHBTU</td>
            </tr>
            <tr>
                <td>Processor</td>
                <td>13th Gen Intel(R) Core(TM) i5-1335U   1.30 GHz</td>
            </tr>
            <tr>
                <td>Installed RAM</td>
                <td>16.0 GB (15.7 GB usable)</td>
            </tr>
            <tr>
                <td>System type</td>
                <td>64-bit operating system, x64-based processor</td>
            </tr>
            <tr>
                <td>Pen and touch</td>
                <td>No pen or touch input is available for this display</td>
            </tr>
        </tbody>
    </table>

</body>
</html>
</html>
'''




class myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received....")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode()) 
print("This is my webserver!")
server_address = ('',8000)
httpd=HTTPServer(server_address,myserver)
httpd.serve_forever()
~~~
urls.py
~~~
from django.contrib import admin
from django.urls import include, path
from app import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('app/', include('app.urls')),
    path('lapspecs/',include('app.urls')),
]

~~~

# OUTPUT:
![server_response_specs](https://github.com/user-attachments/assets/3c702844-cd65-4b94-9f6a-94d18199838c)

![myserver_specs](https://github.com/user-attachments/assets/56378532-f491-4536-ac0e-af6a3cd2af83)



# RESULT:
The program for implementing simple webserver is executed successfully.
