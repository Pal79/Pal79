
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

# Blog Project

> BootStrap:
>
> - ![Clean Blog BootStrap](./blog_project/startbootstrap-clean-blog-gh-pages.zip)


<details>
    <summary>./templates</summary>

> about.html

```html
{% include "header.html" %}
        <!-- Page Header-->
        <header class="masthead" style="background-image: url({{ url_for('static', filename='assets/img/about-bg.jpg') }})">
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="page-heading">
                            <h1>About Me</h1>
                            <span class="subheading">This is what I do.</span>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Main Content-->
        <main class="mb-4">
            <div class="container px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Saepe nostrum ullam eveniet pariatur voluptates odit, fuga atque ea nobis sit soluta odio, adipisci quas excepturi maxime quae totam ducimus consectetur?</p>
                        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eius praesentium recusandae illo eaque architecto error, repellendus iusto reprehenderit, doloribus, minus sunt. Numquam at quae voluptatum in officia voluptas voluptatibus, minus!</p>
                        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut consequuntur magnam, excepturi aliquid ex itaque esse est vero natus quae optio aperiam soluta voluptatibus corporis atque iste neque sit tempora!</p>
                    </div>
                </div>
            </div>
        </main>
        <!-- Footer-->
{% include "footer.html" %}
```

> contact.html

```html
{% include "header.html" %}
        <!-- Page Header-->
        <header class="masthead" style="background-image: url({{ url_for('static', filename='assets/img/contact-bg.jpg') }})">
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="page-heading">
                            {% if msg_sent: %}
                            <h1>Successfully sent your message</h1>
                            {% else: %}
                            <h1>Contact Me</h1>
                            <span class="subheading">Have questions? I have answers.</span>
                            {% endif %}
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Main Content-->
        <main class="mb-4">
            <div class="container px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <p>Want to get in touch? Fill out the form below to send me a message and I will get back to you as soon as possible!</p>
                        <div class="my-5">
                            <!-- * * * * * * * * * * * * * * *-->
                            <!-- * * SB Forms Contact Form * *-->
                            <!-- * * * * * * * * * * * * * * *-->
                            <!-- This form is pre-integrated with SB Forms.-->
                            <!-- To make this form functional, sign up at-->
                            <!-- https://startbootstrap.com/solution/contact-forms-->
                            <!-- to get an API token!-->
                            <form id="contactForm" data-sb-form-api-token="API_TOKEN" method="post" action="{{ url_for('contact') }}">
                                <div class="form-floating">
                                    <input class="form-control" name="name" id="name" type="text" placeholder="Enter your name..." data-sb-validations="required" />
                                    <label for="name">Name</label>
                                    <div class="invalid-feedback" data-sb-feedback="name:required">A name is required.</div>
                                </div>
                                <div class="form-floating">
                                    <input class="form-control" name="email" id="email" type="email" placeholder="Enter your email..." data-sb-validations="required,email" />
                                    <label for="email">Email address</label>
                                    <div class="invalid-feedback" data-sb-feedback="email:required">An email is required.</div>
                                    <div class="invalid-feedback" data-sb-feedback="email:email">Email is not valid.</div>
                                </div>
                                <div class="form-floating">
                                    <input class="form-control" name="phone" id="phone" type="tel" placeholder="Enter your phone number..." data-sb-validations="required" />
                                    <label for="phone">Phone Number</label>
                                    <div class="invalid-feedback" data-sb-feedback="phone:required">A phone number is required.</div>
                                </div>
                                <div class="form-floating">
                                    <textarea class="form-control" name="message" id="message" placeholder="Enter your message here..." style="height: 12rem" data-sb-validations="required"></textarea>
                                    <label for="message">Message</label>
                                    <div class="invalid-feedback" data-sb-feedback="message:required">A message is required.</div>
                                </div>
                                <br />
                                <!-- Submit success message-->
                                <!---->
                                <!-- This is what your users will see when the form-->
                                <!-- has successfully submitted-->
                                <div class="d-none" id="submitSuccessMessage">
                                    <div class="text-center mb-3">
                                        <div class="fw-bolder">Form submission successful!</div>
                                        To activate this form, sign up at
                                        <br />
                                        <a href="https://startbootstrap.com/solution/contact-forms">https://startbootstrap.com/solution/contact-forms</a>
                                    </div>
                                </div>
                                <!-- Submit error message-->
                                <!---->
                                <!-- This is what your users will see when there is-->
                                <!-- an error submitting the form-->
                                <div class="d-none" id="submitErrorMessage"><div class="text-center text-danger mb-3">Error sending message!</div></div>
                                <!-- Submit Button-->
                                <button class="btn btn-primary text-uppercase" id="submitButton" type="submit">Send</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </main>
        <!-- Footer-->
{% include "footer.html" %}
```

