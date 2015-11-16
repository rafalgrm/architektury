# architektury
dodać do aplikacji

Team COSOMOS w 2013 roku przeniósł z powodzeniem dwa projekty na architekturę MIC. Z kolaboracją z Intelem, udało się przenieść m.in kod symulujący
ewolucje ścian domenowych, które postawały we wczesnym Wszechświecie (magnetycznych zaburzeń symetrii).
Kod był początkowo zrównoleglony przy użyciu czystego OpenMP tak by móc działać na kolejnych generacjach komputera COSMOS.
Rozwiązania testowane były poza systemem przy użyciu Intel Xeon E5-4650L oraz dwóch kart Xeon Phi 5110P. Sockety Xeon Phi okazały się być 2x szybsze. 
Po dość prostych modyfikacjach algorytmu kod został zrefaktorrowany tak by zajmował mniej pamięci, był bardziej zwektoryzowany i bardziej cache-friendly.
Po trzech tygodniach pracy kod został przyspieszony o 5.51x na 2 Xeonach i o 17x na Xeon Phi. Obecnie kod przenoszony jest tak by mógł uzywać wielu MICów w celu
przygotowania się do największej symulacji domain walls. Największą innowacją było stworzenie dense, symmetric, real eigensolver for the UV2000 co pozwoliło lepiej korzystać z dzeilonej pamięci
w architekturze SMP niż w gotowych implementacjach

Ostatnio komputer COSMOS przy użyciu ulepszonych algorytmów zdiagonalizowal macierz 130,000^2 wprzy użyciu 14 wezlow w 4.5 godziny. 
To samo uzywajac ScaLAPACK zajelo 7 godzin. Powstal z tego odrebny projekt, ktory jest obecnie rozwijany wykorzystujac 15TB pamieci wspoldzielonej!

http://www.ctc.cam.ac.uk/news/140108_newsitem.php
