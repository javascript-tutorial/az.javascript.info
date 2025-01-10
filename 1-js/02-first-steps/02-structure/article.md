# Kod Strukturu

İlk öyrənəcəyimiz mövzu kodun əsas elementləridir.

## İfadələr

İfadələr sintaksis konstruksiyaları və əmrlərdir ki, müəyyən əməliyyatlar yerinə yetirir.

Artıq `alert('Salam, dünya!')` ifadəsini görmüşük ki, bu da "Salam, dünya!" mesajını göstərir.

Kodumuzda istədiyimiz qədər ifadə ola bilər. İfadələr nöqtəli vergüllə ayrılır.

Məsələn, burada "Salam, dünya" mesajını iki xəbərdarlıq şəklində ayırmışıq:

```js run no-beautify
alert('Salam'); alert('Dünya');
```

Adətən, ifadələr kodun oxunaqlılığını artırmaq üçün ayrı-ayrı sətirlərdə yazılır:

```js run no-beautify
alert('Salam');
alert('Dünya');
```

## Nöqtəli Vergüllər [#semicolon]

Sətir kəsilməsi mövcud olduqda nöqtəli vergül buraxıla bilər.

Bu da işləyəcək:

```js run no-beautify
alert('Salam')
alert('Dünya')
```

Burada JavaScript interpretatoru sətir sonunu "örtülü" nöqtəli vergül kimi qəbul edir. Bu proses [avtomatik nöqtəli vergül daxil edilməsi (automatic semicolon insertion)](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) adlanır.

**Əksər hallarda yeni sətir bir nöqtəli vergülü nəzərdə tutur. Amma "əksər hallarda" "hər zaman" demək deyil!**

Müəyyən hallar var ki, yeni sətir nöqtəli vergül anlamına gəlmir. Məsələn:

```js run no-beautify
alert(3 +
1
+ 2);
```

Bu kodun nəticəsi `6` olacaq, çünki, JavaScript interpretatoru burada nöqtəli vergül daxil etmir. JavaScript üçün intuitiv olaraq aydındır ki, əgər sətir `+` (üstəgəl) simvolu ilə bitirsə, bu "natamam ifadə"dir və nöqtəli vergül tələb olunmur. Bu halda kod gözlənildiyi kimi işləyir.

**Amma müəyyən hallar da var ki, JavaScript belə hallarda nöqtəli vergülü avtomatik əlavə edə bilmir və nəticədə xəta yaranır.**

Belə hallarda xətaları tapmaq və düzəltmək olduqca çətin ola bilər.

````smart header="Xəta üçün bir nümunə"
Əgər belə bir xətaya konkret nümunə görmək istəyirsinizsə, bu kodu yoxlayın:

```js run
[1, 2].forEach(alert)
```

İndilik `[]` (kvadrat mötərizələr) və `forEach` haqqında düşünməyə ehtiyac yoxdur. Onları daha sonra öyrənəcəyik. Hazırda sadəcə kodun nəticəsinə diqqət edin: bu kod əvvəlcə `1`, daha sonra `2` göstərəcək.

İndi kodun əvvəlinə bir `alert` əlavə edək və onu nöqtəli vergülsüz bitirək:

```js run no-beautify
alert("Xəta baş verəcək")

[1, 2].forEach(alert)
```

İndi bu kodu işə salsaq, yalnız ilk `alert` mesajı görünəcək və daha sonra xəta ilə üzləşəcəyik!

Amma əgər `alert` ifadəsindən sonra nöqtəli vergül əlavə etsək, hər şey yenidən qaydasında olacaq:
```js run
alert("Hər şey qaydasındadır.");

[1, 2].forEach(alert)  
```

İndi "Hər şey qaydasındadır." mesajından sonra `1` və `2` görünür.


Nöqtəli vergülün olmadığı variantda xəta JavaScript'in kvadrat mötərizədən əvvəl nöqtəli vergülü avtomatik əlavə edə bilməməsindən qaynaqlanır.

Beləliklə, nöqtəli vergül avtomatik olaraq əlavə edilmədiyindən, ilk nümunədəki kod tək ifadə kimi qəbul olunur. JavaScript mühərriki kodu belə görür:

```js run no-beautify
alert("Xəta baş verəcək")[1, 2].forEach(alert)
```

Amma kod iki ayrı ifadə olmalı idi, tək deyil. Bu halda birləşmə səhv baş verir və nəticədə xəta yaranır. Bu problem digər hallarda da yarana bilər.
````

Əgər ifadələr sətirlərlə ayrılıbsa, onların arasına nöqtəli vergül qoymağı tövsiyə edirik. Bu qayda JavaScript cəmiyyəti tərəfindən geniş şəkildə qəbul olunub. Yenidən bir də qeyd edək ki, nöqtəli vergülləri çox vaxt buraxmaq -- *mümkündür*. Lakin, xüsusilə yeni başlayanlar üçün, nöqtəli vergüllərdən istifadə etmək daha təhlükəsizdir.

## Comments [#code-comments]

As time goes on, programs become more and more complex. It becomes necessary to add *comments* which describe what the code does and why.

Comments can be put into any place of a script. They don't affect its execution because the engine simply ignores them.

**One-line comments start with two forward slash characters `//`.**

The rest of the line is a comment. It may occupy a full line of its own or follow a statement.

Like here:
```js run
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Multiline comments start with a forward slash and an asterisk <code>/&#42;</code> and end with an asterisk and a forward slash <code>&#42;/</code>.**

Like this:

```js run
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

The content of comments is ignored, so if we put code inside <code>/&#42; ... &#42;/</code>, it won't execute.

Sometimes it can be handy to temporarily disable a part of code:

```js run
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl`.
```

````warn header="Nested comments are not supported!"
There may not be `/*...*/` inside another `/*...*/`.

Such code will die with an error:

```js run no-beautify
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
````

Please, don't hesitate to comment your code.

Comments increase the overall code footprint, but that's not a problem at all. There are many tools which minify code before publishing to a production server. They remove comments, so they don't appear in the working scripts. Therefore, comments do not have negative effects on production at all.

Later in the tutorial there will be a chapter <info:code-quality> that also explains how to write better comments.
