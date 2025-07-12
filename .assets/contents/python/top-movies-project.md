
---

- [Back to the first page](../../../README.md)
- [Back to the Python](../python.md)

---

# Top Movies project

### Install the required packages first: 
Open the Terminal
- On Windows type:
```Bash
python -m pip install -r requirements.txt
```
- On MacOS type:
```Bash
pip3 install -r requirements.txt
```
- On Linux type:
```Bash
pip install -r requirements.txt
```
This will install the packages from requirements.txt for this project.
- `./requirements.txt`
```TXT
Bootstrap_Flask==2.2.0
Flask==2.3.2
flask_sqlalchemy==3.0.5
Flask_WTF==1.1.1
Requests==2.31.0
WTForms==3.0.1
werkzeug==2.3.7
```

### `./templates/`

<details>
    <summary>Templates</summary>

- `add.html`
```html
{% extends 'base.html' %}

{% block title %}Add Movie{% endblock %}

{% block content %}
<div class="content">
    <h1 class="heading">Add a Movie</h1>
</div>
{% endblock %}
```
- `base.html`
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />

    {% block styles %}
    <!-- Load Bootstrap-Flask CSS here -->
    {{ bootstrap.load_css() }}
    <!-- Link to the styles.css here to apply styling to all the child templates.-->
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css?family=Nunito+Sans:300,400,700"
    />
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css?family=Poppins:300,400,700"
    />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.14.0/css/all.min.css"
      integrity="sha512-1PKOgIY59xJ8Co8+NE6FZ+LOAZKjy+KY8iq0G4B3CyeY6wYHN3yt9PW0XpSriVlkMXe40PTKnXrLnZ9+fkDaog=="
      crossorigin="anonymous"
    />
    <link
      rel="stylesheet"
      href="{{ url_for('static', filename='css/styles.css') }}"
    />
    {% endblock %}

    <title>{% block title %}{% endblock %}</title>
  </head>
  <body>
    {% block content %}{% endblock %}
  </body>
</html>
```
- `edit.html`
```html
{% extends 'base.html' %}

{% block title %}Edit Movies{% endblock %}

{% block content %}
<div class="content">
  <h1 class="heading">Movie Title</h1>
    <p class="description">Edit Movie Rating</p>
  </div>
{% endblock %}
```
- `index.html`
```html
{% extends 'base.html' %}

{% block title %}My Top 10 Movies{% endblock %}

{% block content %}
<div class="container">
  <h1 class="heading">My Top 10 Movies</h1>
  <p class="description">These are my all-time favourite movies.</p>
   
  <div class="card" >
    <div class="front" style="background-image: url('https://www.shortlist.com/media/images/2019/05/the-30-coolest-alternative-movie-posters-ever-2-1556670563-K61a-column-width-inline.jpg');">
        <p class="large">1</p>
    </div>
    <div class="back">
      <div>
    <div class="title">Drive <span class="release_date">(2011)</span></div>
        <div class="rating">
            <label>7.5</label>
          <i class="fas fa-star star"></i>
        </div>
          <p class="review">"Loved it!"</p>
        <p class="overview">
            A mysterious Hollywood stuntman and mechanic moonlights as a getaway driver and finds himself in trouble when he helps out his neighbor in this action drama.
        </p>

        <a href="#" class="button">Update</a>
        <a href="#" class="button delete-button">Delete</a>

      </div>
    </div>
  </div>
</div>
<div class="container text-center add">
<a href="#" class="button">Add Movie</a>
</div>

{% endblock %}
```
- `select.html`
```html
{% extends 'base.html' %}

{% block title %}Select Movie{% endblock %}

{% block content %}
<div class="container">
    <h1 class="heading">Select Movie</h1>
  <p>
    <a href="#"> MOVIE TITLE - MOVIE RELEASE DATE</a>
  </p>

