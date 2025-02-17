# Kod Strukturu

İlk öyrənəcəyimiz mövzu, kodun bloklarını inşa etməkdir.

## İfadələr

İfadələr sintaksis konstruksiyaları və əmrlərdir ki, müəyyən əməliyyatlar yerinə yetirir.

Biz artıq alert('Salam, Dünya!') ilə bir ifadə görmüşük, ki, bu da bizə "Salam, Dünya!" mesajını göstərir.

Kodumuzda istədiyimiz qədər ifadə ola bilər. İfadələr bir-birindən "nöqtəli vergül"lərlə ayrıla bilər.

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

Sətir sonunda bir çox hallarda nöqtəli vergül buraxıla bilər.

Bu da işləyəcək:

```js run no-beautify
alert('Salam')
alert('Dünya')
```

Burada JavaScript interpretatoru sətir sonunu "örtülü" nöqtəli vergül kimi qəbul edir. Bu proses [avtomatik nöqtəli vergül daxil edilməsi (automatic semicolon insertion)](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) adlanır.

**Əksər hallarda yeni sətir nöqtəli vergül əlavə edildiyini ifadə edir. Amma "əksər hallarda" "hər zaman" demək deyil!**

Müəyyən hallar var ki, yeni sətir nöqtəli vergül anlamına gəlmir. Məsələn:

```js run no-beautify
alert(3 +
1
+ 2);
```

<<<<<<< HEAD
Bu kodun nəticəsi `6` olacaq, çünki, JavaScript interpretatoru burada nöqtəli vergül daxil etmir. JavaScript üçün intuitiv olaraq aydındır ki, əgər sətir `+` (üstəgəl) simvolu ilə bitirsə, bu "natamam ifadə"dir və nöqtəli vergül tələb olunmur. Bu halda kod gözlənildiyi kimi işləyir.
=======
The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an "incomplete expression", so a semicolon there would be incorrect. And in this case, that works as intended.
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

**Amma müəyyən hallar da var ki, JavaScript belə hallarda nöqtəli vergülü avtomatik əlavə edə bilmir və nəticədə xəta yaranır.**

Belə hallarda xətaları tapmaq və düzəltmək olduqca çətin ola bilər.

````smart header="Xəta üçün bir nümunə"
Əgər belə bir xətaya konkret nümunə görmək istəyirsinizsə, bu kodu yoxlayın:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

<<<<<<< HEAD
İndilik `[]` (kvadrat mötərizələr) və `forEach` haqqında düşünməyə ehtiyac yoxdur. Onları daha sonra öyrənəcəyik. Hazırda sadəcə kodun nəticəsinə diqqət edin: bu kod əvvəlcə `1`, daha sonra `2` göstərir.

İndi kodun əvvəlinə bir `alert` əlavə edək və onu nöqtəli vergülsüz bitirək:

```js run no-beautify
alert("Xəta baş verəcək")
=======
No need to think about the meaning of the brackets `[]` and `forEach` yet. We'll study them later. For now, just remember the result of running the code: it shows `Hello`, then `1`, then `2`.

Now let's remove the semicolon after the `alert`:

```js run no-beautify
alert("Hello")
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

[1, 2].forEach(alert);
```

<<<<<<< HEAD
İndi bu kodu işə salsaq, yalnız ilk `alert` mesajı görünəcək və daha sonra xəta ilə üzləşəcəyik!

Amma əgər `alert` ifadəsindən sonra nöqtəli vergül əlavə etsək, hər şey yenidən qaydasında olacaq:
```js run
alert("Hər şey qaydasındadır.");
=======
The difference compared to the code above is only one character: the semicolon at the end of the first line is gone.

