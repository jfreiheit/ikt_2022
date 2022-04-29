# Aktuelle Trends der IKT

Herzlich willkommen zur Veranstaltung **Aktuelle Trends der IKT**! 

### Grober Inhalt

Wir beschäftigen uns dieses Semester mit *Progressive Web Apps (PWA)*. Dieser Begriff ist 2015 bei Google entstanden. Progressive Web Apps bieten installierbare nativen Apps ähnliche Nutzererfahrungen sowohl auf dem Desktop als auch auf dem Smartphone, sind aber Webanwendungen, die im Browser laufen, also zum World Wide Web gehören. Typische Eigenschaften von Progressive Web Apps sind die Einbindung von Kamera und Mikrofon, dem eigenen Standort sowie die Fähigkeit, (zumindest teilweise) offline ausführbar zu sein. 

Nachfolgend der vorläufige Wochenplan (wird eventuell angepasst). Die Vorlesungsvideos finden Sie darunter für die einzelnen Wochen (unter [**Inhalte**](http://freiheit.f4.htw-berlin.de/ikt/#inhalte)).

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) | Abgabe Übung bis | 
|-|-------|--------------------|-------|-----------------|------------------|
| 1. | 04.-08.04.2022 | Einführung und Organisatorisches | - | - | - | 
| 2. | 11.-15.04.2022 | Grundgerüst und Application Manifest | Übung 1 | - | 30.04.2022 | 
| 3. | 18.-22.04.2022 | Service workers | Übung 2 | - | 07.05.2022 | 
| 4. | 25.-29.04.2022 | Promises und Fetch API | Übung 3 | - | 14.05.2022 | 
| 5. | 02.-06.05.2022 | Service workers und Caching | - | - | 21.05.2022 | 
| 6. | 09.-13.05.2022 | Entwicklungsinfrastruktur | Übung 4 | - | 28.05.2022 | 
| 7. | 16.-20.05.2022 | Datenbank und Backend | Übung 5 | - | 04.06.2022 | 
| 8. | 23.-27.05.2022 | Frontend mit Backend-Anbindung | Übung 6 | - | 11.06.2022 | 
| 9. | 30.-03.06.2022 | Caching dynamische Daten mit IndexDB | Übung 7 | - | 18.06.2022 | 
| 10. | 06.-10.06.2022 | Hintergrundsynchronisation | - | Datenbank | - | 
| 11. | 13.-17.06.2022 | Push-Notifikationen | - | Backend | - | 
| 12. | 20.-24.06.2022 | Kamera und Geolocation | - | Backend | - |
| 13. | 27.-01.07.2022 | Wiederholung | - | Frontend | - |
| 14. | 04.-08.07.2022 | Wiederholung | - | Frontend | - |
|  |  |  |  | Abgabe 1.PZ 18.07.2022 | - |
|  |  |  |  | Abgabe 2.PZ 01.10.2022 | - |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen Sie am Ende des Semesters die Lösung Ihrer Semesteraufgabe abgeben. Diese Aufgabe zusammen mit einem Gespräch, das wir über Ihre Lösung führen, wird bewertet. Die Bewertung entspricht dann der Modulnote. 

Die Übungen sind dafür vorgesehen, dass Sie im Semester sukzessive Ihre Lösung erstellen können. Wir beantworten in den Übungen Ihre Fragen und lösen gemeinsam Probleme. Jede Woche gibt es ein Thema, das Sie selbständig durcharbeiten und dann angepasst in Ihre Lösung integrieren können.  

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes **Diskussionsforum** entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese **von Ihnen dort beantwortet** zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht. Außerdem lernen Sie beim Beantworten der Fragen nochmals deutlich mehr. Das wäre super, wenn das klappt!

### Inhalte

Hier sind die Videos aus **2021** verlinkt!!! (auf Wunsch) Der aktuelle Stoff ist aber teilweise abgeändert und angepasst! Insbesondere werden wir 2022 MongoDB als Datenbank verwenden und nicht PostgresQL. Außerdem haben sich wieder einige APIs seit 2021 geändert. 

##### Woche 1 (Grundgerüst)

??? question "Woche 1 - Grundgerüst"

	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=9acae2bf623912843d1298721c67867a&width=720&height=405&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="405" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>


##### Woche 2 (Manifest)

??? question "Woche 2 - Manifest"

	- Diese Woche wird unsere App mithilfe des [Application Manifest](./manifest/#web-app-manifest) **installierbar**. Dazu gibt es folgendes Video: 
		<iframe src="https://mediathek.htw-berlin.de/media/embed?key=247bb388ae29a4d849a3fcff5fae95db&width=720&height=450&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="450" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>



##### Woche 3 (Promises und Fetch API)

??? question "Woche 3 - Promises und Fetch API"

	- Diese Woche betrachten wir den Lebenszyklus eines Service Workers, schauen uns Promises und die Fetch API an. Dazu dieses Video:
		<iframe src="https://mediathek.htw-berlin.de/media/embed?key=71d02c5d395a874c9b2b4821a140dc7f&width=720&height=389&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="389" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>
	- Sourcecode zur Vorlesung am 05.05.2021 (also alt!!!) [hier zum Herunterladen](./files/03_promise.zip)



##### Woche 4 (Caching)

??? question "Woche 4 - Caching"

	- Diese Woche wird die App mithilfe von [Caching](./caching/#caching-mit-service-workern) auch offline nutzbar.
	- Video zur Vorlesung am 12.05.2021
		<iframe src="https://mediathek.htw-berlin.de/media/embed?key=bf498f35fe78e01a22d5fa909d4c4be8&width=720&height=389&autoplay=false&autolightsoff=false&loop=false&chapters=false&related=false&responsive=false&t=0" data-src="" class="iframeLoaded" width="720" height="389" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no"></iframe>
	- Sourcecode zur Vorlesung am 12.05.2021 (also alt!!!) [hier zum Herunterladen](./files/04_caching.zip)



### Semesteraufgabe

Die als Semesteraufgabe zu entwickelnde Webanwendung sollte

1. ein Frontend besitzen (muss nicht mit einem JavaScript-Framework erstellt werden),
2. das Frontend soll responsive sein (wenn nicht, dann *mobile first*!),
3. ein Backend (damit Daten auf dem Server verwaltet werden können), 
4. eine Datenbank zur persistenten Speicherung von Daten (wir verwenden MongoDB, kann aber auch MariaDB, MySQL, PostgresQL oder auch SQLite oder ähnlich In-Apps-Datenbanken sein),
5. installierbar sein,
6. offline nutzbar sein,
7. die IndexedDB verwenden,
8. Hintergrundsynchronisation verwenden,
9. Push-Nachrichten verwenden,
10. die Gelocation API verwenden,
11. die Kamera oder eine andere technische Schnittstelle (z.B. Sensoren, Mikrofon) verwenden.

Von den Punkten 5.-11. sollten 

- 5 für eine 2,0 implementiert sein, 
- 6 für eine 1,7 und 
- 7 für eine 1,3. 
- Ist die Anwendung besonders toll und/oder deployed, kann es auch eine 1,0 werden. 

Bitte erstellen Sie eine aussagekräftige `README.md`-Datei. Die erstellte Anwendung soll präsentiert werden und in einem kurzen Gespräch (15-20min) wird die Implementierung besprochen. 

Hier eine Idee einer Anwendung, eine *Ausgabenverwaltung*:

- installierbare Webanwendung, 
- Formular für die Buchung einer Ausgabe 
	- Datum, 
	- Titel für die Ausgabe, 
	- Betrag, 
	- Foto des Kassenzettels, 
	- evtl. Geolocation des Ausgabeortes
- Übersicht über Ausgaben,
- offline verwendbar, d.h. Ausgabe wird in der IndexedDB gespeichert und erst, wenn wieder online, dann in der Datenbank,
- Push-Benachrichtigung, wenn Ausgabe in der Datenbank gespeichert (Hintergrundsynchronisation), 
- Backend ist zwingend erforderlich (für Speichern und Abrufen der Daten in die und aus der Datenbank),
- MongoDB zur persitenten Datenspeicherung,
- evtl. Nutzerverwaltung zur Verwaltung der eigenen Ausgaben.

Sie können natürlich auch eine eigene Anwendungsidee umsetzen! Viel Spaß und Erfolg!   


