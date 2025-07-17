# Proyecto de Redes: VLANs y Enrutamiento Dinámico con RIP v2

Este proyecto simula una red segmentada por departamentos utilizando **VLANs**, conectadas entre sí mediante **routers configurados con RIP versión 2** para habilitar el **ruteo dinámico**. El propósito es aprender y demostrar cómo segmentar redes, usar subinterfaces para el ruteo inter-VLAN y cómo implementar un protocolo de enrutamiento dinámico para lograr comunicación entre redes separadas.

---

## Objetivos del Proyecto

- Configurar VLANs por áreas departamentales.
- Implementar subinterfaces en routers para enrutar entre VLANs.
- Establecer enlaces WAN punto a punto entre routers.
- Aplicar el protocolo RIP v2 para enrutamiento dinámico entre LANs.
- Verificar conectividad completa entre todas las estaciones de trabajo de diferentes segmentos.

---

## Descripción de la Topología

La red se divide en tres LANs principales:

1. **LAN 1 – Área de Cómputo**
   - Subred: `192.168.1.0/24`
   - Sin VLAN (red plana)
   - Conectada directamente al Router0

2. **LAN 2 – Administración**
   - VLAN 10: RRHH → `192.168.10.0/24`
   - VLAN 20: Negocios Internacionales → `192.168.20.0/24`
   - Conectada a Router1 mediante un enlace trunk

3. **LAN 3 – Económicas**
   - VLAN 30: Contaduría → `192.168.30.0/24`
   - VLAN 40: Economía → `192.168.40.0/24`
   - Conectada a Router2 mediante un enlace trunk

### Enlaces entre Routers

- Router0 ↔ Router1: `192.168.0.0/30`
- Router0 ↔ Router2: `192.168.0.4/30`

Estos enlaces permiten el intercambio de rutas mediante RIP v2.

---

## Configuraciones Clave

Cada router utiliza subinterfaces para enrutar entre VLANs. Las rutas se comparten usando RIP v2.  
Se configuraron los switches con VLANs, asignando puertos de acceso por departamento y puertos trunk para los enlaces a router.

---

## Pruebas Realizadas

- **Ping entre PCs de diferentes VLANs**: confirmando ruteo funcional.
- **Rutas aprendidas automáticamente con RIP v2**: revisadas con `show ip route`.
- **Verificación de encapsulaciones DOT1Q**: correcta segregación de tráfico VLAN.

---

## Herramientas Utilizadas

- Cisco Packet Tracer
- IOS Cisco 2811 y 2960
- PCs genéricos para prueba de conectividad

---

## Conclusiones

Este ejercicio demuestra cómo las VLANs mejoran la organización y seguridad de una red, permitiendo segmentar por departamentos sin requerir equipos físicos separados. Con RIP v2, los routers pueden aprender rutas automáticamente y escalar la red fácilmente.


## Autor

Emiliano Martínez Vega  
Repositorio creado para prácticas profesionales en redes y ciberseguridad.
