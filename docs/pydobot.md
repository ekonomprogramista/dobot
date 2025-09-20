# BIBLIOTEKA PYDOBOT

***Pydobot*** to niezwykle przydatna biblioteka, która umożliwia sterowanie ramieniem robota Dobot Magician bezpośrednio z poziomu języka Python. Stworzona z myślą o prostocie i dostępności, pozwala na łatwe łączenie się z robotem i wydawanie mu poleceń, bez potrzeby korzystania z jego natywnego oprogramowania.

Biblioteka stanowi pomost między twoim kodem w Pythonie a ramieniem robota, komunikując się z nim przez port szeregowy (USB). Jej kluczowe cechy to:
<ul>
    <li>Prosta instalacja: Można ją zainstalować za pomocą menedżera pakietów pip.</li>
    <li>Intuicyjne metody: Udostępnia łatwe w użyciu funkcje do sterowania ruchem, chwytakiem, czy przyssawką.</li>
    <li>Wsparcie dla różnych systemów: Działa na systemach Windows, macOS i Linux.</li>
</ul>

---

# JAK ZACZĄĆ?

Do rozpoczęcia pracy, potrzebny nam będzie edytor kodu *(zalecamy Visual Studio Code lub PyCharm)*, sterownik do portu wirtualnego oraz oczywiście zainstalowany Python na naszym komputerze.

!!! info "Adresy do stron"
    Visual Studio Code: [_https://code.visualstudio.com/download_](https://code.visualstudio.com/download)<br>
    PyCharm: [_https://www.jetbrains.com/pycharm/download/_](https://www.jetbrains.com/pycharm/download)<br>
    Sterownik CP210x: [_https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads_](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads)<br>
    Python: [_https://www.python.org/downloads/_](https://www.python.org/downloads)<br>

<ol>
    <li>
    Otwórz Terminal i wprowadź następującą komendę instalacyjną
    ```python
    pip install pydobot
    ``` 
    Możesz również zainstalować bibliotekę w konkretnej lokalizacji:
    ```python
    pip install --target=ŚCIEŻKA_FOLDERU pydobot
    ```
    </li>
    <li>Zainstaluj wcześniej wspomniany sterownik</li>
	<li>Podłącz Dobota do komputera dołączonym do zestawu kablem USB</li>
	<li>Ustaw ramię robota w odpowiedniej pozycji - tak aby późniejsze ruchy nie powodowały zacięć oraz aby ustalanie koordynat było łatwiejsze</li>
	<li>Włącz robota, zaczekaj aż dioda na jego podstawie zmieni kolor na zielony</li>
    <li>Zacznij programować. Aby przekazać kod do Dobota, postępuj w ten sam sposób jak przy uruchamianiu normalnego kodu konsolowego</li>
</ol>

---

# KLUCZOWE METODY BIBLIOTEKI

Tworzy instancję robota, łącząc się z danym portem szeregowym
```python
Dobot(port, verbose=False)
```

Zwraca aktualną pozycję robota jako krotkę (x, y, z, r, j1, j2, j3, j4)
```python
.pose()
```

Dodaje do kolejki ruch do podanych współrzędnych. Parametr wait sprawia, że program czeka na zakończenie ruchu
```python
.move_to(x, y, z, r, wait=False)
```

Steruje przyssawką (True/False)
```python
.suck(enable)
```

Steruje chwytakiem (True/False)
```python
.grip(enable)
```

Zmienia prędkość i przyspieszenie ruchu robota
```python
.speed(velocity, acceleration)
```

Dodaje do kolejki czas, który ma upłynąć przez wznowieniem wątku (milisekundy)
```python
.wait(ms)
```

Zamyka połączenie z robotem
```python
.close()
```
<br>
Przykładowy program:

```python linenums="1"
from serial.tools import list_ports

import pydobot

available_ports = list_ports.comports()
port = available_ports[0].device

device = pydobot.Dobot(port=port, verbose=True) # konstruktor

(x, y, z, r, j1, j2, j3, j4) = device.pose()  # pobiera aktualne położenie ramienia robota
print(f'x:{x} y:{y} z:{z} j1:{j1} j2:{j2} j3:{j3} j4:{j4}')

device.move_to(x + 20, y, z, r, wait=False)
device.move_to(x, y, z, r, wait=True)

device.close() # rozłączenie
```
