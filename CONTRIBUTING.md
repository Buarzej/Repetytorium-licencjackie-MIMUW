# Wytyczne dotyczące kontrybucji

**Chcesz pomóc nam rozwijać repetytorium?** Dopisać rozdział, dodać rysunek, poprawić rozwiązanie lub zrobić jeszcze coś innego? Zapoznaj się z poniższymi informacjami! 👇

## 🗝️ Główne założenia

Przy tworzeniu dokumentu trzymamy się dwóch najważniejszych, wysokopoziomowych zasad:

1. Repetytorium jest tworzone **wyłącznie pod klucz egzaminu licencjackiego**, a nie z całego rozkładu materiału! Jeśli jakiś temat nie jest wspomniany w [zagadnieniach do egzaminu][requirements] lub na podstawie archiwalnych zadań można wywnioskować, że się on nie pojawia, to nie ma sensu umieszczać go w części teoretycznej.

2. Docelowy styl językowy dokumentu **różni się** od stylu, którym pisane są różne publikacje naukowe czy skrypty do przedmiotów. Publikacja jest wzorowana na repetytoriach maturalnych i to właśnie do ich stylu chcemy się dostosować: treść jest pisana prostszymi słowami, jak dla uczniów szkół średnich; pomijane są nieistotne dowody; część teoretyczna składa się z pełnych akapitów tłumaczących intuicję lub rozumowanie przyczynowo-skutkowe, a nie idąca od twierdzenia, przez lematy, do kolejnych twierdzeń.

> [!TIP]
> Jeszcze nie wszystkie rozdziały są w pełni dostosowane do drugiej wspomnianej tu zasady, ale najlepiej odzwierciedlają ją rozdziały z **rachunku prawdopodobieństwa, baz danych, programowania współbieżnego** i **matematyki dyskretnej**. Warto w pierwszej kolejności zapoznać się z nimi, żeby wyczuć styl językowy, o jakim tu wspominamy.

## 🗂️ Układ dokumentu

- Każdy rozdział znajduje się w osobnym pliku w katalogu `rozdziały` (np. `rozdziały/analiza_matematyczna.tex`).
- Lista rozdziałów jest zgodna z aktualnymi [zagadnieniami do egzaminu][requirements], przy czym nie ma rozdziałów poświęconych przedmiotom:
	- Wstęp do programowania (zagadnienia stąd są umieszczone w innych rozdziałach, głównie w *Algorytmach i strukturach danych*)
	- Inżynieria oprogramowania (brak zadań dotyczących IO w archiwalnych egzaminach)

### Układ rozdziału

- Każdy rozdział składa się z **sekcji** (`\section`), będących konkretnymi, wydzielonymi tematycznie częściami materiału. Dla przykładu, podziałem *Matematyki dyskretnej* na sekcje może być np. teoria liczb, teoria grafów, kombinatoryka, funkcje tworzące itd.
- Pojedyncza sekcja może składać się z **podsekcji** (`\subsection`), np. sekcja *Teoria grafów* może zawierać podsekcje: podstawowe pojęcia, cykle Eulera i Hamiltona, planarność itd.

### Układ pojedynczej sekcji

