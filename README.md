# RaspberryPi-sensor-dht22-am2302-thingspeak
Raspberry Pi 3 B+ - Captar temperatura y humedad con sensor DHT22 (AM2302) y enviar datos a ThingSpeak.com

Channel ThingSpeak: https://thingspeak.com/channels/769908/

## Requisitos previos

#### Instalar Python 2
```
sudo apt update -y
sudo apt install python-pip -y
sudo python -m pip install --upgrade pip setuptools wheel
```

#### Instalar librerías Adafruit
```
git clone https://github.com/adafruit/Adafruit_Python_DHT.git
cd Adafruit_Python_DHT
sudo python setup.py install
```

## Esquema de conexión: Temperatura y Humedad sensor DHT22 AM2302

El sensor DHT22 AM2302 consta de 3 pines:

- **+** (positivo) = Voltaje 3V (Power - pin 1)
- **-** (negativo) = Tierra (Ground - pin 6)
- **out** = Salida de datos (GPIO4 - pin 7)

Podemos hacer otro esquema de conexión siempre que se respete la funcionalidad de cada pin del sensor al esquema de conexión de la RaspberryPi. Hay que tener en cuenta el número de GPIO donde iría conectado el pin "out" del sensor, este nos proporciona la salida de datos captados. 

En el script *"thingspeak_raspi_dht22.py"* establecemos el número de GPIO en la variable ***raspiGPIO***.

#### Test de conexión del sensor DHT22 AM2302

Teniendo las librerías Adafruit ya instaladas una forma de probar la conexión entre el sensor y la RaspberryPi es ejecutar el script de ejemplo para obtener los datos de temperatura y humedad actuales.

Se le pasa como primer parámetro el modelo de sensor "2302" y el número de GPIO del pin correspondiente donde está conectado la salida de datos (out) del sensor, en este caso 4 (GPIO4)
```
$ python Adafruit_Python_DHT/examples/AdafruitDHT.py 2302 4
Temperatura=21.2*  Humedad=57.7%
```

<p align="center">
<img src="https://raw.githubusercontent.com/adrianlois/RaspberryPi-sensor-dht22-am2302-thingspeak/master/screenshots/raspberrypi-gpio-esquema-conexion-sensor-dht22-am2302.png" width="620" />
</p>

<p align="center">
<img src="https://raw.githubusercontent.com/adrianlois/RaspberryPi-sensor-dht22-am2302-thingspeak/master/screenshots/raspberrypi-gpio-foto-sensor-dht22-am2302.jpg" width="580" />
</p>

## Configuración en la web de ThingSpeak.com

1. Registrarse en https://thingspeak.com
2. Si no tenemos cuenta previa en mathworks, thingspeak nos redirigue usando el mismo email hacia el registro de https://www.mathworks.com. 
3. Crear un nuevo channel en nuestra perfil y agregar dos field chart (Temperatura y Humedad).
4. Obtener el **"Write API Key"** del channel creado.
5. Establecer el API Key en el script *"thingspeak_raspi_dht22.py"* en la variable ***miAPIWrite***. 

Channel ThingSpeak: https://thingspeak.com/channels/769908/

<p align="center">
<img src="https://raw.githubusercontent.com/adrianlois/RaspberryPi-sensor-dht22-am2302-thingspeak/master/screenshots/raspberrypi-thingspeak-adryanraspi.png" width="720" />
</p>
