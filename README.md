# LEETCODE-Arrays-3623
Here’s a **very beginner-friendly dry run** of the code for the input:

```
points = [[1,0],[2,0],[3,0],[2,2],[3,2]]
```

---

# ✅ **Step 1: Count how many points exist on each Y-coordinate**

We loop through all points and store:

```
Y = 0 → 3 points   (because [1,0], [2,0], [3,0])
Y = 2 → 2 points   (because [2,2], [3,2])
```

So the map becomes:

```
countByY = {0=3, 2=2}
```

---

# ✅ **Step 2: Sort the Y-coordinates**

```
yCord = [0, 2]
```

---

# ✅ **Step 3: For each Y-level, compute how many pairs of points exist**

A horizontal line (Y = constant) forms **pairs (choose 2)**.

Formula used:

```
pairs = c * (c - 1) / 2
```

### For Y = 0:

```
c = 3
pairs = 3*2/2 = 3
```

(3 points give pairs: (A,B), (A,C), (B,C))

### For Y = 2:

```
c = 2
pairs = 2*1/2 = 1
```

(2 points give 1 pair)

So:

```
hPlanes = [3, 1]
```

---

# ✅ **Step 4: Count trapezoids**

A trapezoid forms when you pick **one pair on one horizontal line** and **one pair on another horizontal line**.

We use:

```
prefix = running sum of previous hPlane values
result = total trapezoids
```

### Start:

```
prefix = 0
result = 0
```

---

### **Iteration 1:** h = 3 (for Y = 0)

```
result = result + prefix * h
       = 0 + 0 * 3
       = 0

prefix = prefix + h
        = 0 + 3
        = 3
```

---

### **Iteration 2:** h = 1 (for Y = 2)

```
result = result + prefix * h
       = 0 + 3 * 1
       = 3

prefix = prefix + h
        = 3 + 1
        = 4
```

---

# 🎉 **Final Output: 3**

---

# ✅ Why the answer is 3?

From Y = 0 → 3 pairs
From Y = 2 → 1 pair

To make a trapezoid, choose **one pair from Y=0** and **one pair from Y=2**:

```
3 (from Y=0) × 1 (from Y=2) = 3 trapezoids
```

✔ **Final Answer = 3**

---
