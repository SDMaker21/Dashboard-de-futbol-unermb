# Arquitectura y Estructura del Proyecto: Elite Scout

Este documento describe la estructura técnica y los archivos del ecosistema Elite Scout, diseñado para la gestión y exportación de datos deportivos.

## 📂 Archivos del Sistema

* **`index.html`**: Archivo principal del proyecto (Single-File Component). Contiene la estructura de la interfaz, el diseño estilizado y toda la lógica de la aplicación, incluyendo la base de datos local y el motor de renderizado.
* **`Fichas_Individuales.txt`**: Reporte generado dinámicamente en texto plano. Presenta la información de los jugadores utilizando arte ASCII, optimizado para la lectura rápida del cuerpo técnico.
* **`Base_Datos.csv`**: Archivo de exportación tabular estructurado por comas. Diseñado para garantizar la interoperabilidad con herramientas de análisis de datos como Microsoft Excel o Google Sheets.

## 🏗️ Estructura Interna del Código (`index.html`)

### 1. Capa de Presentación (HTML & Tailwind CSS)
* **Navegación (`<header>`)**: Contiene el branding de Elite Scout, las pestañas de selección de equipo y el menú desplegable de exportación de archivos.
* **Panel Lateral (`<aside>`)**: Sección fija (sticky) que renderiza la tabla de posiciones general basándose en los puntos y diferencia de goles.
* **Área Principal (`<section>`)**: Contenedor dinámico que aloja el buscador de texto en tiempo real, los filtros por posición y el *grid* responsivo de tarjetas de jugadores.
* **Ventana Modal (`#player-modal`)**: Capa superpuesta que se activa mediante el DOM para mostrar el detalle extendido del jugador seleccionado.

### 2. Capa de Lógica y Procesamiento (JavaScript)
* **Base de Datos Mock (`TEAMS`)**: Arreglo de objetos JSON que actúa como fuente de la verdad para inyectar datos en la interfaz.
* **Gestor de Estado (`state`)**: Objeto global ligero que rastrea los filtros activos (equipo seleccionado, término de búsqueda y posición).
* **Motor de Renderizado**: Conjunto de funciones (`renderRoster`, `renderStandings`, etc.) que actualizan partes específicas del DOM utilizando *Template Literals*.
* **Módulo de I/O (Exportación)**: Sistema basado en la API nativa `Blob` que serializa los objetos de memoria en archivos TXT, CSV y MD para su descarga directa en el navegador.