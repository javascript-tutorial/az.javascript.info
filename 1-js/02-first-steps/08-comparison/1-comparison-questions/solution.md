

```js no-beautify
5 > 4 → true
"apple" > "pineapple" → false
"2" > "12" → true
undefined == null → true
undefined === null → false
null == "\n0\n" → false
null === +"\n0\n" → false
```

Səbəblərdən bəziləri:

1. Əlbəttəki, doğru.
2. Lüğət müqayisəsi. `"a"` `"p"`-dən əvvəl gəlir, buna görədə `false`.
3. Yenə lüğət müqayisəsinə görə ilk simvol olan `"2"`, `"1"`-dən böyükdür.
4. `null` və `undefined` bir-birinə bərabərdir.
5. Ciddi bərabərlik ciddidir. Hər iki fərqli növ səhvə gətirib çıxarır.
6. '(4)' kimi, 'null' yalnız 'müəyyən edilməmiş'ə bərabərdir.
7. Müxtəlif növlər `false` verir.
