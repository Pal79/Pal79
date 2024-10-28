
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

```python
print('Thank you for choosing Python Pizza Deliveries!')
size = input('What size pizza do you want? S, M, or L: ')
add_pepperoni = input('Do you want pepperoni? Y or N: ')
extra_cheese = input('Do you want extra cheese? Y or N: ')

result = 0

if size == "S":
  result = 15
  if add_pepperoni == "Y":
    result += 2
  if extra_cheese == "Y":
    result += 1
elif size == "M":
  result = 20
  if add_pepperoni == "Y":
    result += 3
  if extra_cheese == "Y":
    result += 1
else:
  result = 25
  if add_pepperoni == "Y":
    result += 3
  if extra_cheese == "Y":
    result += 1


print(f"Your final bill is: ${result}.")
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---