importance: 4

---

# Böyük hərflərlə const?

Aşağıdakı koda baxın:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Burada `birthday` olaraq adlandırılmış bir tarix dəyəri saxlayan konstantımız var. `age` həmin `birthday` və müəyyən bir kodun köməyi ilə hesablanır (qısa olsun deyə və təfərrüatlar burada əhəmiyyətli olmadığı üçün bu kod təmin edilməyib).

`birthday` üçün böyük hərflərdən istifadə etmək yaxşı fikirdir?

```js
const BIRTHDAY = '18.04.1982'; // böyük hərflərlə yazaq?

const AGE = someCode(BIRTHDAY); // böyük hərflərlə yazaq?
```