- Na początku **nazwa sekcji** (`\section{Nazwa}`).
- Cała treść sekcji to **część teoretyczna** – istotne, żeby nie była zbyt długa i nie zagłębiała się we wszystkie szczegóły.  Ma tylko **przybliżyć najważniejsze koncepty** i przypomnieć zasady działania różnych rzeczy. W miarę dobrą intuicją, jak bardzo streszczony powinien być materiał, jest [ta notatka z *Programowania współbieżnego*](https://drive.google.com/file/d/1uXtmLBMIz4NsdsGUeBw0uWAQerDOgUyB/view?usp=share_link).
- Najważniejsze zagadnienia powinny być **pogrubione** (`\textbf{}`, w Overleafie wystarczy zaznaczyć tekst i nacisnąć Ctrl/Cmd + B). Najważniejsze wzory matematyczne powinny być **zaznaczone na fioletowo** (`\purple{}`), jako że nie da się ich pogrubić. Dłuższe teksty, które pogrubione wyglądają zbyt przytłaczająco, także można **zaznaczyć na fioletowo**.
- Starajmy się umieszczać jak najwięcej **przykładów** przy zagadnieniach teoretycznych:
    
    ```latex
    \begin{example}
    	Ta treść pojawi się w ramce z przykładem.
    \end{example}
    ```
    
- Jeśli jakiś rodzaj zadania pojawia się w archiwalnym zbiorze zadanek **często** (w naszym przypadku: przynajmniej dwukrotnie) i można stwierdzić, że jest on **typowy**, warto umieścić w treści sekcji **ramkę *To było na egzaminie***, zawierającą przykładowe zadanie tego typu i pełne rozumowanie stojące za jego rozwiązaniem:
    
    ```latex
    \begin{exam}
    	Polecenie do zadania
    	\answers{Odpowiedź A}{Odpowiedź B}{Odpowiedź C}
    	
    	Rozwiązanie zadania, wraz z wyszczególnieniem poprawnych odpowiedzi.
    \end{exam}
    ```
    
- W razie potrzeby w treści sekcji można umieścić znacznik oddzielający **podsekcję** (`\subsection{Nazwa}`).
	> [!CAUTION]
	> Nie umieszczamy pierwszej podsekcji **tuż po** rozpoczęciu sekcji! Zamiast tego dobrą praktyką jest umieszczenie akapitu, który wprowadzi czytelnika do tematu, na przykład:

	```latex
    \section{Ciągły rozkład prawdopodobieństwa}
    
	% W tym miejscu unikamy \subsection!
	
	Dla dyskretnych zmiennych losowych mieliśmy (...)
	A co byłoby, gdyby (...)?
	W takiej sytuacji mamy do czynienia z ciągłym rozkładem prawdopodobieństwa.
	
	\subsection{Ciągłe zmienne losowe}
	(...)
    ```
- **Na końcu** sekcji umieszczony jest **zbiór zadań** tematycznie z nią związanych. Zadania będą automatycznie odpowiednio ponumerowane, są wrzucone makra, które za to odpowiadają.
    
    ```latex
    \begin{problems}
    	\prob Polecenie do zadania 1.
    	\answers{Odpowiedź A}{Odpowiedź B}{Odpowiedź C}
    
    	\prob Polecenie do zadania 2.
    	\answers{Odpowiedź A}{Odpowiedź B}{Odpowiedź C}
    
    	(…)
    \end{problems}
    ```

Przykładowa treść pojedynczej sekcji:
```latex
% Nazwa sekcji
\section{Ciągłość funkcji}

% Część teoretyczna z pogrubieniami najważniejszych zagadnień
Powiemy, że $a$ jest \textbf{punktem skupienia} zbioru $A \subset \RR$ wtedy i tylko wtedy, gdy istnieje ciąg $(a_n) \subset A - \{a\}$, taki że $a_n \to a$.

% Każde ważne zagadnienie staramy się zilustrować przykładami
\begin{example}
	0 jest jedynym punktem skupienia zbioru $A = \{\frac{1}{n} \ : \ n \in \NN\}$.
\end{example}

(…) % dalszy ciąg teorii

% Sekcja może zawierać tematyczne podsekcje dla lepszego porządku
\subsection{Granica funkcji}

Niech $a$ będzie punktem skupienia $A \subset \RR$ i weźmy funkcję $f : A \to \RR$. \textbf{Granicę funkcji} możemy zdefiniować na dwa sposoby:
(…)

% Ramka „To było na egzaminie” z najbardziej typowymi zadaniami i sposobem ich rozwiązania
\begin{exam}
	Ciąg, którego $n$-ty wyraz zadany jest wzorem $\sqrt{n^2+(-1)^n}-n$
	\answers{jest monotoniczny}{jest rozbieżny}{jest nieograniczony}

	Aby stwierdzić, czy ciąg jest monotoniczny, zauważamy, że (…)
\end{exam}

(…)

% Sekcja jest zwieńczona zbiorem archiwalnych zadań pasujących do jej tematu
\begin{problems}
	\prob Ciąg, którego $n$-ty wyraz zadany jest wzorem $\frac{2010^n - n^{2010}}{2^{n^2}-2010^n}$,
  \answers{jest zbieżny}{ma granicę równą $-1$}{ma granicę równą 0}

	\prob (…)
	\answers (…)

	(…)
\end{problems}

% Rozwiązania zadań nie są umieszczone tutaj, ale hurtowo na końcu rozdziału
```

## 🟠 Aktualny status dokumentu

Pierwsza wersja repetytorium powstała w roku 2023 i bazuje na zagadnieniach programowych z tego właśnie roku. Od tego czasu studia licencjackie z informatyki na MIM-ie przeszły zmianę programową, a co za tym idzie - zmianę [zagadnień do egzaminu licencjackiego][requirements]:
- W niemal każdym z przedmiotów **przeredagowana została lista zagadnień**. Czasem nie wpływa to w żaden sposób na materiał, który jest już zawarty w repetytorium, a czasem materiał nieco się zmienia - coś jest dodane, a coś usunięte.
- Układ rozdziałów w repetytorium jest ściśle powiązany z przedmiotami obowiązkowymi, których dotyczy rozkład zagadnień programowych na egzaminie. Tutaj również zaszło kilka zmian:
	- usunięto *Semantykę i weryfikację programów*, *Bezpieczeństwo systemów komputerowych* oraz *IPP i blok JNP*
	- dodano *Wstęp do uczenia maszynowego*
	- zmieniono *Systemy operacyjne* na *Architekturę komputerów i systemy operacyjne*

> [!NOTE]
> Ponieważ repetytorium jest skonstruowane pod klucz archiwalnych zadań z egzaminów licencjackich, powyższe zmiany nie wpływają znacząco na sens obecnie zawartej treści.

### 💡 Lista potrzebnych zmian

- Zmiana **podstawy programowej** na początku każdego rozdziału na aktualną - obecna jest nieaktualna.
- Spisanie zadań z większej liczby [dostępnych egzaminów licencjackich][exams] do odpowiednich miejsc dokumentu (lista egzaminów, z których już spisano zadania, znajduje się poniżej).
- Utworzenie rozdziału *Wstęp do uczenia maszynowego*.
- Przeredagowanie wybranych rozdziałów bądź ich części (szczegóły poniżej w sekcji *Status poszczególnych rozdziałów*).

### Archiwalne zadania zawarte w dokumencie

Jako że jedynie **niewielka część poprzednich egzaminów jest [oficjalnie udostępniana][exams]**, zadania zawarte obecnie w repetytorium bazują w większości na dobrowolnych pracach archiwizacyjnych poprzednich pokoleń studentów (spisujących zadania z pamięci po napisanym egzaminie). Poniższa lista zawiera egzaminy, z których zadania zostały spisane i posegregowane do odpowiednich miejsc w repetytorium:
- **2023, częściowo** (patrz: notka poniżej)
- **2022** (I termin)
- **2021** (I termin)
- **2020** (I termin)
- **2020** (zdalny, na Moodle)
- **2019** (I termin)
- **2018** (I termin)
- **2012** (I termin)
- **2010** (I termin)
- **2010** (próbny)

Dodatkowo, zadania z I terminu z roku *2023* są umieszczone wyłącznie rozdziałach z **rachunku prawdopodobieństwa, baz danych, programowania współbieżnego** i **matematyki dyskretnej**. Pozostałe zadania należy spisać i umieścić je w odpowiednich miejscach w repetytorium.

### Status poszczególnych rozdziałów

Niektóre rozdziały wciąż wymagają większych lub mniejszych zmian. Mniejsze z nich zawarliśmy w dokumencie jako **przypisy redakcji** umieszczone w czerwonych ramkach lub jako czerwony tekst.

> [!TIP]
> Jeśli chcesz pomóc nam poprawić którąś z rzeczy oznaczą przypisem redakcji, w kodzie LaTeX-owym oznaczyliśmy każdą z nich komentarzem `% TODO` i ewentualnym dodatkowym komentarzem.

Większe zmiany wypisaliśmy w poniższej tabeli. Kilka uwag:
- tabela nie uwzględnia mniejszych zmian (są one oznaczone bezpośrednio w repetytorium jako przypisy redakcji oraz w plikach LaTeX-owych jako `% TODO`),
- jako *docelowy styl językowy* będziemy odnosić się tu do stylu wspomnianego w sekcji *Główne założenia*.

| Rozdział | Status |
| --- | --- |
| Analiza matematyczna | 🔴 Część teoretyczną w znacznej większości należy poprawić, znacząco odbiega od docelowego stylu |
| Geometria z algebrą liniową | 🟠 Sekcje 2.1-2.3 są napisane zgodnie z docelowym stylem językowym, pozostałe trzeba przeredagować |
| Podstawy matematyki | 🟠 Materiał jest w porządku, potrzeba dodać sporo więcej przykładów i przeredagować całość do docelowego stylu |
| Matematyka dyskretna | 🟢 Brak potrzebnych większych zmian |
| Rachunek prawdopodobieństwa | 🟢 Brak potrzebnych większych zmian |
| Algorytmy i struktury danych | 🔴 Część teoretyczna w dużej mierze chaotyczna, niezrozumiała i z niskiej jakości rysunkami, potrzebne gruntowne przeredagowanie |
| Języki, automaty i obliczenia | 🟠 Materiał jest w porządku, potrzeba jedynie delikatnie przeredagować całość do docelowego stylu |
| Bazy danych | 🟢 Brak potrzebnych większych zmian |
| Programowanie współbieżne | 🟢 Brak potrzebnych większych zmian |
| Metody numeryczne | 🔴 Część teoretyczna w dużej mierze chaotyczna, potrzebne gruntowne przeredagowanie |
| Programowanie obiektowe | 🟠 Materiał jest w porządku, potrzeba dodać sporo więcej przykładów i delikatnie przeredagować całość do docelowego stylu |
| Systemy operacyjne | 🟠 Materiał jest w porządku, potrzeba przeredagować całość do docelowego stylu |
| Aplikacje WWW | 🟠 Materiał jest w porządku, potrzeba delikatnie przeredagować całość do docelowego stylu |
| Sieci komputerowe | 🔴 Część teoretyczna w dużej mierze chaotyczna, potrzebne gruntowne przeredagowanie |

<!-- Linki -->
[requirements]: https://www.mimuw.edu.pl/media/uploads/cms-files/cms-file-zalacznik-zagadnienia-na-egzamin-licencjacki_zFbTxiH.pdf
[exams]: https://www.mimuw.edu.pl/pl/rekrutacja/archiwalne-egzaminy-wstepne-na-informatyke-ii-stopnia/