# C# I DOBOT

C# to jeden z popularniejszych języków programowania, który jest szeroko stosowany w aplikacjach desktopowych, webowych oraz w środowiskach automatyki i robotyki. Dzięki bibliotekom i interfejsom API, C# może być używany do programowania robotów, takich jak Dobot.

Dzięki SDK (Software Development Kit) udostępnianemu przez producenta robota, można z łatwością napisać aplikację do kontrolowania robota w C#. W naszej dokumentacji używamy klasy ```Dobot```

--- 

# JAK ZACZĄĆ?

Do rozpoczęcia pracy, potrzebne będzie nam IDE (zalecamy Vistual Studio) i sterownik do portu wirtualnego.

!!! info "Adresy do strony"
    Vistual Studio 2022 [_https://visualstudio.microsoft.com/pl/_](https://visualstudio.microsoft.com/pl/)<br>
    Sterownik CP210x: [_https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads_](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads)

<ol>
    <li>Stwórz nowy projekt - Aplikacja Konsoli (.NET 7.0)</li>
    <li>W zakładce Kompilowanie > Menedżer konfiguracji w polu **Aktywne platformy rozwiązania** kliknij <Nowy...>, następnie wybierz platformę x86 i kopiuj ustawienia z Any CPU</li>
    <li>W polu Konteksty projektu upewnij się że otwarty projekt ma wybraną platformę x86</li>
    <li>Dodaj folder z klasami do obsługi robota</li>
    <li>Upewnij się że w folderze bin/x86/Debug/net7.0 masz wrzucone wszystkie pliki .dll</li>
    <li>Zainstaluj wcześniej wspomniany sterownik</li>
    <li>Podłącz Dobota do komputera dołączonym do zestawu kablem USB</li>
    <li>Ustaw ramię robota w odpowiedniej pozycji - tak aby późniejsze ruchy nie powodowały zacięć oraz aby ustalanie koordynat było łatwiejsze</li>
    <li>Włącz robota, zaczekaj aż dioda na jego podstawie zmieni kolor na zielony</li>
    <li>Używając Menedżera urządzeń, ustal jakiego portu używa Dobot (COM<liczba>)</li>
    <li>Zacznij programować. Aby przekazać kod do Dobota, postępuj w ten sam sposób jak przy uruchamianiu normalnego kodu konsolowego</li>
</ol>

!!! warning "Uwaga!"
    Uważaj! Przed rozpoczęciem prac, zmień przestrzeń nazw (namespace) wszystkich plików *.cs* w folderze CPlusDLL do obsługi DLL. W przeciwnym wypadku nie nawiążesz połączenia z robotem!

!!! info "Program eksperymentalny"
    Praca z Dobotem używając C# jest jeszcze w fazie testowania, pewne funkcje mogą nie działać tak jak powinny, a w dokumentacji mogą być pomyłki

---

# KLUCZOWE METODY

```csharp
/// <summary>
/// Tworzy nową instancję obiektu Dobot, łącząc się z urządzeniem za pomocą podanego portu i prędkości transmisji
/// </summary>
/// <param name="port">Port, do którego urządzenie jest podłączone (np. "COM1").</param>
/// <param name="baudRate">Prędkość transmisji (np. 9600, 115200).</param>
new Dobot(*string port*, *int baudRate*)
```

```csharp
/// <summary>
/// Sprawdza czy udało się nawiązać połączenie
/// </summary>
/// <returns>True, jeśli połączenie zostało nawiązane, false w przeciwnym razie.</returns>
.Connect() <bool>
```

```csharp
/// <summary>
/// Ustawia parametry początkowe robota (konieczne do działania)
/// </summary>
.SetParams()
```

```csharp
/// <summary>
/// Sprawdza i wypisuje alarmy
/// </summary>
.AlarmTest()
```

```csharp
/// <summary>
/// Czyści aktywne alarmy
/// </summary>
.ClearAlarms()
```

```csharp
/// <summary>
/// Zwraca pozycję ramienia
/// </summary>
/// <returns>Enum Pose, który zawiera koordynaty</returns>
.GetPose()
```

```csharp
/// <summary>
/// Ustala prędkość i przyspieszenie dla ruchu PTP (Point to Point)
/// </summary>
/// <param name="velocity">Prędkość</param>
/// <param name="acceleration">Przyspieszenie</param>
.SetPTPSpeed(*float velocity*, *float acceleration*)
```

```csharp
/// <summary>
/// Dodaje do kolejki ruch PTP (Point to Point) do podanych współrzędnych
/// </summary>
/// <param name="style">Styl ruchu (np. 0 - szybki, 1 - dokładny itp.)</param>
/// <param name="x">Współrzędna X docelowego punktu</param>
/// <param name="y">Współrzędna Y docelowego punktu</param>
/// <param name="z">Współrzędna Z docelowego punktu</param>
/// <param name="r">Rotacja</param>
.PTP(*byte style*, *float x,* *float y*, *float z*, *float r*)
```

```csharp
/// Włącza lub wyłącza przyssawkę.
/// </summary>
/// <param name="enable">Jeśli wartość to true, przyssawka zostanie włączona. Jeśli false, przyssawka zostanie wyłączona</param>
.SetSuctionCup(*bool enable*)
```

```csharp
/// <summary>
/// Włącza lub wyłącza chwytak.
/// </summary>
/// <param name="enable">Jeśli wartość to true, chwytak zostanie włączony. Jeśli false, chwytak zostanie wyłączony</param>
.SetGripper(*bool enable*)
```

---

# PRZYKŁADOWY PROGRAM

```csharp
class Program
{
    static void Main(string[] args)
    {
        Dobot robot = new Dobot("COM4", 115200);
        if (!robot.Connect())
        {
            Console.WriteLine("Nie udało się połączyć z Dobotem.");
            return;
        }

        robot.SetParams();
        robot.SetPTPSpeed(30, 30);
        robot.ClearAlarms();
        robot.AlarmTest();
        Thread.Sleep(1000);
        robot.PTP(1, 200, 0, -10, 0);
        robot.SetSuctionCup(true);
        robot.PTP(1, 180, 100, -20, 0);
        robot.PTP(1, 180, 100, -20, 50);
        robot.SetSuctionCup(false);
    }
}
```

