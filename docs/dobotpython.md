# LABORATORIUM PYTHON

Laboratorium **Python** w DobotLab pozwala na bardziej precyzyjne i zaawansowane sterowanie robotem Magician. W przeciwieństwie do DobotBlock, nie używamy tutaj „puzzli”, tylko piszemy kod w języku programowania **Python**. To idealna okazja, aby wykorzystać poznane elementy programowania w praktyce!

**Nie musisz znać wszystkich funkcji na pamięć!** W laboratorium Python w DobotLab dostępny jest **przybornik z funkcjami**, który znajduje się po lewej stronie edytora. Wystarczy kliknąć wybraną funkcję z listy – w miejscu kursora w panelu tekstowym pojawi się jej składnia. Dzięki temu możesz łatwo korzystać z dostępnych poleceń bez przeszukiwania dokumentacji zewnętrznej.

<div style="display:flex; gap:1rem; align-items:flex-start; justify-content:center; flex-wrap:wrap;">
  <img src="https://i.ibb.co/VYKbyKyK/image12.jpg" alt="image1" style="max-width:45%; height:50%;">
</div>

<br>

Przykładowy program:

```python linenums="1"

# version: Python3
# Program z przyssawką, przemieszczający obiekty między dwoma punktami

from DobotEDU import *
floorY1 = -50
floorY2 = -30

magician.motion_params(80, 80)

def GoToPos(pos_x, pos_y, pos_z, mode):
    if mode != 0 and mode != 1 and mode != 2: return
    magician.ptp(mode=mode, x=pos_x, y=pos_y, z=pos_z, r=0)
    
def SuctionHandle(switch):
    magician.set_endeffector_suction cup (enable=True, on-switch)

while True:
    SuctionHandle(False)
    GoToPos(250, 0, 50, 0)
    GoToPos(250, -100, floorY2, 0)
    SuctionHandle(True)
    GoToPos(220, 100, floorY1, 0)
    SuctionHandle(False)
    GoToPos(250, 0, 50, 0)
    GoToPos(250, -100, floorY1, 0)
    SuctionHandle(True)
    GoToPos(220, 100, floorY2, 0)
    SuctionHandle(False)
    GoToPos(250, 0, 50, 0)
    GoToPos(220, 100, floorY2, 0)
    SuctionHandle(True)
    GoToPos (250, 100, floorY1, 0)
    SuctionHandle(False)
    GoToPos (220, 100, floorY1, 0)
    SuctionHandle(True)
    GoToPos (250, 100, floorY2, 0)
    SuctionHandle(False)
```

---