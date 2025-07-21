# 🧾 UiPath - Resumen de Logs por Sucursal

Este proyecto en UiPath permite procesar un archivo de logs (`Logs.xlsx`), filtrar registros por sucursal y generar un resumen con el número de capturas exitosas y una agrupación de errores con su respectiva descripción.

## 📁 Estructura del Proyecto

- `Main.xaml` – Flujo principal que realiza el procesamiento.
- `Registros/Logs.xlsx` – Archivo fuente con la información de registros por sucursal.

## 🔄 Flujo General

1. **Lectura del Excel**: Se abre el archivo `Logs.xlsx` y se lee la hoja `Docs`.
2. **Identificación de Sucursales**: Se extrae una lista única de sucursales encontradas en la columna `SUCURSAL`.
3. **Procesamiento por Sucursal**:
   - Se filtran los registros por sucursal.
   - Se cuentan las capturas exitosas (`ESTATUS` contiene “EXITOSA”).
   - Se filtran y agrupan los errores según el campo `CODIGO ERROR`.
   - Se construye un resumen textual con el total de capturas exitosas y errores con descripción.
4. **Descripciones de Errores**:
   - Se usa un `Switch` para asignar descripciones legibles a ciertos códigos de error.
   - Si el código no está definido, se indica: `"Descripción no disponible"`.
5. **Log Final**: Se muestra el resumen de cada sucursal en el panel de Output de UiPath.

## ✅ Requisitos

- UiPath Studio instalado
- Excel instalado (o soporte para manipulación de archivos `.xlsx`)
- Paquetes NuGet:
  - `UiPath.Excel.Activities`
  - `UiPath.System.Activities`

## 📄 Estructura Esperada del Excel

La hoja `Docs` debe tener las siguientes columnas:
- `SUCURSAL`
- `ESTATUS`
- `CODIGO ERROR`

## 📝 Ejemplo de Salida
Sucursal: KIA Tláhuac
Capturas exitosas: 3
Errores: Total (2)
5032 (1) - No se ha realizado los intercambios
0001 (1) - Falta número exterior

## ⚙️ Personalización

Para agregar más códigos de error y sus descripciones, edita el bloque `Switch (GetDescripcionError)` dentro del flujo y añade nuevas entradas.

## 📌 Notas

- Si una sucursal no tiene errores, se omite la agrupación.
- Si una sucursal no tiene capturas exitosas, el conteo será 0.

---

Este proyecto es útil para automatizar el resumen de procesamiento por unidad operativa, especialmente en escenarios donde hay múltiples errores operacionales que deben ser monitoreados.

## 👤 Autor

📌 Desarrollado por **Jorge Cazarez**, Desarrollador RPA – Soporte en **Cyborg Consulting**  
📍 Enrique Rébsamen 925, Col. Narvarte Poniente, Benito Juárez, C.P. 03020  
📞 776-115-25-74  
✉️ jorge.cazarez@cyborgconsulting.com.mx