> footer.html

```html
        <footer class="border-top">
            <div class="container px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <ul class="list-inline text-center">
                            <li class="list-inline-item">
                                <a href="#!">
                                    <span class="fa-stack fa-lg">
                                        <i class="fas fa-circle fa-stack-2x"></i>
                                        <i class="fab fa-twitter fa-stack-1x fa-inverse"></i>
                                    </span>
                                </a>
                            </li>
                            <li class="list-inline-item">
                                <a href="#!">
                                    <span class="fa-stack fa-lg">
                                        <i class="fas fa-circle fa-stack-2x"></i>
                                        <i class="fab fa-facebook-f fa-stack-1x fa-inverse"></i>
                                    </span>
                                </a>
                            </li>
                            <li class="list-inline-item">
                                <a href="#!">
                                    <span class="fa-stack fa-lg">
                                        <i class="fas fa-circle fa-stack-2x"></i>
                                        <i class="fab fa-github fa-stack-1x fa-inverse"></i>
                                    </span>
                                </a>
                            </li>
                        </ul>
                        <div class="small text-center text-muted fst-italic">Copyright &copy; Your Website 2023</div>
                    </div>
                </div>
            </div>
        </footer>
        <!-- Bootstrap core JS-->
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>
        <!-- Core theme JS-->
        <script src="{{ url_for('static', filename='js/scripts.js') }}"></script>
    </body>
</html>
```

> header.html

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
        <meta name="description" content="" />
        <meta name="author" content="" />
        <title>Clean Blog - Start Bootstrap Theme</title>
        <link rel="icon" type="image/x-icon" href="{{ url_for('static', filename='assets/favicon.ico') }}" />
        <!-- Font Awesome icons (free version)-->
        <script src="https://use.fontawesome.com/releases/v6.3.0/js/all.js" crossorigin="anonymous"></script>
        <!-- Google fonts-->
        <link href="https://fonts.googleapis.com/css?family=Lora:400,700,400italic,700italic" rel="stylesheet" type="text/css" />
        <link href="https://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,700italic,800italic,400,300,600,700,800" rel="stylesheet" type="text/css" />
        <!-- Core theme CSS (includes Bootstrap)-->
        <link href="{{ url_for('static', filename='css/styles.css') }}" rel="stylesheet" />
    </head>
    <body>
        <!-- Navigation-->
        <nav class="navbar navbar-expand-lg navbar-light" id="mainNav">
            <div class="container px-4 px-lg-5">
                <a class="navbar-brand" href="index.html">Start Bootstrap</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                    Menu
                    <i class="fas fa-bars"></i>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ms-auto py-4 py-lg-0">
                        <li class="nav-item"><a class="nav-link px-lg-3 py-3 py-lg-4" href="{{ url_for('home') }}">Home</a></li>
                        <li class="nav-item"><a class="nav-link px-lg-3 py-3 py-lg-4" href="{{ url_for('about') }}">About</a></li>
                        <li class="nav-item"><a class="nav-link px-lg-3 py-3 py-lg-4" href="{{ url_for('contact') }}">Contact</a></li>
                    </ul>
                </div>
            </div>
        </nav>
