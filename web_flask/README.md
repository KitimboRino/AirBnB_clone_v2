0x04. AirBnB clone - Web framework

1. **What is a Web Framework?**
   - A web framework is a software framework designed to aid in the development of web applications by providing a structured way to build and organize code. It typically includes libraries, tools, and pre-written code that simplifies common tasks in web development, such as handling HTTP requests, managing sessions, and interacting with databases.

2. **How to build a web framework with Flask:**
   - Flask is a lightweight web framework for Python. To build a web application with Flask, you need to:
     - Install Flask using pip: `pip install Flask`
     - Create a Python script where you define your application and its routes using Flask's decorators.

3. **How to define routes in Flask:**
   - In Flask, routes are URL patterns that the application will respond to. You define routes using the `@app.route()` decorator, where you specify the URL path for which the associated function should be called.

4. **What is a route:**
   - A route is a mapping between a URL and a function in a web application. When a client makes a request to a specific URL, the associated function (view function) is executed to generate a response.

5. **How to handle variables in a route:**
   - Flask allows you to define dynamic routes by including variable parts in the URL. You can capture these variables in your view functions by specifying them in the route decorator's path. These variables can then be used as parameters in the corresponding view function.

6. **What is a template:**
   - A template is an HTML file with placeholders for dynamic content. Templates allow you to separate the presentation logic from the business logic in your web application, making it easier to manage and maintain your code.

7. **How to create an HTML response in Flask by using a template:**
   - Flask integrates with Jinja2, a powerful templating engine, to render HTML templates. You can render templates by using the `render_template()` function provided by Flask. This function takes the name of the template file as an argument and optionally any data you want to pass to the template.

8. **How to create a dynamic template (loops, conditions…):**
   - With Jinja2 templates in Flask, you can include loops, conditions, and other control structures to generate dynamic content. This allows you to iterate over lists, display conditional content, and perform other logic directly in your HTML templates.

9. **How to display in HTML data from a MySQL database:**
   - To display data from a MySQL database in an HTML template with Flask, you first need to establish a connection to the database using a library like `mysql-connector-python`. Once connected, you can execute SQL queries to fetch the data from the database and pass it to your template for rendering using the `render_template()` function. The data can then be accessed and displayed in the HTML template using Jinja2 syntax.

Examples:
- **Defining a route in Flask:**
  ```python
  @app.route('/')
  def index():
      return 'Hello, World!'
  ```

- **Handling variables in a route:**
  ```python
  @app.route('/user/<username>')
  def show_user_profile(username):
      return f'User: {username}'
  ```

- **Rendering a template in Flask:**
  ```python
  from flask import render_template

  @app.route('/hello/')
  @app.route('/hello/<name>')
  def hello(name=None):
      return render_template('hello.html', name=name)
  ```

- **Displaying data from a MySQL database in HTML:**
  ```python
  from flask_mysqldb import MySQL

  mysql = MySQL(app)

  @app.route('/users')
  def users():
      cur = mysql.connection.cursor()
      cur.execute('SELECT username FROM users')
      users = cur.fetchall()
      cur.close()
      return render_template('users.html', users=users)
  ```
  Here, `users.html` is an HTML template where `users` is a list of usernames retrieved from the database and passed to the template for rendering.