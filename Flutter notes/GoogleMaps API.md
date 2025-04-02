Importar libreria flutter pub add google_maps_flutter

En el AndroidManifest ubicado en main, pegar la API Key ej:

```
<application        android:label="google_maps_in_flutter"        android:icon="@mipmap/ic_launcher">        <!-- TODO: Add your Google Maps API key here -->        <meta-data android:name="com.google.android.geo.API_KEY"               android:value="YOUR-KEY-HERE"/>
```
CREACIÓN DEL MAPA

Añades un controller:

late GoogleMapController mapController;
final location = ('Aquí añades tu latitud y longitud actual')

