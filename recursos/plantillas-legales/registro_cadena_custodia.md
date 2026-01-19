## REGISTRO DE CADENA DE CUSTODIA DE EVIDENCIA DIGITAL

**Número de Caso/Incidente:** `[IR-XXXX]`
**Cliente:** `[Nombre del Cliente]`
**Descripción Breve del Incidente:** `[Ej: Presunta infección de ransomware en equipo principal del CEO]`

**Técnico Responsable (Custodio Inicial):** `[Tu Nombre]`
**Firma del Custodio Inicial:** _________________________
**Fecha de Apertura del Registro:** `[Fecha]`

---

### INSTRUCCIONES:
1.  Cada ítem de evidencia física (USB, disco duro) o archivo lógico (imagen de memoria, carpeta de artefactos) **DEBE tener su propia fila** en esta tabla.
2.  **NUNCA** deje una fila en blanco. Si un campo no aplica, escriba "N/A".
3.  **Cada vez que la evidencia cambie de custodia**, el custodio que la entrega y el que la recibe **DEBEN firmar** en las columnas correspondientes.

---

### TABLA DE REGISTRO DE CUSTODIA

| # Ítem | Descripción de la Evidencia | Ubicación/Fuente Original | Fecha/Hora (UTC) Recolección | Hash (SHA-256) | Firma Recolector | Firma Receptor | Observaciones |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `[Ej: Disco SSD externo, Sandisk Extreme, S/N: X123YZ]` | `[Comprado para este caso]` | `[DD/MM/AAAA HH:MM]` | `[N/A para dispositivo nuevo]` | `[Tu Firma]` | `[N/A]` | `USB C "EVIDENCIA". Cifrado BitLocker.` |
| 2 | `[Archivo: memoria_2026-01-18_acme.mem]` | `[Volcado de RAM del equipo "CEO-PC"]` | `[DD/MM/AAAA HH:MM]` | `[Ej: a1b2c3d4...]` | `[Tu Firma]` | `[N/A]` | `Capturado con FTK Imager v4.7.1.` |
| 3 | `[Carpeta: _KAPE_OUTPUT]` | `[Extracción de artefactos del disco C:\]` | `[DD/MM/AAAA HH:MM]` | `[Ej: f7g8h9i0...]` | `[Tu Firma]` | `[N/A]` | `Generado con KAPE v2.0.` |
| 4 | `[Ej: Disco duro original, WD Blue, S/N: W789ABC]` | `[Equipo afectado "CEO-PC"]` | `[DD/MM/AAAA HH:MM]` | `[N/A - Disco fuente]` | `[Tu Firma]` | `[N/A]` | `Disco retirado para preservación.` |
| ... | `[...]` | `[...]` | `[...]` | `[...]` | `[...]` | `[...]` | `[...]` |
| X | `[DEVOLUCIÓN / DESTRUCCIÓN]` | `[Todos los ítems listados]` | `[DD/MM/AAAA HH:MM]` | `[N/A]` | `[Firma Custodio]` | `[Firma Cliente]` | `Evidencia entregada al cliente.` |

---

### DECLARACIONES Y TÉRMINOS:

1.  **Propósito:** Este documento tiene como único objetivo **rastrear la posesión, ubicación y manipulación** de la evidencia digital relacionada con el caso referenciado, desde su recolección hasta su disposición final.
2.  **Integridad:** Cualquier **interrupción, laguna o falta de firma** en este registro puede comprometer la integridad legal de la evidencia y será documentada en la sección de Observaciones.
3.  **Acceso:** El acceso a la evidencia física y lógica **está restringido** únicamente al personal autorizado cuyo nombre y firma aparecen en este registro.
4.  **Almacenamiento:** La evidencia física se almacenará en un **área segura y controlada** cuando no esté bajo análisis. La evidencia lógica se almacenará en medios cifrados.
5.  **Disposición Final:** La evidencia será devuelta al cliente, destruida o archivada según lo acordado en el Acuerdo de Servicio y documentado en la última fila de esta tabla.

---

**Este registro es un anexo inseparable del Acuerdo de Servicio IR y del Informe Final del Incidente.**
