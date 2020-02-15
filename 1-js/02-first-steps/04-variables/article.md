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

Praktikada, çətin yadda qalan dəyərlər skript icra olunmamışdan öncə sabit dəyişələr ilə ləqəbləndirilir.

Bu formalı sabit dəyişənlər böyük hərf və altdan xətt ilə adlandırılırlar.

Məsələn, gəlin "veb" (16-lı rəqəm) formatında olan rənglər üçün sabit dəyişənlər yaradaq:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...rəngdən istifadə etdikdə
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Faydaları:

- `COLOR_ORANGE` dəyəri yadda saxlamaq `"#FF7F00"` dəyərini yadda saxlamaqdan daha asandır.
- `"#FF7F00"` dəyərində səhv etmək `COLOR_ORANGE` dəyərində səhv etməkdən daha asandır.
- Kodu oxuduqda `COLOR_ORANGE` dəyərinin mənası `#FF7F00` dəyərinin mənasından daha çoxdur.

Sabit dəyişənləri nə zaman normal formada, nə zaman isə böyük hərflər ilə yazmaq lazımdır? Gəlin bunun açıqlamasını verək.

Dəyişənin "sabit" olması, bu dəyişənin heç vaxt dəyişməməsi deməkdir. Lakin, bəzi sabit dəyişənlər skript icra olunmamışdan öncə (qırmızı rəngin 16-lıq rəqəmi kimi) , bəziləri isə icra zamanı *hesablanır* və sabit qalır.

Məsələn:
```js
const pageLoadTime = /* veb səhifənin yüklənməsinə xərclənən zaman */;
```

`pageLoadTime` dəyəri səhifə yüklənməmişdən öncə bilinmədiyindən bu, normal adlandırılır. Lakin, bu dəyər təyin edildikdən sonra dəyişmədiyindən sabit qalır.

Digər sözlə, böyük hərf ilə yazılan sabit dəyişənləri yalnız "əl ilə" yazılan dəyərlər üçün istifadə edin. 

## Dəyişənləri düzgün adlandırın

Dəyişənləri adlandırdıqda çox vacib məqam var.

Dəyişən adının saxladığı məlumatı təsvir edən təmin və mənalı adı olmalıdır.

Dəyişənləri adlandırmaq proqramlaşdırmada çox vacib və mürəkkəb bacarıqlardan biridir. Dəyişənin adına baxdıqda kodun yenibaşlayan və ya təcrübəli proqramçının yazdığını bilmək mümkündür.

Real layihədə işlədikdə vaxtın çoxu sıfırdan kod yazmaq əvəzinə mövcud kodu dəyişməyə və artırmağa gedir. Digər tapşırıqlardan kodunuza qayıtdıqda yaxşı adlandırılmış məlumatları tapmaq daha asandır. Digər sözlə dəyişənləri yaxşı adlandırmaq lazımdır.

Dəyişəni müəyyənləşdirməmişdən öncə yaxşı ad haqqında biraz fikirləşin. Bunu etdikdə faydasını görəcəksiniz.

Bəzi əməl edə biləcəyiniz yaxşı qaydalar:

- `userName` və ya `shoppingCart` kimi insanların başa düşə biləcəyi adlardan istifadə edin.
- Qısaldılmış adlardan və ya `a`, `b`, `c` kimi adlardan uzaq durun.
- Adları maksimal dərəcədə təsvirli və dəqiq edin. `data` və `value` kimi adlar pisdir. Bu adlar nəyin baş verdiyi haqqda heç nə təsvir etmir. Əgər kodun konteksti dəyişənin hansı məlumat və ya dəyərə istinad etdiyini göstərirsə, belə adlardan istifadə etmək olar.
- Komandanızda və beyninizdə terminlər haqqında razılığıa gəlin. Əgər sayt ziyatətçisi "user" adlanırsa, buna aid dəyişənləri `currentVisitor` və ya `newManInTown` adlandırmaq əvəzinə `currentUser` və ya `newUser` adlandırın.

Sadə görünür? Bunun sadə görünməyinə baxmayaraq praktikada təsvirli və dəqiq dəyişən adları düzəltmək çətindir.

```smart header="Yenidən işlət yoxsa yarat?"
Bəzi avara proqramçılar yeni dəyişən yaratmaq əvəzinə mövcud dəyişəni istifadə etməyi sevirlər.

Nəticədə, bu dəyişənlər etiketi dəyişməyən, amma daxili dəyişən qutulara bənzəyirlər. Qutunun içində nəyin olduğunu heç kim bilmir. Bu səbəbdən, biz bu kodlara yaxından baxım yoxlamalıyıq.

Bu proqramçılar dəyişən yaratmaqda az vaxt, amma debaq zamanı on dəfə çox vaxt xərcləyirlər.

Yeni dəyişən yaratmaq pis deyil.

Modern JavaScript minifikasiya edici qurğuları və brauzerlər kodu yaxşı optimallaşdırırlar. Bu səbəbdən, çox dəyişən yaratdıqda performans problemləri yaranmayacaq. Fərqli dəyərlər üçün fərqli dəyişənlər işlətdikdə JavaScript mühərriki kodunuzu daha da yaxşı optimizasiya edə bilər.
```

## Xülasə

Dəyişənləri  `var`, `let` və ya `const` açar sözləri ilə yaratmaq mümkündür.

- `let` -- modern dəyişən yaratmaq üçün işlədilir.
- `var` -- köhnə üsulda dəyişən yaratmaq üçün işlədilir. Normalda, biz bu dəyişəndən istifadə etmirik, amma <info:var> bölməsində `let` və `var` arasında olan fərqlərdən danışacağıq.
- `const` -- `let` kimidir. Lakin, bununla yaranan dəyişənin dəyəri dəyişə bilməz.

Dəyişənləri, təyin olunan dəyəri yaxşı başa salan adlar ilə adlandırmağı tövsiyyə edirik.