```

> index.html

```html
{% include "header.html" %}
        <!-- Page Header-->
        <header class="masthead" style="background-image: url({{ url_for('static', filename='assets/img/home-bg.jpg') }})">
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="site-heading">
                            <h1>Clean Blog</h1>
                            <span class="subheading">A Blog Theme by Start Bootstrap</span>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Main Content-->
        <div class="container px-4 px-lg-5">
            <div class="row gx-4 gx-lg-5 justify-content-center">
                <div class="col-md-10 col-lg-8 col-xl-7">
                    <!-- Post preview-->
                    {% for post in all_posts %}
                    <div class="post-preview">
                        <a href="{{ url_for('post', id=post.id) }}">
                            <h2 class="post-title">{{ post.title }}</h2>
                            <h3 class="post-subtitle">{{ post.subtitle }}</h3>
                        </a>
                        <p class="post-meta">
                            Posted by
                            <a href="#!">{{ post.author }}</a>
                            on {{ post.date }}
                        </p>
                    </div>
                    <!-- Divider-->
                    <hr class="my-4" />
                    {% endfor %}
                    <!-- Pager-->
                    <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div>
                </div>
            </div>
        </div>
        <!-- Footer-->
{% include "footer.html" %}
```

> post.html

```html
{% include "header.html" %}
        <!-- Page Header-->
        <header class="masthead" style="background-image: url({{ post.image_url }})">
            <div class="container position-relative px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <div class="post-heading">
                            <h1>{{ post.title }}</h1>
                            <h2 class="subheading">{{ post.subtitle }}</h2>
                            <span class="meta">
                                Posted by
                                <a href="#!">{{ post.author }}</a>
                                on {{ post.date }}
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Post Content-->
        <article class="mb-4">
            <div class="container px-4 px-lg-5">
                <div class="row gx-4 gx-lg-5 justify-content-center">
                    <div class="col-md-10 col-lg-8 col-xl-7">
                        <p>{{ post.body }}</p>
                    </div>
                </div>
            </div>
        </article>
        <!-- Footer-->
{% include "footer.html" %}
```

</details>

> main.py

```python
from flask import Flask, render_template, request
import requests
import smtplib

OWN_EMAIL = "pal.daniel.79@gmail.com"
OWN_PASSWORD = "OWN_PASSWORD"

API_ENDPOINT = "https://api.npoint.io/eb6cd8a5d783f501ee7d"
posts = requests.get(API_ENDPOINT).json()
#print(posts)
PORT = 587

app = Flask(__name__)

@app.route("/")
def home():
    return render_template(
        "index.html",
        all_posts=posts
    )

@app.route("/about")
def about():
    return render_template("about.html")

@app.route("/contact", methods=["GET","POST"])
def contact():
    if request.method == "POST":
        data = request.form
        email_send(
            data["name"],
            data["email"],
            data["phone"],
            data["message"]
        )
        return render_template(
            "contact.html",
            msg_sent=True
        )
    return render_template(
        "contact.html",
        msg_sent=False
    )

@app.route("/post/<int:id>")
def post(id):
    requested_post = None
    for post in posts:
        if post["id"] == id:
            requested_post = post
    return render_template(
        "post.html",
        post=requested_post
    )

def email_send(name,email,phone,message):
    email_message = f"Subject: New Message\n\n" \
                    f"Name: {name}\n" \
                    f"Email: {email}\n" \
                    f"Phone: {phone}\n" \
                    f"Message:\n" \
                    f"{message}"
    enc_msg = email_message.encode("UTF-8")
    with smtplib.SMTP("smtp.gmail.com") as connection:
        connection.starttls()
        connection.login(
            user=OWN_EMAIL,
            password=OWN_PASSWORD
        )
        connection.sendmail(
            from_addr=OWN_EMAIL,
            to_addrs=OWN_EMAIL,
            msg=enc_msg
        )

if __name__ == "__main__":
    app.run(debug=True)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---