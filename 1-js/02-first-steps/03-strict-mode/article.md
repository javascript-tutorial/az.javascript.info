# Müasir rejim, "use strict"

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

Biz funksiyaları (ifadələri qruplaşdırmaq üçün bir yoldur) tezliklə öyrənəcəyik. İndilik isə qeyd etməliyik ki, `"use strict"` direktivini skriptin ən üstündə yerləşdirmək əvəzinə, bir funksiyanın başlanğıcına da əlavə etmək mümkündür. Bu halda yalnız həmin funksiya müasir qaydada işləyəcək. Lakin, adətən insanlar bu direktivi bütün skript üçün istifadə edirlər.

````warn header="\"use strict\" direktivinin ən üstdə olduğundan əmin olun"
Əmin olun ki, `"use strict"` direktivi skriptinizin ən üst hissəsində yerləşir, əks halda sıx rejim aktivləşməyəcək.

Burada sıx rejim aktiv deyil:

```js no-strict
alert("bəzi kodlar");
// "use strict" aşağıda yerləşdiyindən nəzərə alınmayacaq -- o mütləq ən yuxarıda olmalıdır

"use strict";

// sıx rejim aktiv deyil
```

Sadəcə şərhlər `"use strict"` direktivindən əvvəl yerləşdirilə bilər.
````

```warn header="`use strict` rejimini deaktiv etmək mümkün deyil"
Sıx rejimi deaktiv etmək üçün `"no use strict"` kimi bir direktiv mövcud deyil.

Bir dəfə sıx rejim aktivləşdikdən sonra, geri dönüş mümkün deyil.
```

## Brauzer Konsolu

Gələcəkdə brauzerin konsolundan xüsusiyyətləri test etmək üçün istifadə etdikdə unutmayın ki, konsol susqun olaraq `use strict` rejimini aktivləşdirmir.

Bəzən, `use strict` rejimi ilə fərqlər yaranır və nəticədə yanlış nəticələr əldə edə bilərsiniz.

`key:Shift+Enter` kombinasiyasından istifadə edərək çoxsətirli kod daxil edib `use strict` direktivini ən üstünə yerləşdirin. Məsələn:

```js
'use strict'; <Shift+Enter ilə yeni sətir əlavə edin>
//  ...sizin kod
<İcra etmək üçün Enter>
```

Bu metod əksər brauzerlərdə, məsələn, Firefox və Chrome'da işləyir.

Əgər bu işləməzsə, ən etibarlı yol `use strict` rejimini aşağıdakı nümunədə göstərildiyi kimi istifadə etməkdir:

```js
(function() {
  'use strict';

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
