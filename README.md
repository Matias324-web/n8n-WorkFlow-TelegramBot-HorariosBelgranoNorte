Bot de Telegram para Horarios de Tren y Clima (n8n)
Descripción General
Este proyecto es un workflow de n8n que potencia un bot de Telegram para la consulta de horarios de transporte. El bot es capaz de interpretar un mensaje de un usuario (indicando origen, destino y día) y devolver una respuesta completa que incluye los próximos horarios de servicio y el clima actual en la estación de origen.

* Características Principales:
Procesamiento de Lenguaje Natural (Básico): Interpreta el mensaje del usuario para extraer las entidades clave: ORIGEN, DESTINO y DIA de la consulta.

* Lógica de Negocio Personalizada:
Determina automáticamente el sentido del viaje (ej. "Hacia Retiro" o "Hacia Villa Rosa") basándose en las estaciones.
Selecciona la hoja de horarios correcta (ej. días hábiles, sábados o domingos) según el día consultado.

* Filtrado en Tiempo Real: 
Obtiene la hora actual del servidor y la compara con la grilla de horarios para devolver únicamente los próximos trenes disponibles (y no los que ya pasaron).

* Integración de API Externa:
Se conecta a la API de AccuWeather para obtener el reporte del clima actual en la estación de origen.
Respuesta Formateada: Combina toda la información (próximos trenes y clima) en un único mensaje de respuesta, con un formato claro y amigable para el usuario.

* Tecnologías Utilizadas:
n8n (Plataforma de automatización de workflows)
API de Telegram (Para la comunicación del bot)
API de AccuWeather (Para la consulta del clima)
Google Sheets (Como base de datos para las grillas de horarios)

* Cómo Funciona (Flujo del Workflow):
Trigger: El workflow se activa cuando recibe un mensaje a través del Bot de Telegram.
Extracción: Un nodo (posiblemente un Agente AI o código) procesa el texto para extraer ORIGEN, DESTINO y DIA.
Lógica: Se determina el sentido del viaje y la hoja de Google Sheets a consultar.
Búsqueda de Horarios: Se leen los horarios desde Google Sheets.
Búsqueda de Clima: Se realiza una llamada a la API de AccuWeather con la estación de origen.
Procesamiento: Un nodo de código filtra los horarios (solo los próximos) y unifica los datos.
Respuesta: Se envía el mensaje final formateado al usuario por Telegram.
