importance: 4

---

# Böyük hərf ilə const?

Aşağıdakı koda baxın:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Burada `birthday` adlı sabit zaman dəyişəni və `birthday`-dən hesablanan `age` sabit dəyişəni var (hesablama funksiyasının vacib olmadığından bu kodun tətbiq detalı göstərilməyib).

`birthday` üçün böyük hərf işlətmək yaxşı fikirdir? Bəs `age` üçün? Bəs hər ikisi üçün?

```js
const BIRTHDAY = '18.04.1982'; // böyük hərf ilə yazaq?

const AGE = someCode(BIRTHDAY); // böyük hərf ilə yazaq?
```

