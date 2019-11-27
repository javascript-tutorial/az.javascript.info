# JavaScript-ə giriş

Gəlin JavaScript-in niyə belə xüsusi olduğuna, onunla nələr edə biləcəyimizə və onun hansı texnologiyalarla qaynayıb qarışdığına bir nəzər yetirək.

## JavaScript nədir?

_JavaScript_ ilkin olaraq _"web səhifələri canlandırmaq"_ üçün yaradılmışdır.

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

- [V8](<https://en.wikipedia.org/wiki/V8_(JavaScript_engine)>) -- Chrome və Operada.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefoxda.
- [Chakra](<https://en.wikipedia.org/wiki/Chakra_(JScript_engine)>) -- Microsoft Edgedə
- [JavaScriptCore](https://en.wikipedia.org/wiki/WebKit#JavaScriptCore) -- Safaridə (WebKit) və s.

Yuxarıdakı terminləri yadda saxlamağınız tövsiyyə olunur çünki, bu cür terminlər developer məqalələrində çox istifadə olunur. Nümunə üçün onu deyə bilərik ki, kimsə sizə "filan xüsusiyyət V8-də dəstəklənir" deyəndə, o dəqiqə biləcəksiniz ki, Chrome və Opera (bir də gördünüz MS Edge) bu xüsusiyyəti dəstəkləyir.

```smart header="Bəs bu mühərriklər necə işləyir?"

Düzünü desək, bu mühərriklər olduqca mürəkkəbdir lakin əsaslar sadədir:

1. Əvvəlcə skript oxunulur, token-lərə ayrılır və parse edilir
2. Yaradılmış token-lərdən [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree) qurulur
3. Həmin tree-dən [bytecode](https://en.wikipedia.org/wiki/Bytecode) generasiya olunur
4. Bytecode isə maşın koduna çevrilərək icra olunur

Təbii ki, mühərrikin işi bununla bitmir. Hər bir mərhələdə müəyyən optimallaşdırmalar aparılır və skriptlər icra olunduqca optimallaşdırma üçün məlumatlar toplanılır. Bunun vasitəsilə daha süərtli maşın kodları generasiya olunur.
```

## JavaScript brauzer mühitində nələrə qadirdir?

Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or CPU, because it was initially created for browsers which do not require it.

JavaScript's capabilities greatly depend on the environment it's running in. For instance, [Node.js](https://wikipedia.org/wiki/Node.js) supports functions that allow JavaScript to read/write arbitrary files, perform network requests, etc.

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.

For instance, in-browser JavaScript is able to:

- Add new HTML to the page, change the existing content, modify styles.
- React to user actions, run on mouse clicks, pointer movements, key presses.
- Send requests over the network to remote servers, download and upload files (so-called [AJAX](<https://en.wikipedia.org/wiki/Ajax_(programming)>) and [COMET](<https://en.wikipedia.org/wiki/Comet_(programming)>) technologies).
- Get and set cookies, ask questions to the visitor, show messages.
- Remember the data on the client-side ("local storage").

## What CAN'T in-browser JavaScript do?

JavaScript's abilities in the browser are limited for the sake of the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.

Examples of such restrictions include:

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS system functions.

  Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like "dropping" a file into a browser window or selecting it via an `<input>` tag.

  There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).

- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

  This is called the "Same Origin Policy". To work around that, _both pages_ must agree for data exchange and contain a special JavaScript code that handles it. We'll cover that in the tutorial.

  This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.

- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.

![](limitations.svg)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugin/extensions which may ask for extended permissions.
`

## What makes JavaScript unique?

There are at least _three_ great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Support by all major browsers and enabled by default.
```

JavaScript is the only browser technology that combines these three things.

That's what makes JavaScript unique. That's why it's the most widespread tool for creating browser interfaces.

That said, JavaScript also allows to create servers, mobile applications, etc.

## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are _transpiled_ (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and auto-converting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.

There are more. Of course, even if we use one of transpiled languages, we should also know JavaScript to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
