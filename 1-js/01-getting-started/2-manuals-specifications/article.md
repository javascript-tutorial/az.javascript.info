# Manual və standartlar

Bu kitab sizin dil ilə tanışlığınıza və onu tədricən öyrənməyinizə yönəlmiş bir dərslikdir. Lakin dilin əsasları ilə tam tanış olduqdan sonra artıq başqa mənbələrə də ehtiyac duyacaqsınız. Gəlin bu cür mənbələrlə tanış olaq.

<<<<<<< HEAD
## Spesifikasiyalar
=======
This book is a *tutorial*. It aims to help you gradually learn the language. But once you're familiar with the basics, you'll need other resources.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff

[ECMA-262 standartları](https://www.ecma-international.org/publications/standards/Ecma-262.htm) JavaScript haqqında ən dərin, detallı və formal məlumatları ehtiva edir. Başqa sözlə desək, dili təyin edir.

Lakin bu spesifikasiyalar çox formal olduğu üçün bəzən anlaşılması çətin ola bilər. Spesifikasiyalar, JavaScript haqqında tapa biləcəyiniz ən güvənli və dəqiq məlumat mənbəyidir, hərçənd günlük istifadə üçün deyil.

Spesifikasiyanın hər il yeri versiyası yayımlanır. Ən son versiyası ilə [burada](https://tc39.es/ecma262/) tanış ola bilərsiniz.

<<<<<<< HEAD
ECMA-262 standartlarına il boyunca yeni təkliflər verilir, bu təkliflər bir neçə mərhələdən keçdikdən sonra dilə əlavə olunur (standartlaşdırlır). Ən son təkliflər və "demək olar ki standartlaşdırılmış" (stage 3 proposals) xüsusiyyətlər ilə [burada](https://github.com/tc39/proposals) tanış ola bilərsiniz.
=======
A new specification version is released every year. Between these releases, the latest specification draft is at <https://tc39.es/ecma262/>.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff

Bununla bərabar, əgər JavaScripti brauzer daxilində istifadə edirsinizsə bunun üçün başqa standartlar mövcuddur. Bu barədə dərsliyin [ikinci hissəsində](info:browser-environment) danışacağıq.

<<<<<<< HEAD
## Manuallar
=======
Also, if you're developing for the browser, then there are other specifications covered in the [second part](info:browser-environment) of the tutorial.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff

- **MDN (Mozilla) JavaScript Reference**, nümunələr və digər məlumatlarla tanış ola biləcəyiniz başqa bir mənbədir. MDN, spesifik funksiya, obyektlər, metodlar və s. haqqında dərin məlumat əldə etmək və nümunələrlə tanış olmaq üçün əla yerdir.

<<<<<<< HEAD
  Elə indi bu keçiddən istifadə edib baxmağınız tövsiyyə olunur: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.

  Keçidə daxil olduqdan sonra sizin üçün axtardığınız şeyi tapmaq bir az çətin ola bilər. Bu səbəbdən, çox vaxt Google-da axtarış etmək daha əlverişli olar bilər. Misalçün, deyək ki, `parseInt` funksiyası haqqında ətraflı məlumat almaq istəyirsiniz, bunun üçün <https://google.com/search?q=MDN+parseInt> kimi axtarış edə bilərsiniz.

* **MSDN** – JavaScript (JScript deyək) və Microsoft-a məxsus digər şeylər haqqında məlumat toplaya biləcəyiniz əla mənbədir. Əgər Internet Explorer-ə xas bir şeylə bağlı məlumat almaq istəsəniz elə bura baxın: <http://msdn.microsoft.com/>.

  Və təbii ki, sadə bir internet axtarışından da yararlana bilərsiniz. Misalçün, "RegExp MSDN" və ya "RegExp MSDN jscript".

## Brauzer dəstəyi və uyğunluq cədvəlləri

JavaScript iknişafda olan bir dil olduğu üçün müntəzəm olaraq yeni xüsusiyyətlər əlavə olunur.
=======
- **MDN (Mozilla) JavaScript Reference** is the main manual with examples and other information. It's great to get in-depth information about individual language functions, methods etc.

    You can find it at <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.

Although, it's often best to use an internet search instead. Just use "MDN [term]" in the query, e.g. <https://google.com/search?q=MDN+parseInt> to search for the `parseInt` function.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff

Bu cür xüsusiyyətlərin müxtəlif brauzerlər və engine-lər tərəfindən nə dərəcədə dəstəkləndiyini öyrənmək üçün aşağıdakı resurslardan istifadə edin:

- <http://caniuse.com> - hər bir xüsusiyyətə görə brauzer dəstəyini göstərir. Misalçün, kriptokrafik funksiyaların hansı brauzerlər tərəfindən dəstəkləndiyini görmək üçün belə bir axtarış edə bilərsiniz: <http://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - dildəki xüsusiyyətlərin hansı brauzer, engine və s. tərəfindən dəstəklənib dəstəklənmədiyini göstərən böyük bir cədvəldir.

Bütün bu resurslar, dil haqqında müəyyən detallar onların nə dərəcədə dəstəklənib dəstəklənmədiyi və s. kimi dəyərli məlumatlarla zəngin olduğu üçün real iş mühitində çox işinizə yaraya bilər.

<<<<<<< HEAD
Onları yadda saxlamağınız və detallı məlumat üçün onlara istinad etməyiniz vacibdir.
=======
- <https://caniuse.com> - per-feature tables of support, e.g. to see which engines support modern cryptography functions: <https://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - a table with language features and engines that support those or don't support.

All these resources are useful in real-life development, as they contain valuable information about language details, their support, etc.

Please remember them (or this page) for the cases when you need in-depth information about a particular feature.
>>>>>>> ea7738bb7c3616bb51ff14ae3db2a2747d7888ff
