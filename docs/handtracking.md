# DOBOT I GESTYKULACJA

Sterowanie gestami dłoni to nowoczesne podejście do kontroli ruchów robotów, które można zrealizować w całości z poziomu języka Python. Dzięki wykorzystaniu zwykłej kamerki internetowej oraz bibliotek do analizy obrazu, możliwe jest rozpoznawanie położenia dłoni i przekładanie go na konkretne polecenia ruchu robota.

Python pełni tutaj rolę łącznika pomiędzy systemem rozpoznawania gestów a robotem, umożliwiając intuicyjne i naturalne sterowanie bez konieczności stosowania dodatkowych kontrolerów.

<ul>
    <li>Python oferuje bogaty ekosystem bibliotek, które ułatwiają wykrywanie gestów i ich mapowanie na komendy sterujące.</li> 
    <li>Ruchy dłoni w naturalny sposób przekładają się na działania robota.</li> 
    <li>Możliwość dopasowania gestów do własnych potrzeb i przypisania im różnych funkcji.</li> 
    <li>Rozwiązanie można połączyć z różnymi typami robotów, niezależnie od platformy sprzętowej.</li> 
</ul>

---

# JAK ZACZĄĆ?

Aby rozpocząć przygodę ze sterowaniem robota za pomocą gestów dłoni w Pythonie, wystarczy zwykła kamerka internetowa i kilka popularnych bibliotek. Pierwszym krokiem jest instalacja narzędzi do przetwarzania obrazu, które umożliwiają wykrywanie dłoni i śledzenie jej ruchów. W naszej dokumentacji użyjemy bibioletki **Mediapipe**, **OpenCV** oraz **pyDobot**, który opisaliśmy już na naszej stronie [tutaj](https://ekonomprogramista.github.io/dobot/pydobot/).

<ol>
    <li>
    Otwórz Terminal i wprowadź następującą komendę instalacyjną
    ```python
    pip install opencv-python mediapipe
    ``` 
    </li>
	<li>Podłącz Dobota do komputera dołączonym do zestawu kablem USB</li>
	<li>Ustaw ramię robota w odpowiedniej pozycji - tak aby późniejsze ruchy nie powodowały zacięć oraz aby ustalanie koordynat było łatwiejsze</li>
	<li>Włącz robota, zaczekaj aż dioda na jego podstawie zmieni kolor na zielony</li>
    <li>Zacznij programować. Aby przekazać kod do Dobota, postępuj w ten sam sposób jak przy uruchamianiu normalnego kodu konsolowego</li>
</ol>

!!! warning "Uwaga!"
    Biblioteka **Mediapipe** nie jest dostępna na najnowszą wersję Pythona (3.13), zalecamy używanie wersji 3.11, którą możesz pobrać [tutaj](https://www.python.org/downloads/release/python-3110/).
    
!!! warning "Uwaga!"
    Przy instalacji **Mediapipe** i **OpenCV** mogą wystąpić błędy kompatybilności wersji.
    