

Complete **Question 1** and **Question 2** using JavaScript.

---

# Question 1: One-by-one Tea Shop

## Task

Write JavaScript `console.log()` code to show a tea shop serving **5 customers one by one**.

---

## Rule

One customer must finish before the next customer starts.

Each customer must complete these 3 steps:

- Customer orders tea.
- Shopkeeper prepares tea.
- Customer gets tea.

---

## Customer Details

- Arjun orders **Milk Tea**
- Meena orders **Ginger Tea**
- Kavin orders **Plain Tea**
- Priya orders **Lemon Tea**
- Suresh orders **Masala Tea**

---

## Instructions

Your code should print this flow:

- Tea shop opened.
- Arjun orders Milk Tea.
- Shopkeeper prepares Milk Tea for Arjun.
- Arjun gets Milk Tea.
- Meena orders Ginger Tea.
- Shopkeeper prepares Ginger Tea for Meena.
- Meena gets Ginger Tea.
- Kavin orders Plain Tea.
- Shopkeeper prepares Plain Tea for Kavin.
- Kavin gets Plain Tea.
- Priya orders Lemon Tea.
- Shopkeeper prepares Lemon Tea for Priya.
- Priya gets Lemon Tea.
- Suresh orders Masala Tea.
- Shopkeeper prepares Masala Tea for Suresh.
- Suresh gets Masala Tea.
- Tea shop closed.

---

## Use only

```javascript
console.log()
```

---




# Question 2: Tea Shop with Waiting Time

## Task

Write JavaScript `console.log()` and `setTimeout()` code to show a tea shop serving **5 customers with different tea preparation times**.

---

## Rule

All customers can place their orders first.

Each customer gets tea only after their tea preparation time is completed.

---

## Customer Details

- Arjun orders **Milk Tea**
  - Preparation time: **5 seconds**

- Meena orders **Ginger Tea**
  - Preparation time: **4 seconds**

- Kavin orders **Plain Tea**
  - Preparation time: **3 seconds**

- Priya orders **Lemon Tea**
  - Preparation time: **2 seconds**

- Suresh orders **Ready-made Tea**
  - Preparation time: **1 second**

---

## Instructions

Your code should print this flow:

- Tea shop opened.
- Arjun orders Milk Tea.
- Shopkeeper starts preparing Milk Tea for Arjun.
- Set a timer for 5 seconds.
- After 5 seconds, print Arjun gets Milk Tea.
- Meena orders Ginger Tea.
- Shopkeeper starts preparing Ginger Tea for Meena.
- Set a timer for 4 seconds.
- After 4 seconds, print Meena gets Ginger Tea.
- Kavin orders Plain Tea.
- Shopkeeper starts preparing Plain Tea for Kavin.
- Set a timer for 3 seconds.
- After 3 seconds, print Kavin gets Plain Tea.
- Priya orders Lemon Tea.
- Shopkeeper starts preparing Lemon Tea for Priya.
- Set a timer for 2 seconds.
- After 2 seconds, print Priya gets Lemon Tea.
- Suresh orders Ready-made Tea.
- Shopkeeper starts preparing Ready-made Tea for Suresh.
- Set a timer for 1 second.
- After 1 second, print Suresh gets Ready-made Tea.
- Print Shopkeeper continues taking other orders.

---

## Use only

```javascript
console.log()
setTimeout()
```

---

## Time Help

```javascript
1000 = 1 second
2000 = 2 seconds
3000 = 3 seconds
4000 = 4 seconds
5000 = 5 seconds
```
