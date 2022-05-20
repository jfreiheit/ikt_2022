# Geolocation-API

## Geolocation-API

Die Geolocation-API wird von allen Browsern unterstützt (sogar Internet Explorer). Es gibt viele Dokumentationen darüber, z.B. [hier](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation), [hier](https://developer.mozilla.org/de/docs/Web/API/Geolocation_API) und [hier](https://developers.google.com/maps/documentation/geolocation/overview). Die Verwendung ist recht einfach. 

In der `index.html` haben wir uns bereits einen Button erstellt, für den wir "nur noch" das `click`-Ereignis behandeln müssen. 


=== "public/index.html"
	```html linenums="83"
    <div class="input-section">
        <button class="mdl-button mdl-js-button mdl-button--colored" type="button" id="location-btn">Location</button>
        <div class="mdl-spinner mdl-js-spinner is-active" id="location-loader"></div>
    </div>
	```

Zunächst vereinfachen wir uns in der `feed.js` wieder den Zugriff auf den Button und den Spinner (Loader) und erstellen noch eine globale Variable `fetchedLocation`:


=== "public/src/js/feed.js"
	```js linenums="1" hl_lines="14-16"
	let shareImageButton = document.querySelector('#share-image-button');
	let createPostArea = document.querySelector('#create-post');
	let closeCreatePostModalButton = document.querySelector('#close-create-post-modal-btn');
	let sharedMomentsArea = document.querySelector('#shared-moments');
	let form = document.querySelector('form');
	let titleInput = document.querySelector('#title');
	let locationInput = document.querySelector('#location');
	let videoPlayer = document.querySelector('#player');
	let canvasElement = document.querySelector('#canvas');
	let captureButton = document.querySelector('#capture-btn');
	let imagePicker = document.querySelector('#image-picker');
	let imagePickerArea = document.querySelector('#pick-image');
	let base64String = '';
	let locationButton = document.querySelector('#location-btn');
	let locationLoader = document.querySelector('#location-loader');
	let fetchedLocation;

	```

und wir setzen den `Loader` in der `feed.css` auf unsichtbar:


=== "public/src/js/feed.css"
	```css linenums="23" hl_lines="1"
	#create-post #pick-image, #create-post #location-loader {
	    display: none;
	}
	```

`create-post #pick-image` stand dort schon, wir haben nur noch den Selektor `#create-post #location-loader` hinzugefügt.


Wir fügen in der `feed.js` die Behandlung des `click`-Ereignisses für den `Location`-Button hinzu und auch noch, wie für die Kamera, eine `initializeLocation()`-Funktion, in der geprüft wird, ob die `Geolocation`-API überhaupt im Browser verfügbar ist: 


=== "public/src/js/feed.js"
	```js linenums="18"
	locationButton.addEventListener('click', event => {
	    if(!('geolocation' in navigator)) {
	        return;
	    }

	    locationButton.style.display = 'none';
	    locationLoader.style.display = 'block';

	    navigator.geolocation.getCurrentPosition( position => {
	        locationButton.style.display = 'inline';
	        locationLoader.style.display = 'none';
	        fetchedLocation = { latitude: position.coords.latitude, longitude: position.coords.longitude };
	        console.log('current position: ', fetchedLocation);
	        locationInput.value = 'In Berlin';
	        document.querySelector('#manual-location').classList.add('is-focused');
	    }, err => {
	        console.log(err);
	        locationButton.style.display = 'inline';
	        locationLoader.style.display = 'none';
	        alert('Couldn\'t fetch location, please enter manually!');
	        fetchedLocation = null;
	    }, { timeout: 5000});
	});

	function initializeLocation() {
	    if(!('geolocation' in navigator)) {
	        locationButton.style.display = 'none';
	    }
	}
	```

In der `initializeLocation()`-Funktion wird geprüft, ob der Browser die `Geolocation`-API unterstützt. Wenn nicht, wird der `Location`-Button versteckt. Wir haben trotzdem, sicherheitshalber, die Abfrage nochmal in die Behandlung des `click`-Ereignisses für diesen Button eingefügt (Zeilen `19-20`), obwohl dies nicht wirklich notwendig ist, da der Button nicht angeklickt werden kann, wenn die `Geolocation`-API nicht unterstützt wird, da er nicht angezeigt wird. 

Wenn auf den Button geklickt wurde, setzen wir den Button selbst auf unsichtbar (Zeile `23`) und den Spinner (Loader) auf sichtbar (Zeile `24`). Zeile `26` zeigt den eigentlichen Zugriff auf die aktuelle Position. Dort wird die Funktion `getCurrentPosition()` der `Geolocation`-API aufgerufen. Wir übergeben drei Parameter:

- der erste Parameter ist die (Callback-)Funktion, die die aktuelle Position zurückgibt. Wenn diese Funktion ausgeführt wird, setzen wir den Button wieder auf sichtbar (Zeile `27`) und den Loader auf unsichtbar (Zeile `28`). Die aktuelle Position `position` enthält die Eigenschaft `coords`, die die `latitude` und `longitude` als Werte enthält (siehe [GeolocationPosition](https://developer.mozilla.org/en-US/docs/Web/API/GeolocationPosition) und [GeolocationPosition](https://developer.mozilla.org/en-US/docs/Web/API/GeolocationCoordinates)).  Diese Position geben wir auf der Konsole aus (Zeile `30`). Wir befüllen das `locationInput`-Eingabefeld noch mit einem Dummy-Wert und fokussieren auf das Eingabefeld (Zeilen `31-32`).
- der zweite Parameter ist eine Funktion, die ausgeführt wird, wenn ein Fehler auftritt. Mögliche Fehler sind, dass im Browser der Zugriff auf die Position deaktiviert wurde, dass die Nutzerin den Zugriff auf die aktuelle Position blockiert hat oder dass die Position nicht "schnell genug" ermittelt werden konnte. Im Fehlerfall geben wir den Fehler auf der Konsole aus und schalten den Button wieder ein und den Loader wieder aus (Zeilen `34-36`).
- der dritte Parameter ist ein JavaScript-Objekt mit `options`. Wir wählen hier nur eine einzige Option, nämlich wie lange nach der aktuellen Position gesucht werden soll. In der Einstellung erfolgt der `timeout` nach `5 sek`. 

Wir passen nun in der `feed.js` noch die beiden Funktionen `openCreatePostModal()` und `closeCreatePostModal()` an:


=== "public/src/js/feed.js"
	```js linenums="109" hl_lines="4 12-13"
	function openCreatePostModal() {
	    createPostArea.style.transform = 'translateY(0)';
	    initializeMedia();
	    initializeLocation();
	}

	function closeCreatePostModal() {
	    createPostArea.style.transform = 'translateY(100vH)';
	    imagePickerArea.style.display = 'none';
	    videoPlayer.style.display = 'none';
	    canvasElement.style.display = 'none';
	    locationButton.style.display = 'inline';
	    locationLoader.style.display = 'none';
	}
	```


Wenn Sie die Anwenung nun starten, werden Sie gefragt, ob Sie die Abfrage nach Ihrem Standort zulassen oder blockieren wollen. Die meisten von Ihnen werden aber die **Ortungsdienste ausgeschaltet** haben. Dann ist auch die Abfrage zunächst egal. Im Mac kann man diese (kurzzeitig, dann wieder ausschalten) über `Systemeinstellungen --> Sicherheit & Datenschutz --> Reiter Datenschutz --> Ortungsdienste` für `Google Chrome` aktivieren. 

Wenn Sie die Positionsbestimmung zulassen, dann wird nach dem Klicken auf den `Location`-Button die aktuelle Position auf der Konsole eingegeben und im Formular erscheint unter Ort `In Berlin`.

Wir machen nichts weiter mit der aktuellen Position. Es gibt viele Möglichkeiten, die jetzt noch ausprobiert werden könnten. Dazu gehören besipeilsweise:

- Wir könnten mithilfe der [Google-Geolocation-API](https://developers.google.com/maps/documentation/geolocation/overview) die Adresse ermitteln, die Google für eine gegebene Position (`longitude` und `latitude`) zurückgibt. Dazu bräuchten wir aber auch einen [API-Key](https://developers.google.com/maps/documentation/geolocation/get-api-key) von Google.
- Wir könnten das Gleiche mit der [Nominatim-API](https://nominatim.org/) für Open Street Map machen. Sie können den Service [hier einmal ausprobieren](https://nominatim.openstreetmap.org/ui/reverse.html), indem Sie Ihre `latitude` und `longitude` aus der Konsolenausgabe eingeben.
- Wir könnten [OpenLayers](https://openlayers.org/en/latest/doc/quickstart.html) verwenden, um die Position auf einer Karte anzuzeigen.
- Wir könnten die Datenbank erweitern und für alle Posts auch noch die Koordinaten der Position abspeichern und dann alle Posts auf einer Karte (mithilfe von OpenLayers + OpenStreetMap) visualisieren.
- ...


### Letzte Verbesserungen

Ein Nachteil in unserer Anwendung ist noch, dass die Kamera die ganze Zeit läuft, wenn wir einmal den modalen Dialog zur Eingabe von daten geöffnet hatten. Wir sollten sie beim Ausschalten des modalen Dialoges schließen. Das Stoppen aller Videostreams hatten wir bereits für die Aufnahme des Fotos gemacht. Weil jedoch das Schließen und erneutes Öffnen der Kamera sehr ressourcenverbrauchend ist, laufen die Animationen für das Öffnen und Schließen des modalen Dialogs nicht mehr flüssig. Wir lagern diese Animationen deshalb in einen asynchronen "Thread" aus (ist nicht wirklich ein neuer Thread): 


=== "public/src/js/feed.js"
	```js linenums="109" hl_lines="2-4 15-20"
	function openCreatePostModal() {
	    setTimeout( () => {
	        createPostArea.style.transform = 'translateY(0)';
	    }, 1);
	    initializeMedia();
	    initializeLocation();
	}

	function closeCreatePostModal() {
	    imagePickerArea.style.display = 'none';
	    videoPlayer.style.display = 'none';
	    canvasElement.style.display = 'none';
	    locationButton.style.display = 'inline';
	    locationLoader.style.display = 'none';
	    if(videoPlayer.srcObject) {
	        videoPlayer.srcObject.getVideoTracks().forEach( track => track.stop());
	    }
	    setTimeout( () => {
	        createPostArea.style.transform = 'translateY(100vH)';
	    }, 1);
	}
	```

Mithilfe des `timeout`-"Tricks" wird der modale Dialog fließend geschlossen und das Kamerazeichen im Tab des Browsers schließt asynchron etwas später. 

!!! success
	Wir haben erfolgreich den Zugriff auf die Kamera (MediaDevices-API) und die Geolocation-API ausprobiert und in unsere Anwendung eingebunden. Die MediaDevices-API bietet neben der `video`-Eigenschaft auch noch die `audio`-Eigenschaft, um das Mikrofon zu verwenden. Mit dem Zugriff auf Kamera und Position haben wir unsere letzte *progressive* Funktionalität für dieses Semester hinzugefügt! Geschafft! 
