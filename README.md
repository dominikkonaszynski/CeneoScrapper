# CeneoScrapper

## Kod produktu do testów
84514582

## Algorytm pobierania opinii o produkcie z serwisu ceneo.pl
1. Wysłanie żądania dostępu do strony internetowej z opinii o produkcie
2. Jeżeli operacja zakończy się powodzeniem, wyodrębnienie z kodu strony opinii o produkcie
3. Dla każdej opinii wyodrębnanie z kodu HTML poszczególnych składowych i przypinanie ich do elementów złożomej struktury danych
4. Jeśli istnieje kolejna strona z opiniami, przejście do niej i powtórzenie dla niej kroków 1-4
5. Zapisanie wyników do bazy danych

## Struktura opinii w serwisie ceneo.pl
|Składowe|Zmienna|Selektor|
|--------|-------|--------|
|Opinia|Review|div.js_product-review:not(.user-post--highlight)|
|Identyfikator opinii|Review_ID|['data-entry-id']|
|Autor|Author|span.user-post__author-name| 
|Rekomendacja|Recommendation|span.user-post__author-recomendation > em|
|Liczba gwiazdek|Stars|span.user-post__score-count|
|Treść opinii|Content|div.user-post__text|
|Lista zalet|Pros|div.review-feature__item--positive|
|Lista wad|Cons|div.review-feature__item--negative|
|Ile osób uznało opinię za przydatną|Useful|button.vote-yes > span|
|Ile osób uznało opinię za nieprzydatną|Useless|button.vote-no > span|
|Data wystawienia opinii|Post_date|span.user-post_published > time:nth-time:nth-of-type(1)['datetime']|
|Data zakupu produktu|Purchase_date|span.user-post_published > time:nth-of-type(2)['datetime']|