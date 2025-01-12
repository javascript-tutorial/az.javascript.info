# Müasir mod, "use strict"

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

````warn header="Ensure that \"use strict\" is at the top"
Please make sure that `"use strict"` is at the top of your scripts, otherwise strict mode may not be enabled.

Strict mode isn't enabled here:

```js no-strict
alert("some code");
// "use strict" below is ignored--it must be at the top

"use strict";

// strict mode is not activated
```

Only comments may appear above `"use strict"`.
````

```warn header="There's no way to cancel `use strict`"
There is no directive like `"no use strict"` that reverts the engine to old behavior.

Once we enter strict mode, there's no going back.
```

## Browser console

For the future, when you use a browser console to test features, please note that it doesn't `use strict` by default.

Sometimes, when `use strict` makes a difference, you'll get incorrect results.

You can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:

```js
'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

It works in most browsers, namely Firefox and Chrome.

If it doesn't, the most reliable way to ensure `use strict` would be to input the code into console like this:

```js
(function() {
  'use strict';

  // ...your code...
})()
```

## Always "use strict"

We have yet to cover the differences between strict mode and the "default" mode.

In the next chapters, as we learn language features, we'll note the differences between the strict and default modes. Luckily, there aren't many and they actually make our lives better.

For now, it's enough to know about it in general:

1. The `"use strict"` directive switches the engine to the "modern" mode, changing the behavior of some built-in features. We'll see the details later in the tutorial.
2. Strict mode is enabled by placing `"use strict"` at the top of a script or function. Several language features, like "classes" and "modules", enable strict mode automatically.
3. Strict mode is supported by all modern browsers.
4. We recommended always starting scripts with `"use strict"`. All examples in this tutorial assume strict mode unless (very rarely) specified otherwise.
