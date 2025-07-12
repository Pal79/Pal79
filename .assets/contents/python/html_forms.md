
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

# Html Forms
### `./templates/`

<details>
    <summary>Templates</summary>

- `index.html`:
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>HTML FORMS</title>
    </head>
    <body>
        <form action="{{ url_for('receive_data') }}" method="post">
            <label for="username">Username: </label>
            <input type="text" name="username" placeholder="username"/>
            <label for="password">Password: </label>
            <input type="text" name="password" placeholder="password"/>
            <input type="submit" name="submit" value="Ok"/>
        </form>
    </body>
</html>
```

</details>

- `main.py`:
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/")
def home():
    return render_template("index.html")

@app.route("/login", methods=["GET", "POST"])
def receive_data():
    username = request.form["username"]
    password = request.form["password"]
    return f"<h3>Username: {username}, Password: {password}</h3>"

if __name__ == "__main__":
    app.run(debug=True)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---