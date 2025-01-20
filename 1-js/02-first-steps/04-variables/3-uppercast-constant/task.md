importance: 4

---

# Böyük hərflərlə const?

Aşağıdakı koda baxın:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

<<<<<<< HEAD
Burada `birthday` olaraq adlandırılmış bir tarix dəyəri saxlayan konstantımız var. `age` həmin `birthday` və müəyyən bir kodun köməyi ilə hesablanır (qısa olsun deyə və təfərrüatlar burada əhəmiyyətli olmadığı üçün bu kod təmin edilməyib).
=======
Here we have a constant `birthday` for the date, and also the `age` constant.

The `age` is calculated from `birthday` using `someCode()`, which means a function call that we didn't explain yet (we will soon!), but the details don't matter here, the point is that `age` is calculated somehow based on the `birthday`.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

`birthday` üçün böyük hərflərdən istifadə etmək yaxşı fikirdir?

```js
<<<<<<< HEAD
const BIRTHDAY = '18.04.1982'; // böyük hərflərlə yazaq?

const AGE = someCode(BIRTHDAY); // böyük hərflərlə yazaq?
=======
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```
