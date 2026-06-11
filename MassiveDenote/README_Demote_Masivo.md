# Script iLogic: Demote Masivo de Piezas a Subensamblajes

## Descripción
Este script de iLogic para Autodesk Inventor automatiza la operación de "Demote" (degradar) para múltiples piezas en un solo paso. Busca todas las piezas (Parts) individuales ubicadas en el primer nivel del árbol del ensamblaje activo, crea un nuevo documento de subensamblaje para cada una, coloca la pieza en su interior respetando el origen y sustituye la ocurrencia en el ensamblaje principal.

## Requisitos Previos
* Autodesk Inventor (probado en versiones recientes).
* Un ensamblaje (`.iam`) activo y abierto.
* **Crucial:** El ensamblaje principal debe estar guardado previamente. El script utiliza la ruta de este archivo principal para guardar los nuevos subensamblajes generados en el mismo directorio.

## Instrucciones de Uso
1. Abre tu ensamblaje en Autodesk Inventor.
2. Ve a la pestaña **Administrar** (Manage) y abre el panel de **iLogic**.
3. Haz clic derecho en la pestaña **Reglas** (Rules) del navegador de iLogic y selecciona **Añadir Regla** (Add Rule).
4. Asigna un nombre a la regla (por ejemplo, `Demote_Masivo`).
5. Pega el código del script en el editor de texto de iLogic.
6. Haz clic en **Guardar y Ejecutar** (Save & Run).

## Consideraciones Importantes
* **Pérdida de Restricciones (Constraints):** Al reemplazar ocurrencias vía la API de Inventor, las restricciones de ensamblaje que tenía la pieza original se pierden debido al cambio de topología. El script fija (*Ground*) las piezas automáticamente dentro de sus nuevos subensamblajes para asegurar estabilidad.
* **Posicionamiento Geométrico:** La matriz de transformación original se hereda de manera exacta. Cada pieza mantendrá su misma posición visual y de coordenadas en el espacio tridimensional del ensamblaje principal.
* **Dimensiones y Escalas:** La geometría física del modelo se mantiene completamente intacta. El proceso de empaquetado no altera la escala, respetando con precisión el sistema de unidades original con el que se modeló la pieza (ya sean dimensiones precisas en milímetros (mm) o en pulgadas (inches)).
* **Archivos Generados:** Los nuevos ensamblajes se nombrarán usando el formato `[NombreDeLaPieza]_Demoted_[Número].iam` para evitar la sobrescritura accidental de archivos existentes.

## Limitaciones
* Actualmente, el script solo actúa sobre componentes del **primer nivel** del árbol (raíz del ensamblaje principal).
* Solamente degrada documentos de piezas (`.ipt`), ignorando los subensamblajes existentes.
