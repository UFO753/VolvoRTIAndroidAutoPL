# Volvo RTI AndroidAuto PL
<details><summary>Ostrzeżenie!</summary>Wszelkie modyfikacje wprowadzasz na własną odpowiedzialność. Nie odpowiadam za uszkodzenia mienia podczas prac, jak i również za późniejsze działanie!</details>

Projekt ten jest modyfikacją dla wyświetlacza RTI w volvo, pozwala on na dodanie do twojego samochodu trochę świeżości, jaką jest android auto. Wszystko jest wyświetlane na oryginalnym wyświetlaczu, nie potrzeba nic ciąć bądź modyfikować w sposób nieodwracalny, wszystkie zmiany w tym projekcie są w pełni odwracalne.

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
![Schemat podłączenia sterowania i całej reszty](https://github.com/UFO753/VolvoRTIAndroidAutoPL/blob/main/pics/diagram%20pod%C5%82%C4%85czenia.png?raw=true)
Ważną rzeczą jest aby zbadać multimetrem gdzie mamy dostępne GND i + sygnał wychodzący z wtyczki RCA, pozostałe wtyczki RCA zostają pod wyjście Audio z raspberry - można je odizolować aby nie spowodować zwarcia. 
![Schemat jack dla raspberry pi 3 b+](https://github.com/UFO753/VolvoRTIAndroidAutoPL/blob/main/pics/Model-B-Plus-Audio-Video-Jack-Diagram.png?raw=true)
Z powyższego schematu wychodzi iż interesuje nas pin numer 4 dla + sygnału oraz pin 3 dla GND. 
U mnie wszystko zostało przedłużone przy pomocy skrętki aby schować tymczasowo wszystko w schowku, dodatkowo zastosowałem złącze RCA żeńskie dla wejscia wideo do ekranu. 
U mnie wygląda wszystko w ten sposób: 
![Schowek zdjęcie](https://github.com/UFO753/VolvoRTIAndroidAutoPL/blob/main/pics/IMG_20240717_184416.jpg?raw=true)
![kabelki na środku zdjęcie](https://github.com/UFO753/VolvoRTIAndroidAutoPL/blob/main/pics/IMG_20240717_184500.jpg?raw=true)
## Oprogramowanie
Oprogramowanie do sterowania ekranem zaciągamy z tąd: https://github.com/TymEK49/RTI_control?tab=readme-ov-file
Z kolei za emulator android auto będzie nam służył Crankshaft dostępny pod adresem: https://getcrankshaft.com
#### Ważne, nie wiem jak w waszym przypadku w moim wersja najnowsza miała problem ze starowaniem android auto, cofnięcie się do wersji Alpha-7.4 2021-09-22 naprawiło problem.
System ten jest systemem w pełni niezależnym, instalujemy go za pomocą oprogramowania BalenaEtcher - zaznaczamy zip, kartę pamięci i program już całą resztę ogarnia za nas. 
#### Pierwsze uruchomienie programu wymaga chwili czasu, pójdź w tym czasie/ po kawkę herbatę aby nic nie przeszkodziło dla pierwszego uruchomienia
Po instalacji będziemy musieli metodą prób i błędów dopasować ekran aby nie było czarnych pasków do ookoła, robimy to przy pomocy pliku config.txt znajdującego się na karcie po instalacji. W moim przypadku najlepszy wynik uzyskałem na ustawieniach 
- overscan_left=-19
- overscan_right=-19
- overscan_top=-30
- overscan_bottom=-26

Dodatkowo ustawiłem rozdzielczość na sztywno
- framebuffer_width=1280
- framebuffer_height=720

W zasadzie na tym etapie wystarczy podłączyć wszystko w samochodzie, warto pamiętać o podłączeniu myszki/ touchpada tak aby mieć możliwość jakiej kolwiek nawigacji po androidauto, jako iż ekran RTI nie jest dotykowym ekranem. Po uruchomieniu prezentuje się nam taki ekran. 
![Ekran crankshaft](https://github.com/UFO753/VolvoRTIAndroidAutoPL/blob/main/pics/IMG_20240717_193846.jpg?raw=true)
Rozdzielczość nie powala, ale sam ekran RTI najlepszej rozdzielczości nie ma.
W lewym dolnym rogu jest zębatka, należy wejść do ustawień i włączyć "Show cursor" Tak aby mieć możliwość klikania w android auto, w innym przypadku nawet nie jesteśmy w stanie podłączyć telefonu do android auto.

W zasdzie podejrzewam że dla CarPlay też by się znalazł soft na raspberry. 

## Ciekawostka
Ekran RTI jest tak skonstruowany jeżeli dostanie sygnał analogowy jest w stanie go wyświetlić, nawet xboxa 360 podłączyłem do niego 
https://youtube.com/shorts/qyWzGKkTKGw?feature=share
## Źródła
- Projekt kontroli nad RTI https://github.com/TymEK49/RTI_control
- Główna inspiracja https://luuk.cc/p/vD2f/Android_Auto_on_Volvo_RTI
- Crankshaft ale ze zmianą ekranu https://github.com/laurynas/volvo_crankshaft
