
---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---

## 1. BMI calculator:
```python
height = input(enter height in meters e.g: 1.65: )
weight = input(enter weight in kilograms e.g: 72: )

w = float(weight)
h = float(height)
bmi = w / (h * h)
print(int(bmi))
```
## 2. BMI calculator 2.0
```python
height = float(input(Enter your height in meters e.g., 1.55: ))
weight = int(input(Enter your weight in kilograms e.g., 72: ))

bmi = weight / (height * height)

if bmi <= 18.5:
  print(f"Your BMI is {bmi}, you are underweight.")
elif bmi > 18.5 and bmi < 25:
  print(f"Your BMI is {bmi}, you have a normal weight.")
elif bmi >= 25 and bmi < 30:
  print(f"Your BMI is {bmi}, you are slightly overweight.")
elif bmi >=30 and bmi < 35:
  print(f"Your BMI is {bmi}, you are obese.")
else:
  print(f"Your BMI is {bmi}, you are clinically obese.")
```

---

- [Back to the Python](../python.md)
- [Back to the Main](../../../README.md)

---