If we run this code, only the first `Hello` shows (and there's an error, you may need to open the console to see it). There are no numbers any more.
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

That's because JavaScript does not assume a semicolon before square brackets `[...]`. So, the code in the last example is treated as a single statement.

<<<<<<< HEAD
İndi "Hər şey qaydasındadır." mesajından sonra `1` və `2` görünür.


Nöqtəli vergülün olmadığı variantda xəta JavaScript'in kvadrat mötərizədən əvvəl nöqtəli vergülü avtomatik əlavə edə bilməməsindən qaynaqlanır.

Beləliklə, nöqtəli vergül avtomatik olaraq əlavə edilmədiyindən, ilk nümunədəki kod tək ifadə kimi qəbul olunur. JavaScript mühərriki kodu belə görür:

```js run no-beautify
alert("Xəta baş verəcək")[1, 2].forEach(alert)
```

Amma kod iki ayrı ifadə olmalı idi, tək deyil. Bu halda birləşmə səhv baş verir və nəticədə xəta yaranır. Bu problem digər hallarda da yarana bilər.
=======
Here's how the engine sees it:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

Looks weird, right? Such merging in this case is just wrong. We need to put a semicolon after `alert` for the code to work correctly.

This can happen in other situations also.
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a
````

Əgər ifadələr sətirlərlə ayrılıbsa, onların arasına nöqtəli vergül qoymağı tövsiyə edirik. Bu qayda JavaScript cəmiyyəti tərəfindən geniş şəkildə qəbul olunub. Yenidən bir də qeyd edək ki, nöqtəli vergülləri çox vaxt buraxmaq -- *mümkündür*. Lakin, xüsusilə yeni başlayanlar üçün, nöqtəli vergüllərdən istifadə etmək daha təhlükəsizdir.

## Şərhlər [#code-comments]

Zaman keçdikcə proqramlar daha mürəkkəb hala gələ bilər. Bu zaman kodun nə etdiyini və niyə olduğunu izah edən *şərhlər* əlavə etmək lazım olur.

Şərhləri skriptin istənilən yerində yerləşdirmək olar. Onlar kodun icrasına təsir etmir, çünki, JavaScript mühərriki onları sadəcə nəzərə almır.

**Təksətirlik şərhlər iki ardıcıl slash (`//`) ilə başlayır.**

Sətirin qalan hissəsi şərh hesab olunur. Şərhlər ayrıca bir sətri tuta bilər və ya bir ifadəni izləyə bilər.

Məsələn:
```js run
// Bu şərh ayrıca bir sətirdə yerləşir
alert('Salam');

alert('Dünya'); // Bu şərh ifadədən sonra yerləşir
```

**Çoxsətirli şərhlər bir slash (`/`) və asterisk (`*`) ilə başlayır <code>/&#42;</code> və bir asterisk (`*`) və slash (`/`) ilə bitir <code>&#42;/</code>.**

Məsələn:

```js run
/* İki mesaj ehtiva edən bir nümunə.
Bu çoxsətirli bir şərhdir.
*/
alert('Salam');
alert('Dünya');
```

Şərhlərin məzmunu JavaScript mühərriki tərəfindən nəzərə alınmadığı üçün, əgər kodu <code>/&#42; ... &#42;/</code> içərisində yerləşdirsək, o icra olunmayacaq.

Bəzən kodun müəyyən bir hissəsini müvəqqəti olaraq söndürmək üçün şərhlərdən istifadə etmək faydalıdır:

```js run
/* Kodu deaktiv edirik
alert('Salam');
*/
alert('Dünya');
```

<<<<<<< HEAD
```smart header="Qısayollardan istifadə edin!"
Əksər redaktorlarda bir kod sətrini təksətirlik şərh etmək üçün `key:Ctrl+/` qısayolundan, çoxsətirli şərhlər üçün isə (kodun bir hissəsini seçib) `key:Ctrl+Shift+/` kombinasiyasından istifadə edə bilərsiniz. Mac istifadəçiləri, sözügedən kombinasiyalardan istifadədə key:Ctrl əvəzinə key:Cmd klavişiylə cəhd edə bilərlər.
=======
```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a
```

````warn header="İç-içə şərhlər dəstəklənmir!"
`/*...*/` içərisində başqa bir `/*...*/` şərhi yerləşdirilə bilməz.

Belə bir kod xəta ilə nəticələnir:

```js run no-beautify
/*
  /* İç-içə şərh ?!? */
*/
alert('Dünya');
```
````

Kodunuzu şərh etməkdən çəkinməyin.

Şərhlər ümumi kodun ölçüsünü artırır, lakin bu problem deyil. Bir çox alət kodu "production server"da, yəni istehsal serverində yayımlamadan əvvəl kiçildir. Bu prosesdə şərhlər silinir və işlək skriptlərdə yer almır. Buna görə də şərhlərin istehsal serverinə heç bir mənfi təsiri yoxdur.

Daha sonra bu dərslikdə [Kod keyfiyyəti](<info:code-quality>) adlı bir fəsil olacaq. Bu fəsil daha yaxşı şərhlər yazmaq barədə əlavə 
məsləhətlər verəcək.