</div>
{% endblock %}
```

</details>

### `./static/css/`

<details>
    <summary>styles.css</summary>

```css
*, *:before, *:after {
	 box-sizing: border-box;
}
 html {
	 font-size: 18px;
	 line-height: 1.5;
	 font-weight: 300;
	 color: #333;
	 font-family: "Nunito Sans", sans-serif;
}
 body {
	 margin: 0;
	 padding: 0;
	 height: 100vh;
	 background-color: #ecf0f9;
	 background-attachment: fixed;
}
.large {
     font-size: 3rem;
}
 .content {
	 display: flex;
	 margin: 0 auto;
	 justify-content: center;
	 align-items: center;
	 flex-wrap: wrap;
	 max-width: 1500px;
}
 p.overview {
	 font-size: 12px;
	 height: 200px;
	 width: 100%;
	 overflow: hidden;
	 text-overflow: ellipsis;
}
 .heading {
	 width: 100%;
	 margin-left: 1rem;
	 font-weight: 900;
	 font-size: 1.618rem;
	 text-transform: uppercase;
	 letter-spacing: 0.1ch;
	 line-height: 1;
	 padding-bottom: 0.5em;
	 margin-bottom: 1rem;
	 position: relative;
}
 .heading:after {
	 display: block;
	 content: '';
	 position: absolute;
	 width: 60px;
	 height: 4px;
	 background: linear-gradient(135deg, #1a9be6, #1a57e6);
	 bottom: 0;
}
 .description {
	 width: 100%;
	 margin-top: 0;
	 margin-left: 1rem;
	 margin-bottom: 3rem;
}
 .card {
	 color: inherit;
	 cursor: pointer;
	 width: calc(33% - 3rem);
	 min-width: calc(33% - 3rem);
	 height: 400px;
	 min-height: 400px;
	 perspective: 1000px;
	 margin: 1rem auto;
	 position: relative;
}
 @media screen and (max-width: 800px) {
	 .card {
		 width: calc(50% - 3rem);
	}
}
 @media screen and (max-width: 500px) {
	 .card {
		 width: 100%;
	}
}
 .front, .back {
	 display: flex;
	 border-radius: 6px;
	 background-position: center;
	 background-size: cover;
	 text-align: center;
	 justify-content: center;
	 align-items: center;
	 position: absolute;
	 height: 100%;
	 width: 100%;
	 -webkit-backface-visibility: hidden;
	 backface-visibility: hidden;
	 transform-style: preserve-3d;
	 transition: ease-in-out 600ms;
}
 .front {
	 background-size: cover;
	 padding: 2rem;
	 font-size: 1.618rem;
	 font-weight: 600;
	 color: #fff;
	 overflow: hidden;
	 font-family: Poppins, sans-serif;
}
 .front:before {
	 position: absolute;
	 display: block;
	 content: '';
	 top: 0;
	 left: 0;
	 right: 0;
	 bottom: 0;
	 background: linear-gradient(135deg, #1a9be6, #1a57e6);
	 opacity: 0.25;
	 z-index: -1;
}
 .card:hover .front {
	 transform: rotateY(180deg);
}
 .card:nth-child(even):hover .front {
	 transform: rotateY(-180deg);
}
 .back {
	 background: #fff;
	 transform: rotateY(-180deg);
	 padding: 0 2em;
}
 .card:hover .back {
	 transform: rotateY(0deg);
}
 .card:nth-child(even) .back {
	 transform: rotateY(180deg);
}
 .card:nth-child(even):hover .back {
	 transform: rotateY(0deg);
}
 .button {
	 transform: translateZ(40px);
	 cursor: pointer;
	 -webkit-backface-visibility: hidden;
	 backface-visibility: hidden;
	 font-weight: bold;
	 color: #fff;
	 padding: 0.5em 1em;
	 border-radius: 100px;
	 font: inherit;
	 background: linear-gradient(135deg, #1a9be6, #1a57e6);
	 border: none;
	 position: relative;
	 transform-style: preserve-3d;
	 transition: 300ms ease;
}
 .button:before {
	 transition: 300ms ease;
	 position: absolute;
	 display: block;
	 content: '';
	 transform: translateZ(-40px);
	 -webkit-backface-visibility: hidden;
	 backface-visibility: hidden;
	 height: calc(100% - 20px);
	 width: calc(100% - 20px);
	 border-radius: 100px;
	 left: 10px;
	 top: 16px;
	 box-shadow: 0 0 10px 10px rgba(26, 87, 230, 0.25);
	 background-color: rgba(26, 87, 230, 0.25);
}

.button.delete-button {
	 background-color: rgba(230, 87, 230, 0.25);
	 background: linear-gradient(135deg, #e61a46, #e61a1a);
}
.button.delete-button:before {
	 background-color: rgba(230, 87, 230, 0.25);
	 box-shadow: 0 0 10px 10px rgba(230, 87, 230, 0.25);
}
 .button:hover {
	 transform: translateZ(55px);
}
 .button:hover:before {
	 transform: translateZ(-55px);
}
 .button:active {
	 transform: translateZ(20px);
}
 .button:active:before {
	 transform: translateZ(-20px);
	 top: 12px;
	 top: 12px;
}
.container.add {
    margin-top: 40px;
    margin-bottom: 20px;
}
.rating {
    color: #E4BB23;
}
.review {
    font-style: italic;
}
 .movie_gens {
	 font-size: 11.5px;
}
 .title {
	 font-weight: bold;
}
 .release_date {
	 font-weight: normal;
}
```

</details>

- `./instance/`[movies.db](./top_movies_project/movies.db)
- `./main.py`
```python
from flask import Flask, render_template, redirect, url_for, request
from flask_bootstrap import Bootstrap5
from flask_sqlalchemy import SQLAlchemy
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField
from wtforms.validators import DataRequired
import requests

app = Flask(__name__)
app.config['SECRET_KEY'] = 'SECRET_KEY'
Bootstrap5(app)

app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///movies.db"
db = SQLAlchemy()
db.init_app(app)

class Movies(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(250), unique=True, nullable=False)
    year = db.Column(db.Integer, nullable=False)
    description = db.Column(db.String(500), nullable=False)
    rating = db.Column(db.Float, nullable=False)
    ranking = db.Column(db.Integer, nullable=False)
    review = db.Column(db.String(250), nullable=False)
    img_url = db.Column(db.String(250), nullable=False)

with app.app_context():
    db.create_all()

@app.route("/")
def home():
    return render_template("index.html")


if __name__ == '__main__':
    app.run(debug=True)
```

---

- [Back to the first page](../../../README.md)
- [Back to the Python](../python.md)

---