# Salam, dünya!

Dərsliyin bu hissəsində JavaScript dilinin özündən danışılır.

Lakin, skriptləri icra etmək üçün bizə işlək mühit lazımdır. Bu kitab onlayn olduğundan bu skriptləri icra etmək üçün brauzer daha yaxşı seçimdir. Sizin fərqli mühitə (Node.js kimi) keçmək istədikdə brauzerə xas əmrlərin (`alert` kimi) üzərində çox vaxt xərcləməməniz üçün biz bu əmrləri çox az işlədəcəyik. Dərsliyin [sonrakı bölməsində](/ui) brauzerdə JavaScript haqqında danışacağıq.

Gəlin ilk olaraq skripti səhifəyə qoşaq. Server mühitlərində (Node.js kimi) skripti `"node my.js"` formalı əmr ilə icra edə bilərsiniz.


## "script" təqi

<<<<<<< HEAD
`<script>` təqindən istifadə edərək JavaScript proqramlarını HTML sənədinin istənilən yerinə əlavə etmək olar.
=======
JavaScript programs can be inserted almost anywhere into an HTML document using the `<script>` tag.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

Məsələn:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Skriptdən öncə...</p>

*!*
  <script>
    alert( 'Salam, dünya!' );
  </script>
*/!*

  <p>...Skriptdən sonra.</p>

</body>

</html>
```

```online
Yuxarıdakı qutunun yuxarı sağ küncündə yerləşən "Play" düyməsini tıklayaraq bu nümunəni icra edə bilərsiniz.
```

Brauzer `<script>` təqini emal edən kimi təqdə olan JavaScript kodu avtomatik icra olunacaq.


## Modern markap

`<script>` təqinin indiki zamanda çox az işlədilən, amma köhnə kodlarda tapa biləcəyiniz bir neçə atributları var.

<<<<<<< HEAD
`type` atributu: <code>&lt;script <u>type</u>=...&gt;</code>
: Köhnə HTML standartı olan HTML4-də skript təqinin `type` atributunun olması vacib idi. Bu atributun dəyəri adətən `type="text/javascript"` idi. Bu artıq lazım deyil. Əlavə olaraq, modern HTML standartında bu atributun mənası tam dəyişmişdir. İndi, bu atribut JavaScript modulları üçün işlədilə bilər. Biz modullar haqqında bu dərsliyin digər bölməsində danışacağıq.
=======
The `type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>
: The old HTML standard, HTML4, required a script to have a `type`. Usually it was `type="text/javascript"`. It's not required anymore. Also, the modern HTML standard totally changed the meaning of this attribute. Now, it can be used for JavaScript modules. But that's an advanced topic, we'll talk about modules in another part of the tutorial.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

`language` atributu: <code>&lt;script <u>language</u>=...&gt;</code>
: Bu atributda skriptin dili göstərilirdi. JavaScript-in əsas dil olduğundan bu atributun artıq mənası qalmayıb. Bu atributdan istifadə etmək lazım deyil.

Skriptlərdən öncə və sonra kommentlər.
: Çox köhnə kitab və ya məqalələrdə `<script>` təqlərində aşağıdakı şəkildə olan kommentlər tapa bilərdiniz:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Modern JavaScript-də bu hiylədən istifadə edilmir. Bu kommentlər `<script>` təqini emal edə bilməyən köhnə brauzerlərdə JavaScript kodunu gizlətmək üçün lazım idi. Sonuncu 15 ildə dərc olunmuş brauzerlərdə bu problemin olmadığından bunun ilə çox köhnə kodları müəyyənləşdirə bilərsiniz.


## Kənar skriptlər

Çoxlu JavaScript kodu olduqda bu kodu ayrı faylda saxlamaq mümkündür.

Skript faylları HTML-ə `src` atributu ilə qoşulurlar:

```html
<script src="/path/to/script.js"></script>
```

Burada, `/path/to/script.js` dəyəri saytın kökündən absolut yol ilə skript faylına istinad edir. Əlavə olaraq, cari səhifəyə nisbi yerləşən fayla da istinad etmək olar. Məsələn, `src="script.js"` dəyəri `"script.js"` faylının cari direktoriyada olması deməkdir.

Biz, skriptin mənbəsini tam URL ilə də təyin edə bilərik. Məsələn:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Bir neçə skripti qoşmaq üçün bir neçə təqdən istifadə edin:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Qayda olaraq yalnız çox sadə skriptləri HTML faylında saxlayın. Daha mürəkkəb skriptləri fərqli fayllarda saxlayın.

Skripti kənarda saxladıqda brauzer, faylı yükləyib öz [kəşində](https://en.wikipedia.org/wiki/Web_cache) saxlayacaq.

Eyni skripti yükləyən digər səhifələr skripti yükləmək əvəzinə kəşdən oxuyacaq. Bu səbəbdən skript faylı yalnız bir dəfə yüklənəcək.

Bu, trafiki azaldaraq səhifəni tezləşdirəcək.
```

````warn header="`src` atributu təyin edildikdə skriptin kontenti sayılmır."
Tək `<script>` təqinin həm `src` atributu, həm də daxili kodu ola bilməz.

Aşağıdakı kod işləməyəcək:

```html
<script *!*src*/!*="file.js">
  alert(1); // src təyin edilib deyə kontent sayılmır
</script>
```

Biz ya kənar skripti yükləyən `<script src="…">` təqi, ya da kod ilə `<script>` təqini təyin edə bilərik.

Yuxarıdakı nümunənin işləməsi üçün skriptləri ayrı-ayrı təqlərə ayırın:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Xülasə

- JavaScript kodunu səhifəyə əlavə etmək üçün `<script>` təqindən istifadə edə bilərik.
- `type` və `language` atributlarından istifadə etmək vacib deyil.
- Kənar faylda yerləşən skriptləri `<script src="path/to/script.js"></script>` təqi ilə yükləmək mümkündür.


Brauzer skriptləri və onların veb səhifə ilə interaksiyası haqqında öyrənilməli daha çox məlumat var. Lakin, dərsliyin bu hissəsinin JavaScript dilinə həsr olunduğu üçün biz brauzerə xas tətbiqlərə fokuslanmayacağıq. Biz JavaScript kodunu icra etmək üçün brauzerdən istifadə edəcəyik. Brauzerdən istifadə etdikdə icra olunan skriptləri onlayn oxumaq olur. Lakin, skriptləri başqa mühitlərdə də icra etmək mümkündür.
