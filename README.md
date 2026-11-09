Vinted Manager
Vinted Manager to prywatne narzędzie do zarządzania sprzedażą własnych, używanych ubrań przez jedną osobę (sprzedawcę prywatnego). Aplikacja działa lokalnie na komputerze właściciela i nie jest udostępniana innym użytkownikom ani publicznie w internecie.

English summary: Vinted Manager is a private, single-user tool for managing the sale of the owner's own second-hand clothing. It runs locally on the owner's computer and is not offered to third parties.

Do czego służy
prowadzenie magazynu ubrań (zdjęcia, marka, rozmiar, stan, opis, cena, koszt zakupu),
przygotowywanie ogłoszeń na kilka platform sprzedażowych z jednego miejsca,
ewidencja sprzedaży i wyliczanie zysku,
drukowanie etykiet magazynowych.
Integracja z Allegro REST API
Aplikacja korzysta z oficjalnego Allegro REST API wyłącznie w imieniu konta właściciela (jedno konto sprzedającego).

Zakres	Opis
Autoryzacja	OAuth 2.0 — Device Flow; tokeny przechowywane w postaci zaszyfrowanej, odświeżane automatycznie
Kategorie i parametry	GET /sale/matching-categories, GET /sale/categories/{id}/parameters — dobór kategorii i wymaganych parametrów oferty
Zdjęcia	POST /sale/images (upload.allegro.pl) — przesłanie zdjęć własnych produktów
Oferty	POST /sale/product-offers (szkic, status INACTIVE), PATCH /sale/product-offers/{id} (aktualizacja, publikacja, zakończenie), GET /sale/offers?external.id= (ochrona przed duplikatami)
Ustawienia	GET /sale/shipping-rates, GET /me
Zasady działania:

każda publikacja oferty jest ręcznie zatwierdzana przez właściciela — aplikacja nie wystawia ofert automatycznie,
aplikacja nie usuwa ofert; kończenie oferty odbywa się wyłącznie na polecenie właściciela,
przed utworzeniem oferty sprawdzana jest sygnatura (external.id), aby nie powstawały duplikaty,
liczba zapytań jest niewielka (pojedyncze oferty), z ponawianiem zgodnie z nagłówkiem Retry-After przy kodzie 429,
aplikacja nie pobiera ani nie przetwarza danych kupujących poza zakresem potrzebnym do obsługi własnej sprzedaży.
Identyfikacja aplikacji
Zapytania do Allegro REST API są wysyłane z nagłówkiem User-Agent w formacie Vinted Manager/1.0.0 (+adres tej strony), zgodnie z wymaganiami Allegro.

Kontakt
W sprawach dotyczących działania integracji prosimy o kontakt przez zgłoszenie (Issues) w tym repozytorium.

Ta strona zawiera wyłącznie opis aplikacji. Kod źródłowy, dane, zdjęcia i klucze dostępowe nie są publikowane.
