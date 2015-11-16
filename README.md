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

The new eigensolver is currently utilized to great effect in the ExoMol project, which has a complicated SMP 
pipeline which runs on COSMOS. Recently, a 130,000^2 matrix was diagonalised using 14 nodes on COSMOS in 4.5 hours. 
The equivalent using ScaLAPACK took 7 hours. The aim is now to test COSMOS 15TB shared-memory limits by analysing 
650,000^2 matrices, opening up new ExoMol (and other science) frontiers. John Cheng (SGI) has led developments here, 
with collaborative support from James Briggs.

http://www.ctc.cam.ac.uk/news/140108_newsitem.php
