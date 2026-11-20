# Adaptación de mapas de Chile para Lastbook — plan inicial

**Estado:** investigación y planificación, sin cambios funcionales en el motor ni mapas generados.
**Fecha:** 2026-11-20.
**Alcance geográfico inicial:** Región de Los Ríos (CL-LR), con continuidad hacia Los Lagos (CL-LL).

## Contexto

Esta rama del fork [jnramosm/lastbook](https://github.com/jnramosm/lastbook/tree/feature/chile-maps) separa el trabajo local sobre mapas de Chile de la rama `main`, que puede mantenerse alineada con [Immortal-Protocols/lastbook](https://github.com/Immortal-Protocols/lastbook). La planificación general, compras y pruebas del proyecto se mantienen en [resiliencia-panguipulli](https://github.com/jnramosm/resiliencia-panguipulli), no dentro del fork.

## Fuentes y dependencias a evaluar

1. [Propuesta oficial existente para regiones de Chile](https://github.com/Immortal-Protocols/lastbook/blob/main/docs/REGIONS-CL.md): **es una propuesta documental, no una implementación funcional**.
2. [OpenStreetMap Chile en Geofabrik](https://download.geofabrik.de/south-america/chile.html): datos base de vías, localidades y puntos de interés. Respetar la licencia ODbL y atribución.
3. Límites regionales oficiales (INE / IDE Chile / BCN): verificar geometrías y derechos de reutilización antes de cortar paquetes.
4. Direcciones: adaptar parser para calle antes del número, `S/N`, nombres con números y tildes, comuna y códigos postales de 7 dígitos. Inspeccionar registros de Overture para Chile antes de implementar índices.
5. Datos de emergencia (SENAPRED y autoridades): usar capas solo con vigencia, origen y permisos comprobados; no prometer que un mapa base refleja vías abiertas o refugios operativos.

## Plan de trabajo por etapas

- [ ] Revisar `docs/MAPS.md`, `docs/REGIONS-CL.md`, `tools/`, `engine/address_search.py` y `packaging/` para identificar las modificaciones mínimas.
- [ ] Conseguir extracto OSM y límites oficiales para un prototipo de CL-LR; no almacenar datos privados o coordenadas de propiedades en este fork público.
- [ ] Construir un conjunto cartográfico pequeño y verificable, sin sustituir indiscriminadamente archivos del producto original.
- [ ] Adaptar e inspeccionar búsqueda de direcciones y localidades chilenas; agregar tests de acentos y rutas rurales.
- [ ] Probar navegación y consultas sin WAN, desde la app y eventualmente desde el servidor LAN.
- [ ] Verificar licencia y trazabilidad de cada capa; documentar tamaño de descarga y almacenamiento.
- [ ] Evaluar incluir CL-LL y conexiones interregionales; validar cómo maneja Lastbook conjuntos de mapas alternativos.
- [ ] Antes de proponer cambios al upstream, preparar PR pequeño con pruebas reproducibles y sin datos locales sensibles.

## Arquitectura y pruebas

- La aplicación de escritorio de Lastbook no abre puertos; el acceso mediante teléfonos requiere probar su modalidad de servidor, documentada en [LIBRARY-SERVER.md](https://github.com/Immortal-Protocols/lastbook/blob/main/docs/LIBRARY-SERVER.md).
- Verificar requisitos del modelo de IA opcional y rendimiento real del Mac elegido antes de comprar hardware por motivos exclusivamente cartográficos.
- Probar siempre un reinicio completo sin internet, restauración de backups y visualización básica incluso si el modelo de IA no arranca.

**Importante:** Crear esta rama y documento no incorpora todavía mapas de Chile, ni garantiza interoperabilidad o sincronización automática con el repositorio original.
