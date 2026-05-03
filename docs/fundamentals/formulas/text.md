# 🔤 Text Functions (Production)

---

## 📊 Data

| Full Name        |
| ---------------- |
| John Michael Doe |

---

# 1. Extract First Name

## Formula

```excel id="txt1"
=LEFT(A2,FIND(" ",A2)-1)
```

---

## Explanation

* FIND space
* LEFT extract before space

---

## Result

→ John

---

## Edge Cases

* No space → error
  Fix:

```excel id="txt2"
=IFERROR(LEFT(A2,FIND(" ",A2)-1),A2)
```

---

# 2. Extract Last Name

```excel id="txt3"
=RIGHT(A2,LEN(A2)-FIND("@",SUBSTITUTE(A2," ","@",LEN(A2)-LEN(SUBSTITUTE(A2," ","")))))
```

---

## Use Case

* CRM data cleaning
