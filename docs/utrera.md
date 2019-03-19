# Utrera - Smart Utrera

---

## Introducción, antecedentes, entorno

Wellness es la competencia en este cliente. Wellness tiene en Utrera una especie de laboratorio smart city. Han desplegado su plataforma smart y verticales. También han desplegado una app ciudadana. Sin que haya habido concurso público, mediante algún tipo de acuerdo con el Ayuntamiento, del que desconocemos detalles.

Wellness presentó su oferta para este pliego fuera de plazo. Telefónica ganó porque fué el que más mejoras ofreció en su oferta. Las mejoras eran incrementar el número de dispositivos por encima del mínimo exigido en el pliego (quizá alguna mejora adicional).

Los verticales que implantamos en este proyecto tienen que enviar sus datos a la plataforma smart de Wellness. Para ello, nuestros verticales tendrán un API que se invocará desde Wellness.

El alcalde ha estado siempre en contra de Telefónica. Con este proyecto está cambiando algo su percepción, gracias a nuestra propuesta de utilizar NB-IoT para las comunicaciones, lo que hace innecesario la instalación de dispositivos concentradores en via pública.

---

## Descripción

Instalación de dos verticales:

* Smart Parking
* Calidad Ambiental

---
### Contactos

#### Ayuntamiento de Utrera

* Begoña Sanchez Cañete: arquitecto del Ayto. Utrera
    * bsanchez@utrera.org
* Juan Luis Martinez Paredez: responsable IT del Ayto. Utrera
    * jlmartinez@utrera.org
* Vicente Llanos Siso: el jefe de Begoña, la va a sustituir mientras Begoña está de baja
    * vllanos@utrera.org

#### C&G ITsolutions

* Victor García: comercial
    * 663818217
    * vgarcia@cygitsolutions.com

#### Urbiótica

* Leonardo G. Rios
    * leonardo.g.rios@urbiotica.com

---

## Alcance y planificación

La ejecución del proyecto tiene tres partes: 

1. Proyecto Técnico. Es un documento en el que hay que describir todo lo que se va a hacer y el impacto en las calles de Utrera. Los parkings están en zona de Patrimonio Histórico. Descripción técnica y el impacto. A la parte de calidad ambiental este tema le afecta menos, porque las zonas no son patrimonio histórico.
    - Plazo: 30 de marzo
    - Proveedor: Afivén (en concreto, un arquitecto que proporciona Afivén)
1. Implantación:
    - Plazo: 3 meses una vez aprobado el Proyecto Técnico
    - Proveedores
        - Parking: la solución es la de Urbiótica pero la instalación la hace la empresa C&G ITsolutions. El motivo es que Urbiótica no tenía gente para instalar en Utrera (o salía carísimo) y Miguel Ángel encontró esta empresa con la ayuda de Compras
        - Calidad ambiental: HOP Obiquitous, lo hacen todo, proveen la solución completa y realizan la instalación
1. Garantía y Soporte
    - Plazo : 7 años

### Instalación de smart parking en la Plaza del Altozano

Se ha adelantado al mes de Abril la instalación de las plazas de parking de la Plaza del Altozano. La instalación de las plazas de parking se hará aprox en Mayo porque los sensores de parking con NB-IoT tienen que fabricarse ex-profeso para el proyecto. La instalación se realizará, por tanto, después de las elecciones y se ha decidido adelantar una instalación de plazas de parking. Esta instalación no va a llevar NB-IoT por lo que hay que instalar un dispositivo concentrador, con tarjeta M2M estandar.

Miguel Angel ha comunicado a C&G la instalación en Abril de la Plaza del Altozano.

### Instalación de calidad ambiental

Toda la instalación la hace HOPU. Ha habido unos cambios sobre las ubicaciones indicadas en el pliego. Estamos a la espera de recibir la confirmación de las ubicaciones definitivas para ver la implicación de las nuevas ubicaciones en los costes de instalación y confirmar si HOPU lo asume (en principio, están dispuestos a asumirlo si las implicaciones no son muy grandes). Hemos recibido un documento por correo con los materiales necesarios para la instalación en las nuevas ubicaciones pero no hemos recibido todavía en sí el listado con las nuevas ubicaciones.

---

## Proveedores, Compras

### Afiven

Compra y pedido realizado. Es una subcontratación. El pedido tiene un hito correspondiente a la aceptación del proyecto técnico.

PDTE hitos del pedido

### Urbiótica

PDTE datos solicitud de compra e hitos del pedido

### [C&G ITsolutions](https://cygitsolutions.com/)

PDTE datos solicitud de compra e hitos del pedido

### [HOP](https://hopu.eu/)

Tienen una plataforma compatible FIWARE

PDTE datos solicitud de compra e hitos del pedido

---

## Estado actual, temas pendientes

### Temas pendientes

- [ ] Revisar hitos pedido Afivén
- [ ] Rellenar información compra Urbiótica
- [ ] Rellenar información compra C&G ITsolutions
- [ ] Rellenar información compra HOP
- [ ] Datos instalaciones calidad ambiental para el proyecto técnico solicitados en correo
- [ ] Confirmar con Miguel Angel qué hay que hacer con el documento recibido por correo con lista de materiales para la instalación de calidad ambiental
- [ ] Datos instalaciones parking Plaza Altozano solicitados en correo del 14/03
- [ ] Persona responsable en C&G de la instalación en Plaza del Altozano
- [ ] Revisar con Miguel Angel si hay temas pendientes con M2M (administrativos o de otro tipo)
- [ ] NB-IoT : gestionar que se haga una prueba e2e con un dispositivo de parking lo antes posible

---
