
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

### Install the required packages first: 
Open the Terminal
- On `Windows` type:
```Bash
python -m pip install -r requirements.txt
```
- On `MacOS` type:
```Bash
pip3 install -r requirements.txt
```
- On `Linux` type:
```Bash
pip install -r requirements.txt
```
This will install the packages from requirements.txt for this project.
- `requirements.txt`
```TXT
Bootstrap_Flask==2.2.0
Flask==2.3.2
Flask_WTF==1.1.1
WTForms==3.0.1
werkzeug==2.3.7
```

### `./templates/`

<details>
    <summary>templates</summary>

- `base.html`:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
      <title>{% block title %}{% endblock %}</title>
      <!--style>
          {% block styling %}
          body {
            background-color: purple;
          }
          {% endblock %}
      </style-->
      {% block styles %}
        {{ bootstrap.load_css() }}
      {% endblock %}
  </head>
  <body>
    {% block content %}{% endblock %}
  </body>
</html>
```
- `denied.html`:
```html
{% extends "base.html" %}
{% block title %}Access Denied{% endblock %}
<!--{% block styling %}
	{{ super() }}
	h1 {
		color: red;
	}
{% endblock %}-->
{% block content %}
	<div class="container">
		<h1>Access Denied </h1>
		<iframe src="https://giphy.com/embed/1xeVd1vr43nHO" width="480" height="271" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
		<p><a href="https://giphy.com/gifs/cheezburger-funny-dog-fails-1xeVd1vr43nHO">via GIPHY</a></p>
	</div>
{% endblock %}
```
- `index.html`:
```html
{% extends "base.html" %}
{% block title %}Secrets{% endblock %}
{% block content %}
    <div class="jumbotron">
      <div class="container">
        <h1>Welcome</h1>
        <p>Are you ready to discover my secret?</p>
        <a class="btn btn-primary btn-lg" href=" {{ url_for('login') }} ">Login</a>
      </div>
    </div>
{% endblock %}
```
- `login.html`:
```html
{% extends "base.html" %}
{% from 'bootstrap4/form.html' import render_form %}
{% block title %}Login{% endblock %}
{% block content %}
        <div class="container">
			<h1>Login</h1>
    	    <!-- This is where our form will go. -->
			<!--form action="{{ url_for('login') }}" method="post" novalidate>
				{{ form.csrf_token }}
				<p>
					{{ form.email.label }} <br/> {{ form.email(size=30) }}
					{% for err in form.email.errors %}
					<span style="color:red">{{ err }}</span>
					{% endfor %}
				</p>
				<p>
					{{ form.password.label }} <br/> {{ form.password(size=30) }}
					{% for err in form.password.errors %}
					<span style="color:red">{{ err }}</span>
					{% endfor %}
				</p>
				{{ form.submit }}
			</form-->
			{{ render_form(form) }}
        </div>
{% endblock %}
```
- `success.html`:
```html
{% extends "base.html" %}
{% block title %}Access Granted{% endblock %}
{% block content %}
	<div class="container">
		<h1>Top Secret </h1>
		<iframe src="https://giphy.com/embed/Ju7l5y9osyymQ" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
		<p><a href="https://giphy.com/gifs/rick-astley-Ju7l5y9osyymQ">via GIPHY</a></p>
	</div>
{% endblock %}
```

</details>

- `main.py`:
```python
from flask import Flask, render_template
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length #pip install email-validator
from flask_bootstrap import Bootstrap5 # pip install bootstrap-flask

OWN_EMAIL = "pal.daniel.79@gmail.com"
OWN_PASSWORD = "abc123"

class LoginForm(FlaskForm):
    email = StringField(label='Email', validators=[DataRequired()])
    password = PasswordField(label='Password', validators=[DataRequired()])
    submit = SubmitField(label="Log in")

app = Flask(__name__)
app.secret_key = "ezegynagyontitkoskulcsamitsenkisemtudkitalálni"
bootstrap = Bootstrap5(app) # bootstrap-flask inicializálása


@app.route("/")
def home():
    return render_template('index.html')

@app.route("/login", methods=["GET","POST"])
def login():
    login_form = LoginForm()
    if login_form.validate_on_submit():
        #print(login_form.email.data)
        if login_form.email.data == OWN_EMAIL and login_form.password.data == OWN_PASSWORD:
            return render_template("success.html")
        else:
            return render_template("denied.html")
    return render_template(
        "login.html",
        form=login_form
    )


if __name__ == '__main__':
    app.run(debug=True, port=5001)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---