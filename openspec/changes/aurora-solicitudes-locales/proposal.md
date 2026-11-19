# Piloto local de solicitudes para Comercial Aurora

## Why

Comercial Aurora necesita dar seguimiento a unas 600 solicitudes de servicio mensuales y reducir los casos extraviados o sin responsable. El piloto permitirá comprobar el flujo de atención en el navegador de un solo equipo durante seis semanas.

## What Changes

- Entregar un HTML autónomo que se pueda abrir con doble clic.
- Radicar solicitudes de teléfono, correo y mensajería, asignarlas por rotación y seguirlas en una bandeja con historial.
- Medir el tiempo transcurrido hasta la resolución y el cumplimiento del plazo de 48 horas corridas.
- Cargar un directorio de prueba desde JSON o CSV y conservar la sesión entre aperturas mediante respaldo JSON manual.

## Capabilities

### New Capabilities

- `radicacion-de-solicitudes` — directorio, captura y asignación rotativa.
- `seguimiento-de-solicitudes` — perfiles locales, bandeja, estados, historial y resolución.
- `respaldo-local` — exportación y recuperación desde JSON.

### Modified Capabilities

## Impact

El repositorio incorporará `aurora.html` como entregable. El piloto funciona en una sesión activa de navegador, en un equipo. La autenticación, la base de datos compartida, las integraciones ERP y omnicanal, las alertas de plazo y el portal externo quedan fuera del piloto.
