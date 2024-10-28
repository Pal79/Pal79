
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

```python
print("The Love Calculator is calculating your score...")
name1 = input('What is your name?')
name2 = input('What is their name?')

result_1 = 0
result_2 = 0
name1_lower = name1.lower()
name2_lower = name2.lower()

t_true = name1_lower.count("t") +  name2_lower.count("t")
result_1 += t_true
r_true = name1_lower.count("r") + name2_lower.count("r")
result_1 += r_true
u_true = name1_lower.count("u") + name2_lower.count("u")
result_1 += u_true
e_true = name1_lower.count("e") + name2_lower.count("e")
result_1 += e_true

l_love = name1_lower.count("l") +  name2_lower.count("l")
result_2 += l_love
o_love = name1_lower.count("o") + name2_lower.count("o")
result_2 += o_love
v_love = name1_lower.count("v") + name2_lower.count("v")
result_2 += v_love
e_love = name1_lower.count("e") + name2_lower.count("e")
result_2 += e_love

result = int(f"{result_1}{result_2}")

if result < 10 or result > 90:
  print(f"Your score is {result}, you go together like coke and mentos.")
elif result > 40 and result < 50:
  print(f"Your score is {result}, you are alright together.")
else:
  print(f"Your score is {result}.")
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---