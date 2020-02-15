# Dəyişənlər

Çox vaxt JavaScript applikasiyalarının məlumatlar ilə işləmələri lazımdır. Məsələn:
1. onlayn mağaza applikasiyasında satılan mallar və alış-veriş səbəti haqqında məlumatlar lazımdır.
2. çat applikasiyasında isitfadəçilər, ismarıclar və başqa maddələr haqqında məlumatlar lazımdır.

Məlumatları saxlamaq üçün dəyişənlərdən istifadə edilir.

## Dəyişən

[Dəyişən](https://en.wikipedia.org/wiki/Variable_(computer_science)), məlumat üçün üçün "adlı saxlama yeridir." Dəyişənlər ilə mağaza malları, applikasiyaya ziyarət edənlər və digər məlumatları saxlamaq mümkündür.

JavaScript-də dəyişən yaratmaq üçün `let` açar sözündən istifadə edin.

Aşağıdakı ifadədə "message" adlı dəyişən yaradılır (digər sözlə, *bildirilir* ingiliscə, *declare*):

```js
let message;
```

İndi, biz `=` təyinat operatorundan istifadə edərək bu dəyişənə məlumat təyin edə bilərik:

```js
let message;

*!*
message = 'Salam'; // Mətni saxla
*/!*
```

İndi, mətn dəyəri dəyişənə bağlı olan yaddaş sahəsində saxlanılır. Biz, dəyişənin adından istifadə edərək bu dəyəri oxuya bilərik:

```js run
let message;
message = 'Salam!';

*!*
alert(message); // dəyişənin kontentini göstər
*/!*
```

Yığcam kod yazmaq üçün biz dəyişənin yaranmasını və təyinatını bir sətirdə birləşdirə bilərik:

```js run
let message = 'Salam!'; // Dəyişəni müəyyənləşdir və dəyəri təyin et

alert(message); // Salam!
```

Biz, həmçinin bir neçə dəyişəni eyni sətirdə müəyyənləşdirə bilərik:

```js no-beautify
let user = 'Orxan', age = 25, message = 'Salam';
```

Bunun daha qısa olmasına baxmayaraq biz belə kod yazmağı tövsiyyə etmirik. Oxunaqlığı çoxaltmaq üçün hər dəyişən üçün ayrı sətir işlədin.

Çox sətirli variantın biraz uzun olmasına baxmayaraq bunu oxumaq daha asandır:

```js
let user = 'Orxan';
let age = 25;
let message = 'Salam';
```

Bəzi proqramçılar bir neçə dəyişəni aşağıdakı formada:
```js no-beautify
let user = 'Orxan',
  age = 25,
  message = 'Salam';
```

...vı ya "vergül-birinci" stilində də müəyyənləşdirirlər:

```js no-beautify
let user = 'Orxan'
  , age = 25
  , message = 'Salam';
```

Texniki olaraq yuxarıdakı bütün variantlar eyni nəticəni verəcək. Bu səbəbdən, burada vacib olan proqramçıların şəxsi zövqüdür.


````smart header="`let` əvəzinə `var`"
Siz, köhnə skriptlərdə `let` əvəzinə `var` açar sözünün işlədildiyini görə bilərsiniz:

```js
*!*var*/!* message = 'Salam';
```

`var` dəyişəni *az qala* `let` ilə eynidir. Bu açar sözü dəyişənin daha "köhnə" üsul ilə müəyyənləşdirir.

`let` və `var` arasında olan hiss edilməyən fərqlər var. Lakin, indi bu fərqlər bizi maralandırmır. Biz, bu fərqlər haqqında <info:var> bölməsində detallı danışacağıq.
````

## Real dünyada analogiya

"Dəyişən" konsepsiyasını yaxşı anlamaq üçün bunun, üzərində unikal adlı etiketi olan məlumatlar "qutusu" olduğunu fikirləşin.

Məsələn, `message` dəyişəni daxilində "Salam!" dəyəri olan və `"message"` adı ilə etiketlənən qutudur:

![](variable.svg)

Biz qutuda istənilən dəyəri yerləşdirə bilərik.

Əlavə olaraq, biz bu dəyəri istədiyimiz qədər dəyişə bilərik:
```js run
let message;

message = 'Salam!';

message = 'Dünya!'; // dəyər dəyişdi

alert(message);
```

Dəyər dəyişdikdə dəyişəndə olan köhnə məlumat silinir:

![](variable-change.svg)

Əlavə olaraq, biz iki dəyişən yaradıb birinin məlumatını o birisinə kopiyalaya bilərik.

```js run
let hello = 'Salam dünya!';

let message;

*!*
// 'Salam dünya' dəyərini hello dəyişənindən message dəyişəninə kopiyala
message = hello;
*/!*

// indi, hər iki dəyişəndə eyni dəyər saxlanılır
alert(hello); // Salam dünya!
alert(message); // Salam dünya!
```

```smart header="Funksional dillər"
Nəzərinizə çatdırmaq istəyirik ki, [Scala](http://www.scala-lang.org/) və [Erlang](http://www.erlang.org/) kimi [funksional](https://en.wikipedia.org/wiki/Functional_programming) proqramlaşdırma dillərində dəyişənin dəyişilməsinə icazə verilmir.

Bu dillərdə, dəyər "qutuya" yerləşdirildikdən sonra orada ömürlük qalır. Fərqli məlumat saxlamaq istədikdə proqramlaşdırma dili bizə yeni qutu (dəyişənin yaradılması) yaratmağa məcbur edir. Biz köhnə dəyəri yenidən təyin edə bilmirik.

İlk baxışda bunun biraz qəribə olmasına baxmayaraq bu dillərdə çox ciddi təkmilləşdirmə etmək mümkündür. Bundan əlavə, paralel hesablamalar kimi bəzi tapşırıqlarda bu məhdudiyyətin olmasının faydası var. Fikrinizi genişləndirmək üçün bu formalı dili öyrənməyi (hətta bunu işlətməyi planlaşdırmasanız belə) tövsiyyə edirik.
```

## Dəyişənlərin adlandırılması [#variable-naming]

JavaScript-də dəyişənlərin adlandırılmasında iki məhdudiyyət var:

1. Dəyişən adında yalnız hərflər, rəqəmlər və ya `$` və `_` kimi simvollar ola bilər.
2. Dəyişən adının ilk hərfi rəqəm ola bilməz.

Etibarlı adlar üçün nümunələr:

```js
let userName;
let test123;
```

Dəyişən adı bir neçə sözdən ibarət olduqda çox zaman [camelCase](https://en.wikipedia.org/wiki/CamelCase) formatından istifadə olunur. Bu formatında ilk sözdən başqa bütün sözlər böyük hərf ilə başlayır: `myVeryLongName`.

Dəyişən adlarında dollar (`'$'`) altdan xətt (`'_'`) işarələrinin də işlədilə bilməsi maraqlıdır. Bu simvollar, hərflər kimi xüsusi mənası olmayan sadə simvollardır.

Aşağıdakı dəyişən adlar etibarlıdır:

```js run untrusted
let $ = 1; // "$" adlı dəyişən təyin et
let _ = 2; // "_" adlı dəyişən təyin et

alert($ + _); // 3
```

Səhv məlumat adlarının nümunələri:

```js no-beautify
let 1a; // dəyişən adı rəqəm ilə başlaya bilməz

let my-name; // dəyişən adında '-' kimi simvollar ola bilməz
```

```smart header="Case matters"
`apple` və `AppLE` adları fərqli dəyişənlərə istinad edir.
```

````smart header="Latın adlarını işlətmək olar, amma tövsiyyə edilmir"
Kiril hərfləri və iyeroqlif daxil olmaqla istənilən dildə olan hərfləri işlətmək olar:

```js
let имя = '...';
let 我 = '...';
```

Texniki olaraq, burada heç bir xəta yoxdur. Lakin, beynəlxalq ənənəyə görə dəyişən adları İngiliscə yazılır. Kiçik skript yazsaq belə bu skriptin uzun həyatı ola bilər. Digər ölkələrdə olan proqramistlər bu skripti oxumalı ola bilərlər.
````

````warn header="Qorunan adlar"
JavaScript dilində işlədilən bəzi [qorunan sözləri](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords) dəyişən adı kimi işlətmək olmaz.

Məsələn: `let`, `class`, `return` və `function` sözləri qorunur.

Aşağıdakı kodda sintaksis xətası baş verəcək:

```js run no-beautify
let let = 5; // xəta! "let" adlı dəyişən işlətmək olmaz!
let return = 5; // xəta! "return" adlı dəyişən işlətmək olmaz!
```
````

````warn header="`use strict`-siz təyinat"

Normalda, dəyişəni işlətməmişdən öncə bu dəyişəni yaratmaq lazımdır. Lakin, keçmişdə dəyişəni `let` kimi açar sözü işlətmədən müəyyənləşdirmək mümkün idi. Skriptlərə `use strict` əlavə etmədikdə bu formada olan kodlar işləyəcək.

```js run no-strict
// qeyd: bu nümunədə "use strict" işlədilmir

num = 5; // "num" dəyişəni olmadıqda dəyişən yaranacaq

alert(num); // 5
```

Bunun pis praktika olduğundan bu sizə strikt rejimində xəta verəcək:

```js
"use strict";

*!*
num = 5; // xəta: num təyin edilməyib
*/!*
```
````

## Sabit dəyişənlər

Sabit (dəyişməyən) dəyişən yaratmaq istəyirsinizsə, `let` əvəzinə `const` işlədin:

```js
const myBirthday = '18.04.1982';
```

`const` ilə yaranan dəyişənlər "sabit dəyişənlər" adlandırılır. Bu dəyişənləri yenidən təyin etmək mümkün deyil. Dəyişənin dəyərini dəyişmək istədikdə xəta baş verəcək:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // xəta, sabit dəyişəni dəyişmək olmaz!
```

Proqramçı dəyişənin heç vaxt dəyişməyəcəyindən əmin olduqda dəyişəni `const` ilə təyin edərək bu dəyişənin dəyişməyəcəyini siğortalayıb digər proqramçılara bildirə bilər.


### Böyük hərf ilə yazılmış sabit dəyişənlər

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution.

Such constants are named using capital letters and underscores.

For instance, let's make constants for colors in so-called "web" (hexadecimal) format:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...when we need to pick a color
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Benefits:

- `COLOR_ORANGE` is much easier to remember than `"#FF7F00"`.
- It is much easier to mistype `"#FF7F00"` than `COLOR_ORANGE`.
- When reading the code, `COLOR_ORANGE` is much more meaningful than `#FF7F00`.

When should we use capitals for a constant and when should we name it normally? Let's make that clear.

Being a "constant" just means that a variable's value never changes. But there are constants that are known prior to execution (like a hexadecimal value for red) and there are constants that are *calculated* in run-time, during the execution, but do not change after their initial assignment.

For instance:
```js
const pageLoadTime = /* time taken by a webpage to load */;
```

The value of `pageLoadTime` is not known prior to the page load, so it's named normally. But it's still a constant because it doesn't change after assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.  

## Name things right

Talking about variables, there's one more extremely important thing.

A variable name should have a clean, obvious meaning, describing the data that it stores.

Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can reveal which code was written by a beginner versus an experienced developer.

In a real project, most of the time is spent modifying and extending an existing code base rather than writing something completely separate from scratch. When we return to some code after doing something else for a while, it's much easier to find information that is well-labeled. Or, in other words, when the variables have good names.

Please spend time thinking about the right name for a variable before declaring it. Doing so will repay you handsomely.

Some good-to-follow rules are:

- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you're doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It's only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
- Agree on terms within your team and in your own mind. If a site visitor is called a "user" then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.

Sounds simple? Indeed it is, but creating descriptive and concise variable names in practice is not. Go for it.

```smart header="Reuse or create?"
And the last note. There are some lazy programmers who, instead of declaring new variables, tend to reuse existing ones.

As a result, their variables are like boxes into which people throw different things without changing their stickers. What's inside the box now? Who knows? We need to come closer and check.

Such programmers save a little bit on variable declaration but lose ten times more on debugging.

An extra variable is good, not evil.

Modern JavaScript minifiers and browsers optimize code well enough, so it won't create performance issues. Using different variables for different values can even help the engine optimize your code.
```

## Summary

We can declare variables to store data by using the `var`, `let`, or `const` keywords.

- `let` -- is a modern variable declaration.
- `var` -- is an old-school variable declaration. Normally we don't use it at all, but we'll cover subtle differences from `let` in the chapter <info:var>, just in case you need them.
- `const` -- is like `let`, but the value of the variable can't be changed.

Variables should be named in a way that allows us to easily understand what's inside them.
