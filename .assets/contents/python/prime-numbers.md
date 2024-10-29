
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

```python
def prime_checker(number):
    prime = True
    if number < 2:
        prime = False

    for num in range(2, int(number ** 0.5) + 1):
        if number % num == 0:
            prime = False

    if prime == True:
        print("It's a prime number.")
    else:
        print("It's not a prime number.")


n = int(input('Check this number: '))  #
prime_checker(number=n)
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---