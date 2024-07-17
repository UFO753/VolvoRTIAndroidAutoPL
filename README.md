# Volvo RTI AndroidAuto PL
<details><summary>Ostrzeżenie!</summary>Wszelkie modyfikacje wprowadzasz na własną odpowiedzialność. Nie odpowiadam za uszkodzenia mienia podczas prac, jak i również za późniejsze działanie!</details>

Projekt ten jest modyfikacją dla wyświetlacza RTI w volvo, pozwala on na dodanie do twojego samochodu trochę świeżości, jaką jest android auto. Wszystkie jest wyświetlane na oryginalnym wyświetlaczu, nie potrzeba nic ciąć bądź modyfikować w sposób nieodwracalny, wszystkie zmiany w tym projekcie są w pełni odwracalne.

## Funkcjonalność
- Sterowanie ekranem za pomocą pilota
- Automatyczne uruchomienie AndroidAuto
## Do zrobienia
- Wyjście audio na samochód
- Automatyczne otwieranie i zamykanie ekranu po podłączeniu AndroidAuto
- W moim przypadku to dostarczyć dobre zasilanie do raspberry, obecnie jest zasilane z transmitera
- Zamontować to w porządnym miejscu - leży teraz w schowku
## Potrzebny sprzęt
- Raspberry Pi 3 B+ - można użyć innego, ja zwyczajnie działałem na tym
- Arduino NANO
- Wyświetlacz RTI
- Pilot nawigacji - 30657371
- Jakiś sposób zasilania Raspberry
- Myszka bezprzewodowa/ touchpad
- Jumper wires - najprostszy sposób aby podłączyć się do pinów
- kabel kabel audio-video jack 3.5 w standardzie CTIA - bądź trzeba będzie zbadać wyjście multimetrem.
- Kabel skrętka - bądź coś pokroju jeżeli chcemy gdzieś dalej odejść z raspberry
- Kabel usb - do podłączenia telefonu do raspberry

## Schemat podłączenia


## Źródła
- Projekt kontroli nad RTI https://github.com/TymEK49/RTI_control
- Główna inspiracja https://luuk.cc/p/vD2f/Android_Auto_on_Volvo_RTI
- Crankshaft ale ze zmianą ekranu https://github.com/laurynas/volvo_crankshaft
