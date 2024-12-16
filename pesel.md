# Walidacja PESEL

## Zadanie

Przyjmijmy że mamy taki oto formularz na stronce internetowej:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Test PESEL</title>
    </head>
    <body>
        <div>
            <h2>Formularz</h2>
            <form>
                <div>
                    <label for="firstName">Imię</label>
                    <input type="text" name="firstName" id="firstName"/>
                </div>
                <div>
                    <label for="lastName">Nazwisko</label>
                    <input type="text" name="lastName" id="lastName"/>
                </div>
                <div>
                    <label for="pesel">PESEL</label>
                    <input type="text" name="pesel" id="pesel"/>
                </div>
                <button type="button">Weryfikuj</button>
                <button type="reset">Wyczyść</button>
            </form>
        </div>
        <div>
            <h2>Rezultat walidacji</h2>
            <div id="results">...</div>
        </div>
    </body>
</html>
```

Gdy wciśniemy przycisk "Weryfikuj", w polu rezultat walidacji powinna wyświetlić się treść typu:

```
Imię: Jan (lub np "brak" - jeśli imię nie ma 1 znaku alfanumerycznego)
Nazwisko: Kowalski (lub np "brak" - jeśli nazwisko nie ma 1 znaku alfanumerycznego)
PESEL: prawidłowy
Data urodzenia: 1970-01-01
```

Jeśli nr PESEL nie jest prawidłowy, to wyświetlamy informację "nieprawidłowy" i nie próbujemy wyświetlać daty.

Dodatkowo, na pola nakładamy pewne ograniczenia

### Imię

1. Pole wymaga przynajmniej 1 znaku (mogą być cyfry)
2. Pole powinno automatycznie usuwać spacje przed i za imieniem, czyli jeśli ktoś wpisze "  Jan " to formularz powinien w pewnym momencie (Twoja wola kiedy) zamienić wartość na "Jan" 

### Nazwisko

1. Pole wymaga przynajmniej 1 znaku (mogą być cyfry)
2. Pole powinno automatycznie usuwać spacje przed i za nazwiskiem.

### PESEL

1. PESEL powinien składać się dokładnie z 11 cyfr (usuwamy spacje na początku i końcu)
2. PESEL powinien być prawidłowy (sprawdzamy go [algorytmem](https://pl.wikipedia.org/wiki/PESEL#Cyfra_kontrolna_i_sprawdzanie_poprawności_numeru))
3. Data zapisana w NR pesel ma być sprawdzana pod kątem prawidłowości (czyli uodparniamy algorytm na zamianę miejscami cyfr reprezentujących rok i dzień)

## Przydatne linki:

- [String.prototype.trim](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim)
- [parseInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
- [Tworzenie obiektu Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#several_ways_to_create_a_date_object)
- [Zdarzenie blur](https://developer.mozilla.org/en-US/docs/Web/API/Element/blur_event)
- [Zdarzenie click](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event)
- [document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
