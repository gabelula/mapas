No todos los datos geograficos deberian ser visualizados en mapas. Aveces hay datos que al visualizarlos en un mapa pueden llevar a confundir en vez de aclarar y que realmente requieren otro tipo de visualización.

ejemplos si:
  resultados de elecciones, como se voto en tu escuela?
  por donde hay contaminación, por ejemplo contestar la pregunta "contaminación en el riachuelo"

ejemplos no:
  ...

Cuando no usar un mapa para visualizar datos geograficos:

1. cuando los patrones interesantes no son geograficos
2. cuando los datos geograficos son mas efectivos para analizar


Mapas

Los mapas consisten de datos geograficos y un sistema para representarlos visualmente.

1. Datos Geograficos

- Latitud y Longitud
  Muchos de los datos que encuentren estaran basados en coordenadas latitud/longitud de la superficie de la Tierra.
  Latitudes van de -90 (polo sur) a 90 (polo norte), con 0 siendo el ecuador.
  Longitudes van de -180 (la mitad del camino yendo del primer meridiano al oeste) a 180 (la mitad del camino yendo del primer meridiano al este)

  Un capitan de la mar podria escribir latitud y longitud en grados, minutos y segundos como:

  37°46'42"N, 122°23'22"W

  pero las comutadoras usan decimales nomas:

  37.77833, -122.38944

  Si tienes un par latitud/longitud y quieres saber rapidamente donde es puedes entrarlos en google earth u openstreetmap.org

- Geometria de mapas

  Cualquier espacio geografico se puede expresar como una secuencia de pares latitud/longitud.

  Un lugar (un punto en un mapa) es un sólo par latitud/longitud:

  /mapa/

  Una linea recta (una calle en un mapa) es un par de puntos latitud/longitud (uno para el inicio y otro para el final).

  /mapa/

  Una secuencia de lineas, aveces llamada polyline, es una lista de lineas rectas en orden (una lista de pares de puntos latitud/longitud).

  /mapa/

  Una región cerrada, llamada polygono, es un tipo especia de polyline que termina donde empezo.

  /mapa/


  Resumen: todo lo que representes en un mapa es un conjunto de puntos latitud/longitud.


Los formatios más comunes de expresar datos geograficos, piensan en terminos de features. Una feature puede ser cualquier cosa que exista en un lugar fisico fijo (una casa, un pais, ciudad, calle, semaforo, lago, etc). Una feature tiene geometria y propiedades.

La geometria de una feature consiste en una combinación de elementos geometricos como los anteriores. Por ejemplo, la geodata de un país puede consistir de alrededor de 200 features. Cada feature consiste de una lista de puntos para dibujar una linea alrededor del perimetro del país, es decir, un poligono.

Las propiedades de un feature es todo lo demas que te interesa para mostrar en el mapa. Por ejemplo, para los paises del mundo seguramente te interese los nombres.

Formatos de Geodatos

En el mundo real la lista de latitud/longitud tienen que venir en un formato que una computadora puede leer y que deseablemente sea entendible por humanos.

Hay muchisimos formatos pero cuatro que son los más comunes:

. Shapefile

Más común para datos detallados de mapas. Un "shapefile" es un conjunto de archivos:
- .shp - la geometria de todas las features
- .shx - un archivo de ayuda que guarda el orden en que los shapes estaran
- .dbf - guarda las propiedades de cada features en una planilla
- .prj - descripción de proyecto

Es un buen formato para manipulación e inspección de datos de mapas. No es muy bueno para hacer mapas en la web pero hay herramientas para convertirlos a otros formatos.

. GeoJSON

JSON es un formato ligero para intercambio de datos en la web. GeoJSON es el mismo formato para mapas en la web. También es entendible por humanos y se puede abrir y editar en cualquier editor de textos.

Veamos el geojson para el perimetro de Uruguay

{
  "type":"Feature",  
  "geometry":{
    "type":"Polygon",
    "coordinates":[
      [
        [-57.62513342958296,-30.21629485445426],
        [-56.976025763564735,-30.109686374636127],
        [-55.97324459494094,-30.883075860316303],
        [-55.601510179249345,-30.853878676071393],
        [-54.57245154480512,-31.494511407193748],
        [-53.78795162618219,-32.047242526987624],
        [-53.209588995971544,-32.727666110974724],
        [-53.6505439927181,-33.20200408298183],
        [-53.373661668498244,-33.768377780900764],
        [-53.806425950726535,-34.39681487400223],
        [-54.93586605489773,-34.952646579733624],
        [-55.67408972840329,-34.75265878676407],
        [-56.21529700379607,-34.85983570733742],
        [-57.1396850246331,-34.430456231424245],
        [-57.81786068381551,-34.4625472958775],
        [-58.42707414410439,-33.909454441057576],
        [-58.349611172098875,-33.26318897881541],
        [-58.13264767112145,-33.040566908502015],
        [-58.14244035504076,-32.044503676076154],
        [-57.87493730328188,-31.016556084926208],
        [-57.62513342958296,-30.21629485445426]
      ]
    ]
  },
  "properties":{
    "name": "Uruguay",
    "capital": "Montevideo"
  },  
}

Esto significa dibujar un poligono empezando en [-57.62513342958296,-30.21629485445426] y terminando en ese mismo punto.


. KML

Es un XML especifico para datos geograficos. Es usado por Google Maps, Google Earth, Google Fusion Tables.


Para Uruguay

<?xml version="1.0" encoding="utf-8" ?>
<kml xmlns="http://www.opengis.net/kml/2.2">
<Document><Folder><name>OGRGeoJSON</name>
  <Placemark>
  <name>Uruguay</name>
  <Style><LineStyle><color>ff0000ff</color></LineStyle><PolyStyle><fill>0</fill></PolyStyle></Style>
  <ExtendedData><SchemaData schemaUrl="#OGRGeoJSON">
    <SimpleData name="capital">Montevideo</SimpleData>
  </SchemaData></ExtendedData>
      <Polygon><outerBoundaryIs><LinearRing><coordinates>-57.625133429582959,-30.216294854454262 -56.976025763564735,-30.109686374636127 -55.973244594940937,-30.883075860316303 -55.601510179249345,-30.853878676071393 -54.572451544805119,-31.494511407193748 -53.787951626182192,-32.047242526987624 -53.209588995971544,-32.727666110974724 -53.650543992718099,-33.20200408298183 -53.373661668498244,-33.768377780900764 -53.806425950726535,-34.396814874002231 -54.93586605489773,-34.952646579733624 -55.674089728403288,-34.752658786764073 -56.215297003796067,-34.859835707337417 -57.139685024633103,-34.430456231424245 -57.81786068381551,-34.462547295877499 -58.427074144104388,-33.909454441057576 -58.349611172098875,-33.263188978815407 -58.132647671121447,-33.040566908502015 -58.142440355040762,-32.044503676076154 -57.874937303281882,-31.016556084926208 -57.625133429582959,-30.216294854454262</coordinates></LinearRing></outerBoundaryIs></Polygon>
  </Placemark>
</Folder>
<Schema name="OGRGeoJSON" id="OGRGeoJSON">
  <SimpleField name="capital" type="string"></SimpleField>
</Schema>
</Document></kml>

. TopoJSON

Es similar a GeoJSON pero reducido para que sea más ligero y guarde solamente lo que importe de los datos. 
