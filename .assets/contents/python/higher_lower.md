
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

> # How to run on Ubuntu
>
> enter app dir and create .venv:
>
> ```shell
> python3 -m venv .venv
> ```
>
> activate .venv:
>
> ```shell
> source .venv/bin/activate
> ```
>
> install flask:
>
> ```shell
> pip install flask
> ```
>
> run app:
>
> ```shell
> python3 server.py
> ```
>
> open web browser and run this:
>
> ```shell
> 127.0.0.1:5001
> ```
>
> stop app run:
>
> ```shell
> Ctrl+C
> ```
>
> exit the venv:
>
> ```shell
> deactivate
> ```

> server.py:

```python
from flask import Flask
import random

app = Flask(__name__)
pic_width = 200

@app.route('/')
def home():
    return f"<h1>Guess a number between 0 and 9</h1><br><img src=\"https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif\" width=\"{pic_width}\">"

r = random.randint(0,9)

@app.route("/<int:number>")
def guess_number(number):
    if number < r:
        return f"<h2 color=\"red\">Too low, try again!</h2><br><img src=\"https://media.giphy.com/media/jD4DwBtqPXRXa/giphy.gif\" width=\"{pic_width}\""
    elif number > r:
        return f"<h2 color=\"purple\">Too high, try again!</h2><br><img src=\"https://media.giphy.com/media/3o6ZtaO9BZHcOjmErm/giphy.gif\" width=\"{pic_width}\">"
    else:
        return f"<h2 color=\"green\">You find me!</h2><br><img src=\"https://media.giphy.com/media/4T7e4DmcrP9du/giphy.gif\" width=\"{pic_width}\">"

if __name__ == '__main__':
    app.run(debug=True, port=5001)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---