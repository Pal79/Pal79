
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

# Birthday Wishers SMTP

---

> birthdays.csv (természetesen az email címeket és a neveket valós nevekre kell megváltoztatni)

```csv
name,email,year,month,day
Teszt Elek,tesztelek@gmail.com,1968,08,03
Végh Béla,veghbela@gmail.com,1973,03,08
Tök Ödön,tokodon@gmail.com,1990,11,23
```

> ./letter_templates

> letter_1.txt

```TXT
Dear [NAME]

Happy Birthday!

All the best for the year!

[SENDING_NAME]
```

> letter_2.txt

```TXT
Hey [NAME],

Happy Birthday! Have a wonderful time and eat lots of cake!

Lots of love,

[SENDING_NAME]
```

> letter_3.txt

```TXT
Dear [NAME],

It's your birthday! Have a great day!

All my love,

[SENDING_NAME]
```

> main.py

```python
import smtplib
import random
from datetime import datetime
import pandas

OWN_EMAIL = "OWN_EMAIL"
OWN_EMAIL_PASSWORD = "OWN_EMAIL_PASSWORD"

today = datetime.now()
today_tuple = (today.month, today.day)

data = pandas.read_csv("birthday.csv")
birthdays_dict = {(data_row.month,data_row.day): data_row for (index,data_row) in data.iterrows()}

if today_tuple in birthdays_dict:
    birthday_person = birthdays_dict[today_tuple]
    sending_name = my_name
    file_path = f"letter_templates/letter_{random.randint(1,3)}.txt"

    with open(file_path) as letter_file:
        contents = letter_file.read()
        contents = contents.replace("[NAME]", birthday_person.name)
        contents = contents.replace(["SENDING_NAME"],sending_name)

    with smtplib.SMTP("smtp.gmail.com") as connection:
        connection.starttls()
        connection.login(OWN_EMAIL,OWN_EMAIL_PASSWORD)
        connection.sendmail(
            from_addr=OWN_EMAIL,
            to_addrs=birthday_person.email,
            msg=f"Subject: Happy Birthday\n\n{contents}"
        )
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---
