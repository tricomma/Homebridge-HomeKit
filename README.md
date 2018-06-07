# Homebridge — HomeKit

La idea de este documento es para hacer un pequeño recopilatorio de información y guías para poder montar tu ecosistema en [HomeKit](https://www.apple.com/es/ios/home/) con [Homebridge](https://github.com/nfarina/homebridge) y distintos dispositivos de diferentes marcas.

## Índice

* [Ventajas de usar Homebridge](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#ventajas-de-usar-homebridge)
* [Requisitos](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#requisitos)
* [Instalación servidor Homebridge](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#instalaci%C3%B3n-de-homebridge)
* [Dispositivos](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#dispositivos)

## Ventajas de usar Homebridge

Homebridge es un puente que hace compatibles con HomeKit (el ecositema de Apple para la domótica) accesorios que no lo son. Lo bueno de esto, es que puedes montarte buena parte de la domótica de tu hogar sin hacer un gran desembolso de dinero y sobretodo, trasteando y aprendiendo que es lo que más nos gusta.
Entre las principales ventajas encontramos:

* Dispositivos baratos
* Ecosistema iOS y próximamente OSX (*10.14 Mojave*)
* Diferentes marcas y modelos
* Poder manejar todo con Siri :)

## Requisitos

* Servidor Homebridge
* iPad o AppleTV 4 siempre en el hogar para hacer de central de accesorios (hacer automatizaciones y gestionar la casa a distancia)
* Dispositivos compatibles

## Instalación de Homebridge

| Servidor      | Guía           |
| ------------- | -------------- |
| [RaspberryPi](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#instalaci%C3%B3n-en-raspberrypi)   | *JMRamirez*    |
| [QNAP](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#instalaci%C3%B3n-en-qnap)          | *JMRamirez*    |

### Instalación en RaspberryPi

Tutoríal cortesía de *[JMRamirez](https://www.jmramirez.pro/tutorial/homebridge-con-homekit/)*.

* Conectamos a nuestro servidor mediante SSH, actualizamos los paquetes e instalamos `node.js`:

```
$ sudo apt-get update
$ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash
$ sudo apt-get install -y nodejs
$ sudo apt-get install -y build-essential
```

* Si `curl` no está instalado, ejecutamos este comando:

```
$ sudo apt-get install curl
```

* Instalamos la librería `avahi`:

```
$ sudo apt-get install libavahi-compat-libdnssd-dev
```

* Ahora instalamos un gestor de módulos `npm`:

```
$ sudo apt-get install npm
```

* Si la tenemos ya instalada, nos dará un error diciendo cosas como que no se va a instalar. Podemos ejecutar `$ npm` para comprobarlo.
Ahora que ya tenemos todas las dependencias pareparadas es el turno de instalar Homebridge. Para ello ejecutamos el siguiente comando:

```
$ sudo npm install -g --unsafe-perm homebridge
```

Listo! Ya tenemos homebridge instalado en nuestro equipo. Ahora es el turno de instalar los plugins compatibles con los accesorios que tengas.

El archivo de configuración lo encontramos en la siguiente ruta `/home/tu_usuario`.

Cuando vayamos instalando los plugins para añadir distintos dispositivos, estos se almacenan en la siguiente ruta `/usr/local/lib/node_modules`. Recomiendo desinstalar los que no estemos utilizando.

Para ejecutar Homebridge es recomendable hacerlo sobre un screen y así poder minimizar la ventana y que siga corriendo en segundo plano.

```
$ screen -S homebridge
$ homebridge
```

Pulsando `ctrl` + `a` + `d` minimizamos la ventana de Homebridge. Para recuperarla ejecutamos:

```
$ screen -r homebridge
```

### Instalación en QNAP

Tutoríal cortesía de *[JMRamirez](https://www.jmramirez.pro/tutorial/homebridge-en-qnap/)*.

## Dispositivos

Iré actualizando esta lista. Actualmente son los dispositivos que tengo y he configurado sin problemas en mi casa.

| Marca         | Modelo        | Plugin | Guía  |
| ------------- |:-------------:|:------:|:-----:|
| Xiaomi        | Gateway + accesorios  | *homebridge-mi-aqara*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#xiaomi-gateway-gateway--todos-los-sensores) |
| Xiaomi        | Alarma  | *homebridge-mi-gateway-security*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#xiaomi-alarma-sistema-de-alarma) |
| Xiaomi        | Radio  | *homebridge-mi-gateway-fm*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#xiaomi-radio-fm) |
| Sonoff        | Basic         |   *homebridge-sonoff-basic-espeasy*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#sonoff-basic) |
| Sonoff        | S20           |   *homebridge-sonoff-tasmota-http*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#sonoff-s20) |
| Philips       | LightBulb     |   *homebridge-mi-philips-light*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#philips-lightbulb) |
| LG            | webOS3        |   *homebridge-webos3*  |   [*PEND*](https://github.com/tricomma/Homebridge-HomeKit/blob/master/README.md#lg-webos) |

### Xiaomi Gateway (Gateway + todos los sensores)
[*homebridge-mi-aqara*](https://github.com/YinHangCode/homebridge-mi-aqara)

Con este plugin podemos hacer compatibles prácticamente todos los accesorios que se vinculan con el Gateway.

```
1.Gateway(网关)
2.ContactSensor(门磁感应)
3.MotionSensor(人体感应)
4.Button(按钮)
......... *en desarrollo*
```

```
$ sudo npm install -g homebridge-aqara
```

#### Configuración

*En desarrollo*

### Xiaomi Alarma (Sistema de alarma)
[*homebridge-mi-gateway-security*](https://github.com/YinHangCode/homebridge-mi-gateway-security)

Con este plugin añadimos la alarma del Security Kit a Homebridge.

```
$ sudo npm install -g homebridge-mi-gateway-security
```

#### Configuración

*En desarrollo*

### Xiaomi Radio FM
[*homebridge-mi-gateway-fm*](https://github.com/YinHangCode/homebridge-mi-gateway-fm)

Con este plugin añadimos la radio del Gateway a Homebridge. Extra: Añadir emisoras en Español. Cortesía de *[NPIRTUBE
](https://npirtube.com/radio-internacional-xiaomi-gateway-radio-internet/)*.

```
$ sudo npm install -g homebridge-mi-gateway-fm
```

#### Configuración

*En desarrollo*

### Sonoff Basic
[*homebridge-sonoff-basic-espeasy*](https://github.com/seikan/homebridge-sonoff-basic-espeasy)

Plugin para hacer compatible el relé Sonoff Basic. Requiere desmontar, soldar y flashear el dispositivo.

```
$ sudo npm install -g homebridge-mi-gateway-fm
```

#### Instalando [ESPEasy](https://github.com/letscontrolit/ESPEasy) en Sonoff Basic

*En desarrollo*

#### Configuración

*En desarrollo*

### Sonoff S20
[*homebridge-sonoff-tasmota-http*](https://github.com/ageorgios/homebridge-sonoff-tasmota-http)

Plugin para hacer compatible el enchufe Sonoff S20. Requiere desmontar, soldar y flashear el dispositivo.

```
$ sudo npm install -g homebridge-sonoff-tasmota-http
```

#### Instalando [tasmota](https://github.com/arendst/Sonoff-Tasmota) en Sonoff Basic

*En desarrollo*

#### Configuración

*En desarrollo*

### Philips LightBulb
[*homebridge-mi-philips-light*](https://github.com/YinHangCode/homebridge-mi-philips-light)

Plugin para añadir bombillas Philips.

```
1.MiPhilipsSmartBulb(米家飞利浦智睿球泡灯)
2.MiPhilipsTableLamp2(米家飞利浦智睿台灯二代)
3.MiPhilipsCeilingLamp(米家飞利浦智睿吸顶灯)
```

```
$ sudo npm install -g homebridge-sonoff-tasmota-http
```

#### Configuración

*En desarrollo*

### LG webOS
[*homebridge-webos3*](https://github.com/merdok/homebridge-webos3)

Controlar nuestra televisión con webOS 3.

```
$ sudo npm install -g homebridge-webos3
```

#### Configuración

*En desarrollo*
