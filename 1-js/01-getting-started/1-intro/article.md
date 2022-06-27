# JavaScript-ə giriş

<<<<<<< HEAD
Gəlin JavaScript-in niyə belə xüsusi olduğuna, onunla nələr edə biləcəyimizə və onun hansı texnologiyalarla qaynayıb qarışdığına bir nəzər yetirək.
=======
Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

## JavaScript nədir?

<<<<<<< HEAD
_JavaScript_ ilkin olaraq _"web səhifələri canlandırmaq"_ üçün yaradılmışdır.
=======
*JavaScript* was initially created to "make web pages alive".
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

Bu dilə yazılmış proqramlar _skriptlər_ adlandırılır. Bu skriptlər, birbaşa web səhifənin HTML-inin içərisində yazıla və səhifə yükləndikcə icra oluna bilər.

Skriptlər əvvəlcədən heç bir hazırlıq, kompilyasiya və s. mərhələlərə ehtiyac olmadan, adi mətn şəklində yazıla və təqdim edilə bilər.

Bu baxımdan, JavaScript, [Java](<https://en.wikipedia.org/wiki/Java_(programming_language)>) adlandırılan, lakin çox vaxt onunla qarışıq salınan dildən olduqca fərqlidir.

```smart header="Bəs onda niyə <u>Java</u>Script?"

JavaScript yaradılan vaxtlarda, ilkin olaraq "LiveScript" adlandırılmışdır. Lakin sonradan Java-nın məhşurluğu və digər səbəblərdən dolayı onu Java-nın "kiçik qardaşı" kimi qələmə vermək qərara alınmışdı.

Buna baxamayaraq sonradan JavaScript öz spesifikasiyaları olan ([ECMAScript](http://en.wikipedia.org/wiki/ECMAScript)), tamamilə müstəqil bir dilə çevrildi və artıq Java ilə uzaqdan yaxından heç bir əlaqəsi yoxdur.

```

Günümüzdə isə, JavaScript tək brauzer mühitində deyil, serverdə və [JavaScript mühərriki](https://en.wikipedia.org/wiki/JavaScript_engine) olan istənilən bir qurğuda işləyir.

Brauzerin daxilində "JavaScript virtual maşını" adlı bir mühərrik mövcuddur.

Müxtəlif mühərriklərin müxtəlif kodadları var. Misalçün:

<<<<<<< HEAD
- [V8](<https://en.wikipedia.org/wiki/V8_(JavaScript_engine)>) -- Chrome və Operada.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefoxda.
- [Chakra](<https://en.wikipedia.org/wiki/Chakra_(JScript_engine)>) -- Microsoft Edgedə
- [JavaScriptCore](https://en.wikipedia.org/wiki/WebKit#JavaScriptCore) -- Safaridə (WebKit) və s.

Yuxarıdakı terminləri yadda saxlamağınız tövsiyyə olunur çünki, bu cür terminlər developer məqalələrində çox istifadə olunur. Nümunə üçün onu deyə bilərik ki, kimsə sizə "filan xüsusiyyət V8-də dəstəklənir" deyəndə, o dəqiqə biləcəksiniz ki, Chrome və Opera (bir də gördünüz MS Edge) bu xüsusiyyəti dəstəkləyir.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome, Opera and Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "JavaScriptCore", "Nitro" and "SquirrelFish" for Safari, etc.

The terms above are good to remember because they are used in developer articles on the internet. We'll use them too. For instance, if "a feature X is supported by V8", then it probably works in Chrome, Opera and Edge.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

```smart header="Bəs bu mühərriklər necə işləyir?"

Düzünü desək, bu mühərriklər olduqca mürəkkəbdir lakin əsaslar sadədir:

1. Əvvəlcə skript oxunulur, token-lərə ayrılır və parse edilir
2. Yaradılmış token-lərdən [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree) qurulur
3. Həmin tree-dən [bytecode](https://en.wikipedia.org/wiki/Bytecode) generasiya olunur
4. Bytecode isə maşın koduna çevrilərək icra olunur

Təbii ki, mühərrikin işi bununla bitmir. Hər bir mərhələdə müəyyən optimallaşdırmalar aparılır və skriptlər icra olunduqca optimallaşdırma üçün məlumatlar toplanılır. Bunun vasitəsilə daha süərtli maşın kodları generasiya olunur.
```

## JavaScript brauzer mühitində nələrə qadirdir?

Müasir JavaScript olduqca təhlükəsiz proqramlaşdırma dilidir. O, ilkin olaraq sadəcə brauzer mühitində işləmək üçün yaradıldığı üçün yaddaşa və ya CPU-ya birbaşa müdaxilə imkanı vermir.

Lakin JavaScript-in imkanları onun icra olunduğu mühitdən asılı olaraq dəyişir. Misalçün, [Node.js](https://wikipedia.org/wiki/Node.js) ilə JavaScript faylları oxuya/yaza, şəbəkə sorğuları və s. edə bilər.

Brauzer daxilində isə, JavaScript web səhifə ilə bağlı demək olar ki, hər şeyi edə bilir.

Bunlara misal olaraq:

- SƏhifəyə yeni HTML-in əlavə edilməsi və hazırkı kontentin dəyişdirilməsi.
- Mouse klik, key press və s. kimi istifadəçi tərəfindən tətiklənən eventlərə reaksiya vermək.
- Şəbəkə üzərindən sorğular göndərmək, fayllar endirmək, upload etmək ( [AJAX](<https://en.wikipedia.org/wiki/Ajax_(programming)>) və [COMET](<https://en.wikipedia.org/wiki/Comet_(programming)>) texnologiyaları vasitəsilə).
- Cookie-lərlə işəmək, ziyarətçilərə müxtəlif mesajlar göstərmək və ya suallar vermək.
- İstifadəçi tərəfdə (client-side) məlumatlar saxlamaq və s.

Və digər şeyləri göstərmək olar.

## Bəs JavaScript brauzer daxilində nələri EDƏ BİLMİR?

İstifadəçinin təhlükəsizliyini təmin etmək üçün, JavaScript-in brauzerdəki funksionallıqları limitlidir.

<<<<<<< HEAD
Bu cür limitlərə aşağıdakılar daxildir:
=======
JavaScript's abilities in the browser are limited for the sake of a user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

- Hər hansı bir web səhifədəki JavaScript sizin sərt diskinizdəki ixtiyari faylları yarada, silə, dəyişə və ya icra edə bilməz. Onun sizin əməliyyat sisteminin funksiyalarına bir başa çıxışı yoxdur.

<<<<<<< HEAD
  Müasir brauzerlər fayllarla işləməyə imkan yaradır lakin bu əməliyyat `<input>` etiketi vasitəsilə sayta fayl yükləməkdən başqa bir şeyə imkan yaratmır.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

  Bununla bərarbər, brauzer sizə kamera və mikrofon kimi cihazlarlə işləmək imkanı yaradır lakin bu əməliyyatları istifadəçinin bir başa icazəsi olmadan etmək qeyri-mümkündür. Yəni evdə hər hansı bir işlə məşğul olanda kimsə sizi hansısa web səhifədən izləyə bilməz, bunun üçün siz brauzerə icazə verməlisiniz.

- Fərqli pəncərələr və tablar normalda bir-biri haqqında heç nə bilmirlər. Əgər, siz JavaScript-i istifadə edərək, başqa bir pəncərə açsanız, bu halda açdığınız pəncərə və cari pəncərə fərqli mənbələrdəndirsə (fərqli domen adı, fərqli protokol və ya port) bir pəncərənin digər pəncərəyə heç bir çıxışı yoxdur.

  Bu eyni mənbə siyasəti adlandırılır (Same Origin Policy). Yalnız hər iki səhifə müəyyən protokol üzərindən razılaşdığı halda bir-birinin resurslarından istifadə edə bilərlər.

  Digər mahdudlaşdırmalar kimi, bu da istifadəçinin güvənliyi üçündür. Hər hansı `http://qeyrimüəyyənbirsayt.com` saytı digər pəncərədə açılmış `http://gmail.com` saytından məlumat götürə bilməməlidir. Əks halda halımız yaxşı olmaz.

![](limitations.svg)

Bu cür məhdudiyyətlər sadəcə brauzer daxilində mövcuddur, daha öncə də qeyd etdiyimiz kimi JavaScript-in imkanları mühitə görə dəyişir.

## JavaScript-i unikal edən nədir?

Aşağıdakılar, JavaScript-i unikal edən ən az üç şeydir:

```compare
<<<<<<< HEAD
+ HTML/CSS ilə tam inteqrasiya.
+ Sadə şeylər sadəliklə icra olunur.
+ Əksər brauzerlər tərəfindən dəstəklənir və defolt olaraq aktivdir.
=======
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Supported by all major browsers and enabled by default.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede
```

Bu üç xüsusiyyəti özündə birləşdirən yegənə texnologiya JavaScript-dir.

Məhz bu səbəbdən, JavaScript unikaldır və ən çox yayılmış proqramlaşdırma dillərindəndir.

Yeri gəlmişək, onu da qeyd etmək lazımdır ki, JavaScript ilə mobil tətbiqlər və serverlər də yarada bilərsiniz.

## JavaScript "üzərində" dillər

JavaScript-in sintaksisi hamının ehtiyaclarını ödəmir. Müxtəlif insanlar, müxtəlif funksionallıqlar tələb edir.

Təbii ki, bu normaldır, çünki layihələr və tələblər hamı üçün fərqlidir.

Son zamanlarda, JavaScript-ə çevrilən (transpiled) bir çox dillər meydana gəlmişdir. Onlar, yalnız development mühitində fərqli funksionallıqlar irəli sürür lakin, daha sonra brauzerdə işləyə bilmək üçün JavaScript-ə çevrilməlidir.

Belə dillərə nümunə olaraq aşağıdakıları göstərmək olar:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) JavaScript üçün "Sintaktik şəkərdir"(syntactic sugar) və daha qısa və anlaşıqlı sintaksis ortaya qoyur. Adətən Ruby developerlər onu sevir.
- [TypeScript](http://www.typescriptlang.org/) JavaScript-ə strict type sistemi əlavə edir və development zamanı bəzi bugların qarşısını alır, çox vaxt performansda da qazandırır. TypeScript Microsoft tərəfindən yaradılmışdır və maintain edilir.
- [Flow](http://flow.org/) həmçinin strict type sistemi əlavə edir lakin başqa yol ilə. Facebook tərəfindən yaradılmışdır.
=======
- [CoffeeScript](https://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](https://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](https://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

Təbii ki, belə dillər daha çoxdur. Lakin bu dilləri başa düşmək üçün əvvəlcə JavaScript-i tam anlamaq şərtdir.

## Xülasə

<<<<<<< HEAD
- JavaScript ilkin olaraq yalnız brauzerlər üçün yaradılmış, lakin sonradan başqa mühitlərdə də istifadə olunmağa başlamışdır.
- Günümüzdə JavaScript HTML və CSS ilə tam inteqrasiya oluna bilər, geniş yayılmış unikal bir proqramlaşdırma dilidir.
- JavaScript-ə çevrilən və yeni funksionallıqlar təqdim edən bir çox dillər mövcuddur. Bu dillərdən bəzilərinə nəzər salmaq tövsiyyə olunur. Misalçün, JavaScript-i tam başa düşdükdən sonra TypeScript-dən başlaya bilərsiniz.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language, fully integrated with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede
