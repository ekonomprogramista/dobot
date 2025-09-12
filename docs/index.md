# OGÓLNE

Środowisko Dobot Lab jest konieczne do programowania robota Magician. To właśnie w nim piszemy kod, który zostanie wgrany do naszego robota. Aby zainstalować środowisko Dobot Lab, przejdź na stronę:  [_https://www.dobot-robots.com/service/download-center_](https://www.dobot-robots.com/service/download-center)_,_ a następnie pobierz dwa wymagane instalatory: **DobotLab Win Local** oraz **DobotLink Win Local**.

**Na dzień pisania dokumentacji zalecana wersja: DobotLab V2.3.4, DobotLink V6.7.4**

**Uwaga!** Do instalacji wymagane są uprawnienia administratorskie.

**Uwaga!** Przy instalowaniu na komputer aplikacji DobotLink mogą wystąpić błędy, które skutkują tym, że wymagany sterownik nie zostanie poprawnie pobrany. Zaobserwować można to wchodząc w menedżer urządzeń – podłączony robot powinien znajdować się w swojej własnej, nowej kategorii w liście. Jeżeli wystąpi błąd instalacji sterownika, należy odinstalować aplikację DobotLink oraz przejść przez instalator ponownie.

---
# ŁĄCZENIE ROBOTA ZE STANOWISKIEM PRACY


Po zainstalowaniu na komputer potrzebnych aplikacji, i upewnieniu się, że działają one poprawnie, możemy przejść do łączenia się z naszym robotem
<ol>
	<li><b>Przed podłączeniem robota upewnij się, że robot jest wyłączony</b>. Włącz go dopiero po uruchomieniu DobotLab – niektóre modele wykrywają się lepiej w tej kolejności</li>
	<li>Ustaw ramię robota w odpowiedniej pozycji - tak aby późniejsze ruchy nie powodowały zacięć oraz aby ustalanie koordynat było łatwiejsze</li>
	<li>
	Uruchom DobotLab i wybierz dowolne laboratorium (np. DobotBlock lub Python
		<ol style="list-style: upper-alpha;">
			<li>Jeżeli wybrałeś laboratorium DobotBlock, kliknij w przycisk łączenia, a w otwartym oknie wybierz port do którego podłączony jest Magician</li>
			<li>Jeżeli wybrałeś laboratorium Python, kliknij na listę rozwijalną po prawej stronie paska nawigacji, i wybierz z listy opcję <b>Magician</b></li>
		</ol>
	</li>
</ol>

---
# LABORATORIUM DOBOTBLOCK


Sukces! Udało Ci się połączyć z robotem – możemy przejść do pracy. DobotLab posiada kilka rodzajów laboratoriów, każdy o innym przeznaczeniu ale o podobnej zasadzie działania.

DobotBlock jest właśnie jednym z nich. Zapewne w szkole podstawowej robiłeś proste programy w Scratchu oparte o wizualne elementy (puzzle) w jakimś określonym porządku. Taki porządek można nazwać algorytmem, czyli listą kroków potrzebnych czynności do osiągnięcia jakiegoś celu. W DobotBlock wygląda to identycznie jak w Scratchu. Z listy kontrolek przeciągamy interesujące nas komponenty.

Tak samo wygląda proces uruchomienia i zatrzymywania kodu – naciskamy ikonkę zielonej flagi lub czerwony sześciokąt.

**Nie zapomnij o inicjalizacji robota dodając blok startowy!**

# LABORATORIUM PYTHON


Laboratorium **Python** w DobotLab pozwala na bardziej precyzyjne i zaawansowane sterowanie robotem Magician. W przeciwieństwie do DobotBlock, nie używamy tutaj „puzzli”, tylko piszemy kod w języku programowania **Python**. To idealna okazja, aby wykorzystać poznane elementy programowania w praktyce!

**Nie musisz znać wszystkich funkcji na pamięć!** W laboratorium Python w DobotLab dostępny jest **przybornik z funkcjami**, który znajduje się po lewej stronie edytora. Wystarczy kliknąć wybraną funkcję z listy – w miejscu kursora w panelu tekstowym pojawi się jej składnia. Dzięki temu możesz łatwo korzystać z dostępnych poleceń bez przeszukiwania dokumentacji zewnętrznej.

Przykładowy program:

```python
from DobotEDU import *

# Ruch ramienia do pozycji startowej (ruch punkt-do-punktu)
magician.ptp(mode=0, x=250, y=0, z=50, r=0)

# Włączenie przyssawki
magician.suction_cup(enable_ctrl=True, enable=True)

# Ruch do pozycji nad obiektem
magician.ptp(mode=0, x=200, y=0, z=0, r=0)

# Powrót do pozycji początkowej
magician.ptp(mode=0, x=250, y=0, z=50, r=0)

# Wyłączenie przyssawki
magician.suction_cup(enable_ctrl=True, enable=False)

```

# LABORATORIUM RYSUNKU I GRAFIKI

Laboratorium rysunku pozwala na konwersję obrazów lub tekstu na trajektorie ruchu robota, tak aby mógł je narysować na powierzchni za pomocą uchwytu z długopisem lub pisakiem.

To doskonałe środowisko dla początkujących – nie wymaga umiejętności programowania. Rysunki generowane są automatycznie na podstawie wgranych grafik lub wpisanego tekstu.

Jak korzystać z laboratorium?
<ol>
	<li>
		Wybierz opcję:
		<ul>
			<li>Importuj obraz używając przycisku <b>Otwórz</b>. (<b>Uwaga!</b> Przy wybraniu grafiki o innym formacie niż <i>.svg</i> konieczna będzie konwersja, co może skutkować gorszym efektem końcowym)</li>
			<li>Wpisz tekst w polu tekstowym i kliknij przycisk <b>Dodaj</b></li>
		</ul>
	</li>
	<li>
		Ustaw upragnione parametry grafiki, m.in:
		<ul>
			<li>Rozmiar</li>
			<li>Pozycja na podglądzie</li>
			<li>Styl tekstu</li>
		</ul>
	</li>
</ol>

Wskazówki przed rysowaniem:
<ul>
	<li>Używaj obrazów o wysokim kontraście – najlepiej czarno-białych.</li>
	<li>Robot rysuje tylko ścieżki – nie "drukuje" kolorów.</li>
</ul>