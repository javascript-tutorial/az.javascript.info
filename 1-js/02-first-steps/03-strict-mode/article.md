# Müasir Rejim, "use strict"

JavaScript uzun müddət ərzində uyğunsuzluq problemləri olmadan inkişaf etdi. Köhnə xüsusiyyətlər dəyişdirilmədən, dilə yeni xüsusiyyətlər əlavə olundu.

Bunun üstünlüyü mövcud kodun işləmə qabiliyyətini heç vaxt pozmaması idi. Lakin mənfi tərəfi o idi ki, JavaScript'in yaradıcılarının etdiyi hərhansı bir səhv və ya düzgün olmayan bir qərar dilin daimi bir hissəsinə çevrilirdi.

Bu vəziyyət 2009-cu ildə ECMAScript 5 (ES5) standartı təqdim edilənə qədər davam etdi. ES5 dilə yeni xüsusiyyətlər əlavə etdi və mövcud olan bəzi xüsusiyyətləri dəyişdirdi. Köhnə kodların işləməyə davam etməsi üçün bir çox dəyişikliklər susqunluq halında (by default) deaktiv edilmişdi. Bu dəyişiklikləri aktiv etmək üçün xüsusi bir direktivdən istifadə etməlisiniz: `"use strict"`.

## "use strict"

Bu direktiv bir string kimi görünür: `"use strict"` və ya `'use strict'`. Əgər bu direktiv bir skriptin ən üst hissəsində yerləşdirilərsə, həmin skript "müasir" qaydada işləyir.

Məsələn:

```js
"use strict";

// bu kod müasir qaydada işləyir
...
```

<<<<<<< HEAD
Biz funksiyaları (ifadələri qruplaşdırmaq üçün bir yoldur) tezliklə öyrənəcəyik. İndilik isə qeyd etməliyik ki, `"use strict"` direktivini skriptin ən üstündə yerləşdirmək əvəzinə, bir funksiyanın başlanğıcına da əlavə etmək mümkündür. Bu halda yalnız həmin funksiya müasir qaydada işləyəcək. Lakin, adətən insanlar bu direktivi bütün skript üçün istifadə edirlər.

````warn header="\"use strict\" direktivinin ən üstdə olduğundan əmin olun"
Əmin olun ki, `"use strict"` direktivi skriptinizin ən üst hissəsində yerləşir, əks halda sıx rejim aktivləşməyəcək.
=======
Quite soon we're going to learn functions (a way to group commands), so let's note in advance that `"use strict"` can be put at the beginning of a function. Doing that enables strict mode in that function only. But usually people use it for the whole script.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Burada sıx rejim aktiv deyil:

```js no-strict
alert("bəzi kodlar");
// "use strict" aşağıda yerləşdiyindən nəzərə alınmayacaq -- o mütləq ən yuxarıda olmalıdır

"use strict";

// sıx rejim aktiv deyil
```

Sadəcə şərhlər `"use strict"` direktivindən əvvəl yerləşdirilə bilər.
````

```warn header="`use strict`'i ləğv etmək mümkün deyil"
Sıx rejimi deaktiv etmək üçün `"no use strict"` kimi bir direktiv mövcud deyil.

Bir dəfə sıx rejim aktivləşdikdən sonra, geri dönüş mümkün deyil.
```

## Brauzer Konsolu

<<<<<<< HEAD
Gələcəkdə brauzerin konsolundan xüsusiyyətləri test etmək üçün istifadə etdikdə unutmayın ki, konsol susqunluq halında `use strict` seçənəyini aktivləşdirmir.
=======
When you use a [developer console](info:devtools) to run code, please note that it doesn't `use strict` by default.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Bəzən, `use strict` ilə fərqlər yaranır və nəticədə yanlış nəticələr əldə edə bilərsiniz.

<<<<<<< HEAD
`key:Shift+Enter` kombinasiyasından istifadə edərək çoxsətirli kod daxil edib `use strict` direktivini ən üstünə yerləşdirin. Məsələn:
=======
So, how to actually `use strict` in the console?

First, you can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

```js
'use strict'; <Shift+Enter ilə yeni sətir əlavə edin>
//  ...sizin kod
<İcra etmək üçün Enter>
```

Bu metod əksər brauzerlərdə, məsələn, Firefox və Chrome'da işləyir.

<<<<<<< HEAD
Əgər bu işləməzsə, `use strict` ifadəsini istifadə etmənin ən etibarlı yolu aşağıdakı nümunədə göstərildiyi kimi istifadə etməkdir:
=======
If it doesn't, e.g. in an old browser, there's an ugly, but reliable way to ensure `use strict`. Put it inside this kind of wrapper:
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

```js
(function() {
  'use strict';

<<<<<<< HEAD
  // ...sizin kod...
})()
```

## Hər Zaman "use strict"

Biz hələ sıx rejim ilə "default" rejim arasındakı fərqləri tam əhatə etməmişik.

Növbəti fəsillərdə dil xüsusiyyətlərini öyrəndikcə, sıx rejim və defolt rejim arasındakı fərqləri vurğulayacağıq. Xoşbəxtlikdən, bu fərqlər azdır və həyatımızı daha da asanlaşdırır.

İndilik, aşağıdakıları bilmək kifayətdir:

1. `"use strict"` direktivi mühərriki sıx rejimə keçirir və bəzi daxili xüsusiyyətlərin davranışını dəyişir. Bunun detallarını daha sonra dərslikdə öyrənəcəyik.
2. `"use strict"` direktivini skriptin və ya funksiyanın ən üstünə yerləşdirərək sıx rejimi aktivləşdirə bilərsiniz. "Siniflər" ("classes") və "modullar" ("modules") kimi bəzi dil xüsusiyyətləri sıx rejimi avtomatik aktivləşdirir.
3. Sıx rejim bütün müasir brauzerlər tərəfindən dəstəklənir.
4. Tövsiyə olunur ki, bütün skriptlərinizə `"use strict"` ilə başlayasınız. Bu dərslikdəki nümunələrin hamısı, başqa cür göstərilmədiyi təqdirdə (çox nadir hallarda), sıx rejimi nəzərdə tutur.
=======
  // ...your code here...
})()
```

## Should we "use strict"?

The question may sound obvious, but it's not so.

One could recommend to start scripts with `"use strict"`... But you know what's cool?

Modern JavaScript supports "classes" and "modules" - advanced language structures (we'll surely get to them), that enable `use strict` automatically. So we don't need to add the `"use strict"` directive, if we use them.

**So, for now `"use strict";` is a welcome guest at the top of your scripts. Later, when your code is all in classes and modules, you may omit it.**

As of now, we've got to know about `use strict` in general.

In the next chapters, as we learn language features, we'll see the differences between the strict and old modes. Luckily, there aren't many and they actually make our lives better.

All examples in this tutorial assume strict mode unless (very rarely) specified otherwise.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e
