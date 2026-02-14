<h1 align="center">✮ ═══════𝖦𝖤𝖮𝖫𝖮𝖢𝖠𝖫𝖨𝖹𝖠𝖢𝖨Ó𝖭 𝖶𝖤𝖡═══════ ✮</h1>
<p align="center">ᓚ₍⑅^..^₎♡
<p align="center">
Esta aplicación permite obtener la ubicación actual del usuario y mostrarla en un mapa interactivo.
</p>

![PRUEBA](https://github.com/Vivian-14/GEOLOCALIZACION/blob/main/pruebas/GEOLOCALIZACION.png)


ᴬˡᵒⁿᵈʳᵃ ⱽⁱᵃⁿⁿᵉʸ ᴴᵉʳⁿᵃⁿᵈᵉᶻ ᵀᵒʳʳᵉˢᴳᵀᴵᴰ¹⁵² ⱽⁱ
------------------------------------
ᴄʀᴇᴀᴄɪᴏɴ ᴅᴇ ʟᴀ ᴄᴀʀᴘᴇᴛᴀ ᴅᴇʟ ᴘʀᴏʏᴇᴄᴛᴏ
-----------------------------------
>cd Desktop

>mkdir GeolocalizacionWeb

>cd GeolocalizacionWeb
-----------------------------------
ᴄʀᴇᴀᴄɪᴏɴ ᴅᴇ ʟᴀ ᴇꜱᴛʀᴜᴄᴛᴜʀᴀ
-----------------------------------
>mkdir templates

>mkdir static

>type nul > app.py

>type nul > templates\index.html

>code .

-----------------------------------
ᴇꜱᴛʀᴜᴄᴛᴜʀᴀ ꜰɪɴᴀʟ
-----------------------------------

GeolocalizacionWeb/
│
├── app.py
├── templates/
│   └── index.html
└── static/

-----------------------------------
ᴇɴᴛᴏʀɴᴏ ᴠɪʀᴛᴜᴀʟ
-----------------------------------

>python -m venv venv

>venv\Scripts\activate

>pip install flask


-----------------------------------
ᴀᴘᴘ.ᴘʏ
-----------------------------------

```python
# Importamos Flask
from flask import Flask, render_template

# Creamos la aplicación
app = Flask(__name__)

# Ruta principal
@app.route("/")
def home():
    return render_template("index.html")

# Ejecutar servidor
if __name__ == "__main__":
    app.run(debug=True)

```
-----------------------------------
ɪɴᴅᴇx.ʜᴛᴍʟ
-----------------------------------
```html
<!DOCTYPE html>
<html>
<head>
    <title>Geolocalización Web</title>
    
    <!-- Librería Leaflet (mapa gratis) -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

    <style>
        #map {
            height: 500px;
            width: 100%;
        }
    </style>
</head>
<body>

    <h1>Mi Ubicación Actual</h1>
    <button onclick="obtenerUbicacion()">Obtener Ubicación</button>

    <p id="info"></p>
    <div id="map"></div>

    <script>
        function obtenerUbicacion() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(mostrarPosicion);
            } else {
                alert("La geolocalización no es soportada por este navegador.");
            }
        }

        function mostrarPosicion(position) {
            let lat = position.coords.latitude;
            let lon = position.coords.longitude;

            document.getElementById("info").innerHTML =
                "Latitud: " + lat + "<br>Longitud: " + lon;

            // Crear mapa
            var map = L.map('map').setView([lat, lon], 15);

            // Cargar mapa base OpenStreetMap
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© OpenStreetMap contributors'
            }).addTo(map);

            // Agregar marcador
            L.marker([lat, lon]).addTo(map)
                .bindPopup("Aquí estás 📍")
                .openPopup();
        }
    </script>

</body>
</html>
```
-----------------------------------
ᴄꜱꜱ
-----------------------------------
```css
body {
    font-family: Arial, sans-serif;
    background-color: #e5c0d9; /* fondo suave */
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}

h1 {
    color: #831394;
    margin-top: 30px;
    text-align: center;
}

button {
    background-color: #C88FCF;
    color: rgb(255, 255, 255);
    border: none;
    padding: 12px 25px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    margin: 15px 0;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #831394;
}

#info {
    background-color: #eb6bff44;
    padding: 15px 20px;
    border-radius: 8px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    margin-bottom: 20px;
    text-align: center;
    font-weight: bold;
    color: #333333;
}

#map {
    height: 500px;
    width: 90%;
    max-width: 800px;
    border-radius: 23px;
    box-shadow: 0 4px 10px rgba(214, 78, 155, 0.3);
    margin-bottom: 40px;
}

/* Footer opcional */
footer {
    color: #ac2da3;
    margin-bottom: 20px;
    text-align: center;
    font-size: 14px;
}
```


