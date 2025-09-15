# OGÓLNE

Środowisko Dobot Lab jest konieczne do programowania robota Magician. To właśnie w nim piszemy kod, który zostanie wgrany do naszego robota. Aby zainstalować środowisko Dobot Lab, przejdź na stronę:  [_https://www.dobot-robots.com/service/download-center_](https://www.dobot-robots.com/service/download-center)_,_ a następnie pobierz dwa wymagane instalatory: **DobotLab Win Local** oraz **DobotLink Win Local**.

!!! info "Oprogramowanie"
	Na dzień pisania dokumentacji zalecana wersje oprogramowania: **DobotLab V2.3.4** ; **DobotLink V6.7.4**

!!! warning "Uwaga!"
	Do instalacji wymagane są uprawnienia administratorskie.

!!! warning "Uwaga!"
	Przy instalowaniu na komputer aplikacji DobotLink mogą wystąpić błędy, które skutkują tym, że wymagany sterownik nie zostanie poprawnie pobrany. Zaobserwować można to wchodząc w menedżer urządzeń – podłączony robot powinien znajdować się w swojej własnej, nowej kategorii w liście. Jeżeli wystąpi błąd instalacji sterownika, należy odinstalować aplikację DobotLink oraz przejść przez instalator ponownie.

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