# Drukarka3D-manual
Opis korzystania z drukarki 3D koła i konfiguracji niezbędnego oprogramowania.

W drukarce używana jest płytka [RUMBA](http://www.reprap.org/wiki/RUMBA)

# Potrzebne programy
- program do modelowania 3D     (tworzy model)
- slicer                        (tworzy ścieżki narzędzia na podstawie modelu)
- kontroler druku lub karta SD  (przekazuje polecenia do wykonania maszynie)
- [sterownik drukarki](http://www.reprap.org/wiki/File:RRD_RUMBA_TAURINO_DriverSetup.zip) dla Windowsa

## Modelowanie 3D
Każdy z programów używanych później w pracy z drukarką 3D przyjmuje jako model pliki STL, dlatego swój model najlepiej wyeksportować do tego formatu.  
Edycja plików STL jest mówiąc delikatnie kłopotliwa, dlatego wszelkie zmiany najlepiej nanosić jeszcze w programie do modelowania.  
Jeżeli chcemy drukować model z jak najmniejszą ilością materiału podporowego i z jak największą szansą na udany wydruk to trzeba:
- przewidzieć jak największą powierzchnię styku modelu ze stołem drukarki w czasie drukowania (dla stabilności i uproszczenia slice'owania)
- nie stosować ścian odchylonych o więcej niż 45 stopni od pionu (większe odchylenia wymagają podparcia wydruku w czasie druku)
- zadbać, by otwory w modelu były albo odrobinę mniejsze niż planowane i rozwiercić je w wydruku lub zostawić tylko otwory-piloty
- pamiętać przy wymiarowaniu, że zarówno ABS jak i PLA kurczą się po wydruku (ABS ma większą temperaturę druku, przez co w porównaniu z PLA więcej się kurczy).

## Slicing
Do slicingu można użyć różnych programów. Do tej pory w kole używaliśmy Slic3r oraz Cura przy czym Slic3r ma znacznie więcej możliwości konfiguracji, a Cura jest zintegrowana z kontrolerem druku i pozwala na zrobienie slicingu i rozpoczęcie druku na podłączonej drukarce w kilku kliknięciach.  
Najwięcej problemu może sprawiać dobranie konfiguracji slicera do drukowanego modelu oraz drukarki.  
Podstawowe parametry w konfiguracji:

|Parametr|Wartość|
|---|---|
|Wymiar X|195mm|
|Wymiar Y|180mm|
|Wymiar Z|~190mm (lepiej nieco mniej wstawić)|
|Średnica dyszy|0,4mm aktualnie, mamy dostępne inne|
|Średnica filamentu|~1,75mm (najlepiej zmierzyć w kilku miejscach na szpuli)|
|Prędkość druku|50-60mm/s|
|Prędkość ruchów ustawczych|jak druku (ew. + 10mm/s)|
|Wypełnienie modelu|zazwyczaj wystarcza ~20%, zależy od modelu i zastosowania|
|Temperatura stołu|zależna od materiału, dla PLA zazwyczaj w zakresie 0-50 stopni, ABS 90-115 stopni|
|Temperatura ekstrudera|zależna od materiału, dla PLA zazwyczaj 160-200 stopni, ABS 200-230 stopni|
|Długość retrakcji|poniżej 1mm - E3DV6 ma bardzo mały melt zone dzięki czemu ma krótkie retrakcje|

## Wydruk
Przy drukowaniu z kontrolerem druku trzeba podłączyć drukarkę do komputera przez USB i podłączyć się do odpowiedniego portu szeregowego kontrolerem druku. Płytka nie wykrywa się domyślnie pod Windowsem, dlatego trzeba zainstalować paczkę sterowników.  

Baud połączenia: 115200.

Większość kontrolerów druku pozwala po podłączeniu się do drukarki poruszać jej osiami, zadawać temperatury oraz ręcznie podawać polecenia [G-Code](http://marlinfw.org/meta/gcode/).  
Większość z tych rzeczy można zrobić ręcznie z poziomu drukarki dzięki interfejsowi z ekranem.

Jako program będący tylko kontrolerem druku z wygodnym sterowaniem ręcznym drukarką można użyć [Pronterface](http://www.pronterface.com/) - Pythonowy program który na Windowsie nie wymaga instalacji i jest rozprowadzany w formie .zip ze wszystkim, co do drukowania modeli potrzebne (ma starszą wersję Slic3ra w paczce).

Jako część przygotowania do druku trzeba pokryć stół drukarki papierową taśmą (dla lepszego przyklejenia się wydruku do stołu i ułatwionego sprzątania), wypoziomować stół roboczy (tak, by w całej powierzchni dysza ekstrudera na wysokości Z=0.00 pozwalała przesunąć pod sobą najcieńszy szczelinomierz/kartkę papieru z małym oporem) oraz w przypadku wydruków w ABS pokryć powierzchnię taśmy klejem biurowym (w sztyfcie) dla maksymalnej adhezji.
Warto również przed wydrukiem nagrzać stół do docelowej temperatury tak, by nie trzeba było długo czekać po naciśnięciu "drukuj".
