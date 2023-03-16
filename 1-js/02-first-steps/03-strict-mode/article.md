# "use strict" modern rejimi

Uzun zaman JavaScript heç bir uyğunluq problemi olmadan inkişaf etdirdi. Dilə yeni xüsusiyyətlər əlavə olunur, köhnə xüsusiyyətlər isə dəyişmirdi.

Bunun mövcud kodu sındırmaması faydası var idi. Lakin, bu, JavaScript yaradıcıları tərəfindən verilən hər bir mükəmməl olmayan qərarın dildə ömürlük qalmasına səbəb olurdu.

2009-cu ildə ECMAScript 5 (ES5) dərc olunana kimi bu problem aktual idi. Lakin, bu versiyadan başlayaraq dilə yeni xüsusiyyətlər əlavə olunmaqdan əlavə, bəzi mövcud xüsusiyyətlər də dəyişdirildi. Köhnə kodun işləməsi üçün bu dəyişikliklərin çoxu standart rejimində söndürülüb. Bu xüsusiyyətləri aktivləşdirmək üçün `"use strict"` xüsusi direktivini əlavə etmək lazımdır.

## "use strict"

Bu direktiv `"use strict"` və ya `'use strict'` formalı mətn formasındadır. Bu direktivi skriptin ən yuxarısında yerləşdirdikdə bütün skript "modern" formada işləyək.

Məsələn:

```js
"use strict";

// Buradakı kod modern formada işləyəcək
...
```

Biz, əmrləri qruplaşdırmaq üçün istifadə olunan funksiyalar haqqında öyrənəcəyik. Nəzərə alın ki, `"use strict"` direktivini skriptin başlanğıcına əlavə etmək əvəzinə funksiya gövdəsinin əvvəlinə də əlavə etmək mümkündür. Bunu etdikdə strikt rejimi yalnız funksiyada aktivləşəcək. Lakin, adətən proqramçılar bu rejimi bütün skript üçün aktivləşdirirlər.


````warn header="\"use strict\" direktivinin ən yuxarıda olmasından əmin olun"
`"use strict"` direktivi skriptlərin ən yuxarısında olmadıqda aktiv olunmaya bilər.

Aşağıdakı nümunədə strikt rejimi aktiv olunmayıb:

```js no-strict
alert("bəzi kod");
// aşağıdakı "use strict" ifadəsi sayılmır. Bu ifadə ən yuxarıda olmalıdır

"use strict";

// strikt rejimi aktiv olunmayıb
```

`"use strict"`-dən öncə yalnız kommentlər əlavə oluna bilər.
````

```warn header="`use strict`-i söndürmək mümkün deyil"
JavaScript mühərrikini köhnə davranışa qaytaran `"no use strict"` kimi direktiv mövcud deyil.

Strikt rejimi aktiv olunduqdan sonra geri dönüş yoxdur.
```

## Brauzer konsolu

Gələcəkdə, xüsusiyyətləri yoxlamaq üçün brauzer konsolundan istifadə etikdə nəzərə alın ki, `use strict` direktivini əl ilə aktivləşdirmək lazımdır.

Bu səbəbdən, `use strict`-in fərq yaratdığı kodlarda səhv nəticələr alacaqsınız.

Konsolda bir neçə sətir əlavə etmək üçün `key:Shift+Enter` klaviatur kombinasiyasından istifadə edərək `use strict` ifadəsini əmrdən öncə təyin edə bilərsiniz:

```js
'use strict'; <yeni sətir üçün Shift+Enter>
//  ...sizin kodunu
<icra etmək üçün Enter düyməsini tıklayın>
```

Bu, Firefox və Chrome daxil olmaqla əksər brauzerlərdə işləyir.

Əgər brauzer konsolunda birdən çox sətir ələvə etmək mümkün deyilsə, `use strict` ifadəsinin işləməsindən əmin olmaq üçün konsola aşağıdakı formalı kodu bilərsiniz:

```js
(function() {
  'use strict';

  // ...kodunuz...
})()
```

## "use strict"-dən həmişə istifadə edin

Biz, hələ ki, strikt və "standart" rejiminin fərqlərindən danışmamışıq.

Gələcək səhifələrdə dilin xüsusiyyətlərindən danışdığımız zaman strikt və standart rejimlərinin fərqlərini qeyd edəcəyik. Xoşbəxtlikdən, bu fərqlər çox deyil və olan fərqlər birim işimizi rahatlaşdırır.

İndi isə bu rejim haqqında ümumi məlumatınızın olması bəsdir:

1. `"use strict"` direktivi JavaScript mühərrikini "modern" rejiminə keçirərək bəzi daxili xüsusiyyətlərin davranışlarını dəyişir. Dərsliyin gələcək bölmələrində bu detallardan danışacağıq.
2. Strikt rejimini aktivləşdirmək üçün `"use strict"` ifadəsini skript və ya funksiyanın əvvəlinə əlavə edin. "siniflər" və "modullar" kimi bəzi dil xüsusiyyətlərini istifadə etdikdə strikt rejimi avtomatik olaraq aktiv olunur.
3. Strict rejimi bütün modern brauzerlərdə dəstəklənir.
4. Biz bütün skriptləri `"use strict"` ilə başlamağı tövsiyyə edirik. Bu dərslikdəki bütün nümunələrdə strikt rejiminin aktiv olunduğu fərz edilir. Çox nadir hallarda strikt rejimi işlədilmədikdə bu açıq şəkildə bildiriləcək.
