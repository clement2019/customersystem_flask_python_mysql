# customersystem_flask_python_mysql
Customer Management System with Python, Flask and MySQL
n this project, we will explain how to develop User Management System with Python, Flask and MySQL.

User section is an important part of any web application in which users are created, updated, deleted, viewed etc. We can easily develop user managment system in Python


So let’s proceed to develop User Management System with Python, Flask and MySQL.


Application Setup
We will create application directory customersystem_flask_python_mysql using below command.


$ mkdir customersystem_flask_python_mysql 


Then moved the folder intonits directory
$ cd customersystem_flask_python_mysql 



Modules Required
We will use folloing modules in this application from Python.



Flask: It is a micro framework from Python to create web application. So we will install this module to create web applications. We will install it using the below command:


$ pip install Flask


Create MySQL Database and Table
We will create MySQL database user-system and create tableuser to store users details.


we will create Flask app and assign app.config vaues for MySQL database connection to access database.


from flask import Flask, render_template, request, redirect, url_for, session

from flask_mysqldb import MySQL

import MySQLdb.cursors

import re  


app = Flask(__name__) 


app.secret_key = 'xyzsdfg'

  
app.config['MYSQL_HOST'] = 'localhost'

app.config['MYSQL_USER'] = 'root'

app.config['MYSQL_PASSWORD'] = ''

app.config['MYSQL_DB'] = 'user-system'

  
mysql = MySQL(app)  


@app.route('/')


if __name__ == "__main__":

    app.run()


    Implement User Login Section

We will create template file templates/login.html and create FORM with input and submit button.


<form action="{{ url_for('login') }}" method="post">
	{% if mesage is defined and mesage %}

		<div class="alert alert-warning">{{ mesage }}</div>
	{% endif %}
	<div class="form-group">

		<label for="email">Email:</label>

		<input type="email" class="form-control" id="email" name="email" placeholder="Enter email" name="email">
	</div>

	<div class="form-group">

		<label for="pwd">Password:</label>
		<input type="password" class="form-control" id="password" name="password" placeholder="Enter password" name="pswd">
	</div>   

	<button type="submit" class="btn btn-primary">Login</button>

</form>

Then we will create function login() in app.py file and call function render_template() to render login.html file to load user login page. We will implement login functionality by executing SQL query to perform user login


We will implement new user add using form submit post values. We will insert users details into user table.




Implement User Listing

We will create templates/users.html template file and create HTML to display user list. Then implement to loop through user data and display list with details.



Implement User Edit Section
We will create template file templates/edit.html and create user edit form.


<form action="{{ url_for('edit') }}" method="post">
	{% if mesage is defined and mesage %}

		<div class="alert alert-warning">{{ mesage }}</div>
	{% endif %}
	<div class="form-group">

		<label for="name">Name:</label>

		<input type="text" class="form-control" id="name" name="name" value="{{ editUser.name }}">
	</div>

	<div class="form-group">
		<label for="role">Role:</label>

		<select class="form-control" id="role" name="role">
			<option value="admin" {% if editUser.role == 'admin' %}selected{% endif %}>Admin</option>


            Implement User Password Change
We will create template file templates/password_change.html and create password change form to implement functionality.



We will create edit() function in app.py and implement user edit functionality and render edit.html template.

We will create a function password_change() in app.py and implement user password change functionality.



Implement View User Details
We will create templates/view.html file and implement to display user details.

<h3>User Details</h3> 

<br>

<h4>{{user.name}}</h4>


<p><strong>Email: </strong> {{user.email}}. </p>


<p><strong>Role: </strong> {{user.role}} </p>


<p><strong>Skills: </strong> {{user.country}}</p>



We will create function view() in app.py and implement to get user details from database table and pass to template view.html 

to display user details.