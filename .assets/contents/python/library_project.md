
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

# Library Project

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

> requirements.txt

```txt
Flask==2.3.2
flask_sqlalchemy==3.0.5
```

> ./instance/books.db
>
> ![books.db](./library_project/books.db)

> ./books-collection.db
>
> ![books collection.db](./library_project/books-collection.db)

<details>
    <summary>./templates</summary>

> add.html:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Add Book</title>
  </head>
  <body>
    <form action="{{ url_for('add') }}" method="POST">
      <label>Book Name</label>
      <input name="title" type="text" />
      <label>Book Author</label>
      <input name="author" type="text" />
      <label>Rating</label>
      <input name="rating" type="text" />
      <button type="submit">Add Book</button>
    </form>
  </body>
</html>
```

> edit_rating.html:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Edit Rating</title>
    </head>
    <body>
    <form action="{{ url_for('edit') }}" method="POST">
        <p>Book Name: {{ book.title }}</p>
        <p>Current Rating: {{ book.rating }}</p>
        <input hidden="hidden" name="id" value="{{ book.id }}"/>
        <input name="rating" type="text" placeholder="New Rating"/>
        <button type="submit">Change Rating</button>
    </form>
    </body>
</html>
```

> index.html:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Library</title>
  </head>
  <body>
    <h1>My Library</h1>
    {% if books == []: %}
    <p>Library is empty</p>
    {% endif %}
    <ul>
      {% for book in books %}
      <li>
        <a href="{{ url_for('delete', id=book.id) }}">Delete</a>
        {{ book.title }} - {{ book.author }} - {{ book.rating }}/10
        <a href="{{ url_for('edit', id=book.id) }}">Edit</a>
      </li>
      {% endfor %}
    </ul>

    <a href="{{ url_for('add') }}">Add New Book</a>
  </body>
</html>
```

</details>

> main.py

```python
from flask import Flask, render_template, request, redirect, url_for
import sqlite3
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)

app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///books.db"
db = SQLAlchemy()
db.init_app(app)

class Book(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(250), unique=True, nullable=False)
    author = db.Column(db.String(250), nullable=False)
    rating = db.Column(db.Float, nullable=False)

with app.app_context():
    db.create_all()

@app.route('/')
def home():
    result = db.session.execute(db.select(Book).order_by(Book.title))
    all_books = result.scalars()
    return render_template("index.html", books=all_books)

@app.route("/add", methods=["GET", "POST"])
def add():
    if request.method == "POST":
        new_book = Book(
            title=request.form["title"],
            author=request.form["author"],
            rating=request.form["rating"]
        )
        db.session.add(new_book)
        db.session.commit()
        return redirect(url_for("home"))
    return render_template("add.html")

@app.route("/edit", methods=["GET", "POST"])
def edit():
    if request.method == "POST":
        book_id = request.form["id"]
        book_to_update = db.get_or_404(Book, book_id)
        book_to_update.rating = request.form["rating"]
        db.session.commit()
        return redirect(url_for("home"))
    book_id = request.args.get("id")
    book_selected = db.get_or_404(Book, book_id)
    return render_template("edit_rating.html", book=book_selected)

@app.route("/delete")
def delete():
    book_id = request.args.get("id")

    book_to_delete = db.get_or_404(Book, book_id)
    db.session.delete(book_to_delete)
    db.session.commit()
    return redirect(url_for("home"))

if __name__ == "__main__":
    app.run(debug=True)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---