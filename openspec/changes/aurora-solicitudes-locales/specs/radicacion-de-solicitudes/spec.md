# Radicación de solicitudes

## Purpose

Registrar las solicitudes de los clientes con un identificador único y un agente responsable desde el primer contacto.

## ADDED Requirements

### Requirement: Directorio de clientes

La aplicación SHALL importar un directorio de prueba desde JSON o CSV y permitir buscar por NIT para completar la razón social.

#### Scenario: Localizar un cliente importado

- **GIVEN** un archivo del directorio con un NIT y su razón social
- **WHEN** el usuario importa el archivo y busca ese NIT
- **THEN** puede seleccionar el cliente y se completa su razón social.

#### Scenario: Rechazar datos de clientes inválidos

- **WHEN** el usuario importa un archivo mal formado o con NIT duplicados
- **THEN** la aplicación explica el error y conserva el directorio anterior.

### Requirement: Registro manual de solicitudes

La aplicación SHALL exigir cliente del directorio, canal, tipo y descripción de al menos diez caracteres. SHALL admitir teléfono, correo y mensajería como canales. Los tipos SHALL ser consulta de stock, estado de pedido, inconformidad de envío, facturación o cobro, y devolución. La referencia de pedido SHALL ser opcional.

#### Scenario: Completar una radicación

- **WHEN** un usuario guarda una solicitud válida
- **THEN** la aplicación registra la fecha y hora del equipo, asigna un radicado único e inmutable con formato `AUR-YYYYMM-XXXX`, asigna un agente y crea el primer evento del historial con estado Nuevo.

#### Scenario: Corregir un campo inválido

- **WHEN** un usuario intenta guardar con un campo obligatorio inválido
- **THEN** la aplicación identifica el campo y conserva los datos del formulario sin crear una solicitud ni avanzar el consecutivo o la rotación.

### Requirement: Asignación rotativa

La aplicación SHALL asignar cada radicación exitosa al siguiente de los cuatro agentes en orden circular.

#### Scenario: Completar una vuelta

- **GIVEN** una sesión nueva
- **WHEN** se guardan cinco radicaciones válidas consecutivas
- **THEN** las primeras cuatro quedan asignadas a agentes distintos y la quinta queda a cargo del primer agente.
