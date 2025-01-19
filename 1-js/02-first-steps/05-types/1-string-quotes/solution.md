
Tərs dırnaqlar (backticks: ``) `${...}` daxilində ifadəni mətndə yerləşdirir.

```js run
let name = "Ilya";

// İfadənin çıxışı bir rəqəmdir: 1
alert( `salam ${1}` ); // salam 1

// İfadənin çıxışı bir mətndir: "ad"
alert( `salam ${"ad"}` ); // salam ad

// İfadə dəyişən olduğundan, dəyişənin dəyəri istifadə olunacaq
alert( `salam ${name}` ); // salam Ilya
```
