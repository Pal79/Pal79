
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

# Coffee and wifi - wtf

> Install the required packages first: 
> - Open the Terminal
>
>    - On Windows type:
>    - python -m pip install -r requirements.txt
>
>    - On MacOS type:
>    - pip3 install -r requirements.txt
>
>    - On Linux type:
>    - pip install -r requirements.txt
>
> This will install the packages from requirements.txt for this project.

> requirements.txt:

```txt
Bootstrap_Flask==2.2.0
Flask==2.3.2
Flask_WTF==1.1.1
WTForms==3.0.1
werkzeug==2.3.7
```

<details>
    <summary>./static/css/</summary>

> styles.css:

```css
/* This CSS file will need to be added to the styling of 
your web pages for the styles to be rendered. */

body {
background-color: #333;
color: white;
}

a {
    color: #ffc107;
}

.jumbotron {
  display: flex;
  align-items: center;
  margin: 0;
  height: 100vh;
  color: white;
  background-color: #333;
}

.space-above {
    margin-top: 20px;
    padding-top: 20px;
}
```

</details>

<details>
    <summary>./templates</summary>

> add.html:

```html
{% extends 'base.html' %}
<!--Don't forget your import here-->
{% from 'bootstrap5/form.html' import render_form %}
{% block title %}Add A New Cafe{% endblock %}

{% block content %}
<div class="container">
  <div class="row">
    <div class="col-sm-12 col-md-8">

      <h1>Add a new cafe into the database</h1>

      <!-- This is where your WTForm will go -->
      {{ render_form(form, novalidate=True) }}

	  <p class="space-above"><a href="{{ url_for('cafes') }}">See all cafes</a></p>

    </div>
  </div>
</div>

{% endblock %}
```

> base.html:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no"/>

    {% block styles %}
    <!-- Load Bootstrap-Flask CSS here -->
    {{ bootstrap.load_css() }}

    <!-- Link to the styles.css here to apply styling to all the child templates.-->
    <link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}"/>

    {% endblock %}
    <title>{% block title %}{% endblock %}</title>
  </head>
  <body>
    {% block content %}{% endblock %}
  </body>
</html>
```

> cafes.html:

```html
{% extends 'base.html' %}
{% block title %}Restaurants{% endblock %}

{% block content %}

<div class="container">
  <div class="row">
    <div class="col-sm-12">

      <h1>All Cafes</h1>

	  <table class="table table-dark table-striped table-hover">
          <!-- This is where you will write the code to render a Bootstrap 
          Table that contains all the information from the 
          cafe-data.csv file. -->
          {% for list in cafes %}
          <tr>
              {% for item in list%}
              {% if item[0:4] == "http" %}
              <td><a href="{{ item }}">Maps Link</a></td>
              {% else %}
              <td>{{ item }}</td>
              {% endif %}
              {% endfor %}
          </tr>
          {% endfor %}
  	  </table>

      <p><a href="{{ url_for('home') }}">Return to index page</a></p>

    </div>
  </div>
</div>

{% endblock %}
```

> index.html:

```html
{% extends 'base.html' %}
{% block title %}Coffee and Wifi{% endblock %}

{% block content %}
<div class="jumbotron text-center">
    <div class="container">
  <h1 class="display-4">☕️ Coffee & Wifi 💻</h1>
  <p class="lead">Want to work in a cafe but need power and wifi?</p>
  <hr class="my-4">
  <p>You've found the right place! Checkout my collection of cafes with data on power socket availability, wifi speed and coffee quality.</p>
  <a class="btn btn-warning btn-lg" href="{{ url_for('cafes') }}" role="button">Show Me!</a>
</div>
    </div>

{% endblock %}
```

</details>

> cafe-data.csv:

```csv
Cafe Name,Location,Open,Close,Coffee,Wifi,Power
Lighthaus,https://goo.gl/maps/2EvhB4oq4gyUXKXx9,11AM, 3:30PM,☕☕☕☕️,💪💪,🔌🔌🔌
Esters,https://goo.gl/maps/13Tjc36HuPWLELaSA,8AM,3PM,☕☕☕☕,💪💪💪,🔌
Ginger & White,https://goo.gl/maps/DqMx2g5LiAqv3pJQ9,7:30AM,5:30PM,☕☕☕,✘,🔌
Mare Street Market,https://goo.gl/maps/ALR8iBiNN6tVfuAA8,8AM,1PM,☕☕,💪💪💪,🔌🔌🔌
```

> main.py:

```python
from flask import Flask, render_template, redirect, url_for
from flask_bootstrap import Bootstrap5
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField, SelectField
from wtforms.validators import DataRequired, URL
import csv

app = Flask(__name__)
app.config['SECRET_KEY'] = '8BYkEfBA6O6donzWlSihBXox7C0sKR6b'
Bootstrap5(app)


class CafeForm(FlaskForm):
    cafe = StringField(
        label='Cafe name',
        validators=[DataRequired()]
    )
    location = StringField(
        label="Cafe Location on Google Maps",
        validators=[
            DataRequired(),
            URL()]
    )
    open = StringField(
        label="Opening Time e.g.: 8AM",
        validators=[DataRequired()]
    )
    close = StringField(
        label="Closing Time e.g.: 6:30PM",
        validators=[DataRequired()]
    )
    coffee_rating = SelectField(
        label="Coffee rating",
        choices=[
            "☕️",
            "☕️☕️",
            "☕️☕️☕️",
            "☕️☕️☕️☕️",
            "☕️☕️☕️☕️☕️"
        ],
        validators=[DataRequired()]
    )
    wifi_rating = SelectField(
        label="Wifi Strength Rating",
        choices=[
            "✘",
            "💪",
            "💪💪",
            "💪💪💪",
            "💪💪💪💪",
            "💪💪💪💪💪"
        ],
        validators=[DataRequired()]
    )
    power_rating = SelectField(
        label="Power Strngth Rating",
        choices=[
            "✘",
            "🔌",
            "🔌🔌",
            "🔌🔌🔌",
            "🔌🔌🔌🔌",
            "🔌🔌🔌🔌🔌"
        ],
        validators=[DataRequired()]
    )
    submit = SubmitField('Submit')

# Exercise:
# add: Location URL, open time, closing time, coffee rating, wifi rating, power outlet rating fields
# make coffee/wifi/power a select element with choice of 0 to 5.
#e.g. You could use emojis ☕️/💪/✘/🔌
# make all fields required except submit
# use a validator to check that the URL field has a URL entered.
# ---------------------------------------------------------------------------


# all Flask routes below
@app.route("/")
def home():
    return render_template("index.html")


@app.route('/add', methods=["GET", "POST"])
def add_cafe():
    # Exercise:
    # Make the form write a new row into cafe-data.csv
    # with   if form.validate_on_submit()
    form = CafeForm()
    if form.validate_on_submit():
        with open("./cafe-data.csv", mode="a", encoding="utf-8") as file:
            file.write(f"\n{form.cafe.data},"
                       f"{form.location.data}"
                       f"{form.open.data},"
                       f"{form.close.data},"
                       f"{form.coffee_rating.data},"
                       f"{form.wifi_rating.data},"
                       f"{form.power_rating.data}")
        return redirect(url_for('cafes'))
    return render_template('add.html', form=form)


@app.route('/cafes')
def cafes():
    with open('cafe-data.csv', newline='', encoding='utf-8') as csv_file:
        csv_data = csv.reader(csv_file, delimiter=',')
        list_of_rows = []
        for row in csv_data:
            list_of_rows.append(row)
    return render_template('cafes.html', cafes=list_of_rows)


if __name__ == '__main__':
    app.run(debug=True)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---