# 🚨 PROTOCOLO DE INCIDENTES - EJECUCIÓN EN CAMPO v2.3 ESPECIALISTA

> **TÚ ERES EL EXPERTO INDEPENDIENTE**
> No hay supervisores. Tú tomas TODAS las decisiones basándote en evidencia técnica.
> Tu reputación depende de la calidad de tu análisis y reporte final.

---

## ✅ PRE-REQUISITOS ANTES DE LLEGAR

- [ ] Tienes los 3 USBs listos y testeados? ✅
- [ ] Has leído "KIT_Preparacion_v2.3_ESPECIALISTA.md"? ✅
- [ ] Tienes 5-8 horas libres sin interrupciones?
- [ ] Contacto del cliente anotado (teléfono, email)?
- [ ] Libreta + bolígrafo para documentar?
- [ ] Cámara/móvil para fotografías?

---

## 🚨 FASE 0: LLEGADA Y CONTENCIÓN (T+0 a T+10 min)

**Objetivo:** Preservar evidencia. Contener la amenaza. Tu primera impresión cuenta.

### Acción 0.1: Observación Inicial y Documentación

- [ ] **NO TOQUES NADA.** Observa primero.
- [ ] Abre libreta y anota la HORA EXACTA
- [ ] **¿Qué ves en pantalla?**
  - ¿Mensaje de rescate? (RANSOMWARE - esto es GRAVE)
  - ¿Pantalla azul? (Error crítico o BSOD)
  - ¿Programas abriendo/cerrando solos?
  - ¿Archivos con extensiones extrañas? (.encrypted, .locked, .xyz)
  - ¿Desktop visible o está todo congelado?
  - ¿Sonido de escaneador activo? (disco trabajando)
- [ ] **Anota observaciones iniciales:** "Visto ransomware-like note, archivos con extensión .crypto, sistema congelado a las 14:32"

### Acción 0.2: Fotografía de Evidencia (CRÍTICO)

- [ ] **Abre cámara o móvil**
- [ ] **Fotografía LA PANTALLA COMPLETA** capturando:
  - Texto de nota de rescate (si existe)
  - Programas abiertos
  - Hora del sistema (visible en bandeja)
  - Extensiones de archivos raras (si son visibles)
  - Estado general del escritorio
- [ ] Toma MÍNIMO 3 fotos desde ángulos diferentes
- [ ] **Apunta en libreta:** "Foto 1 - Pantalla completa, Hora exacta: 14:32:45"
- [ ] **Después de incidente:** Calcula hash SHA256 de cada foto
  ```
  certutil -hashfile "IMG_001.jpg" SHA256
  ```
- [ ] Guarda hashes en `USB C:/_REPORTS/foto_hashes.txt`

**Por qué:** La foto es evidencia legal. Su hash verifica que no la modificaste.

---

### Acción 0.3: Corta La Conexión (CRÍTICO - AISLAMIENTO)

**Objetivo:** Impedir que malware siga comunicándose con C2 o borre logs.

- [ ] **Desconectar cable Ethernet (Físico)**
  - Desenchufa el cable RJ45 del PC del cliente
  - NO simplemente "desconectas" desde software (malware podría anularlo)
  - Anota en libreta: "Ethernet desconectado 14:33"

- [ ] **Apaga Wi-Fi (Físico si es posible)**
  - Si laptop tiene botón físico de Wi-Fi: Presiona OFF
  - Si no: Abre Settings > Redes e internet > Wi-Fi > Desactivado
  - Verifica que el icono Wi-Fi en bandeja desaparezca
  - Anota: "Wi-Fi desactivado 14:34"

- [ ] **Desactiva Bluetooth**
  - Settings > Bluetooth > Desactivado
  - Anota: "Bluetooth desactivado 14:34"

- [ ] **VERIFICA:** Ningún icono de red activo en bandeja ✓
  - No debe haber Wi-Fi, no debe haber conexión ethernet
  - Si ves algo: Re-verifica

**Por qué:** Si no ciertas conexión, malware sigue hablando con atacantes en vivo.

---

### Acción 0.4: Aislamiento Físico

- [ ] **Desconecta pendrives o discos duros EXTERNOS**
  - Si hay pendrives conectados: Desenchufa (con cuidado, usando eyector primero)
  - Si hay discos duros externos: Desenchufa
  - **Etiqueta cada uno:** "Pendrive 1", "Disco Externo A", etc
  - Anota en libreta lista de dispositivos encontrados
- [ ] **NO TOQUES estos dispositivos** (podrían tener malware también)
- [ ] **NO los conectes a tu máquina** (hasta analizarlos)

---

### Acción 0.5: Inicial Assessment - ¿Severidad?

En tu libreta, anota AHORA una evaluación rápida:

```
SEVERIDAD INICIAL:
❌ CRÍTICO - Ransomware (archivos encriptados, nota rescate visible)
❌ ALTO - APT/C2 (conexiones sospechosas, procesos raros)
⚠️ MEDIO - Malware commodity (lento, popups, pero funciona)
✅ BAJO - PUP/Adware (molestos pero no graves)

[Anota cuál crees que es]

Evidencia que viste:
- [Qué indica severidad]
```

Esto te ayuda a priorizar pasos.

---

## 🧠 FASE 1: PRESERVAR LA MEMORIA (T+10 a T+60 min)

**Objetivo:** Capturar la RAM COMPLETA. Esta es evidencia forense crítica que desaparece si apagas PC.

**POR QUÉ ES CRÍTICO:**
- Malware fileless (vive en RAM, no en disco)
- Keys de encriptación (si es ransomware)
- Credenciales y tokens activos
- Procesos inyectados que no ves en disco
- Conexiones de red activas a C2

### Acción 1.1: Conectar USBs

- [ ] **Conecta USB A** ("El Escudo" - debe estar en LOCK)
  - Puerto USB trasero si es escritorio (más estable)
  - Cualquier puerto disponible si es laptop
- [ ] Anota en libreta: "USB A conectado 14:35"

- [ ] **Conecta USB C** ("La Evidencia" - necesita escritura)
  - Puerto USB diferente a USB A
- [ ] Anota: "USB C conectado 14:35"

- [ ] **Verifica en Windows:**
  - Abre Explorador
  - ¿Ves los 2 USBs? (USB A con pestaña LOCK, USB C sin protección)
  - Si no los ves: Intenta puertos USB 3.0 (más rápidos)

---

### Acción 1.2: Abre FTK Imager

- [ ] **Navega a:**
  ```
  USB A:/_IR_KIT/FTK Imager/
  ```
- [ ] **Haz doble click en:**
  ```
  FTK Imager.exe
  ```
- [ ] **Windows pide permiso:** Click **SÍ** (necesita admin para acceder a RAM)
- [ ] **Espera 10-20 segs** a que abra interfaz

---

### Acción 1.3: Configura Captura de Memoria

**En el menú de FTK:**

- [ ] Menú **File** > **Capture Memory...**
- [ ] Abre ventana de configuración

**RELLENA CADA CAMPO:**

| Campo | Valor | Notas |
|-------|-------|-------|
| **Destination Path** | USB C (browse y elige carpeta `_DUMPS/`) | Aquí guardará memoria |
| **Destination Filename** | `memoria_FECHA_CLIENTE.mem` | Ej: `memoria_2026-01-18_acme.mem` |
| **Include pagefile** | ✅ MARCADO | Captura datos intercambiados en disco |
| **Create AD1 file** | ❌ DESMARCADO | No necesario para análisis rápido |

- [ ] Anota en libreta: "FTK configurado, RAM [tamaño], destino USB C"

---

### Acción 1.4: Inicia Captura

- [ ] Click en **Capture Memory**
- [ ] **Barra de progreso verde aparece**
- [ ] **NO TOQUES NADA. Espera a que termine.**
- [ ] En libreta: "Captura iniciada 14:37"

### Acción 1.5: Monitorea Progreso

**Mientras corre (puede tardar 15-45 mins):**

- [ ] Observa:
  - **Velocidad:** ¿Va rápido o lento?
  - **Errores:** ¿Sale algo rojo?
  - **ETA:** ¿Cuánto tiempo queda?

- [ ] **SI tarda >60 MINS:** 
  - Posible problema con USB (lento)
  - Cancela presionando CTRL+C
  - Prueba con USB B (si es disponible)
  - O continúa con FASE 2 mientras acabas captura en background

### Acción 1.6: Verifica Captura

- [ ] Cuando aparezca **"Finished successfully"** ✓
- [ ] Cierra FTK Imager
- [ ] Abre Explorador en USB C:
  ```
  USB C:/_DUMPS/
  ```
- [ ] **Verifica:**
  - [ ] Archivo `memoria_FECHA_CLIENTE.mem` existe
  - [ ] Tamaño es similar a RAM de cliente (ej: si tiene 16GB RAM, archivo ~16GB)
  - [ ] Hash: Calcula y anota
    ```
    certutil -hashfile "memoria_FECHA_CLIENTE.mem" SHA256
    ```
    Guarda hash en libreta y en `USB C:/_REPORTS/memoria_hash.txt`

- [ ] En libreta: "Captura terminada exitosamente 14:52, hash verificado"

**¿Por qué el hash?** Verifica que el archivo no fue modificado después. Es evidencia legal.

---

## 🔍 FASE 2: TRIAGE & DIAGNÓSTICO (T+60 a T+180 min)

**Objetivo:** Identificar amenaza específica. Tu análisis determina estrategia de limpieza.

**Decisiones que tomarás aquí:**
- ¿Es ransomware? → Estrategia diferente
- ¿Es APT/C2? → Documentar IOCs profesionalmente
- ¿Es malware commodity? → Limpieza estándar

### Acción 2A: System Informer (Análisis de Procesos)

- [ ] Abre terminal CMD o PowerShell
- [ ] Navega a:
  ```
  USB A:/_IR_KIT/SystemInformer/SystemInformer.exe
  ```
- [ ] **Click derecho > Run as administrator**

- [ ] Interfaz abre (verás árbol de procesos)
- [ ] Tab **"Processes"** (si no está ya ahí)
- [ ] Ordena por **"CPU"** o **"Name"** para ver actividad

- [ ] **BUSCA INDICADORES SOSPECHOSOS:**

  **🔴 ROJO/ROSA = Sin firma digital (Microsoft)**
  - Haz clic en proceso
  - ¿Muestra "Microsoft Corporation"? → Legítimo
  - ¿Muestra "Unverified" o no muestra publisher? → ❌ SOSPECHOSO
  - Anota en libreta: "[PROCESO].exe - Unverified, en [RUTA]"

  **🔵 AZUL CYAN = Packed/Comprimido**
  - Posible malware obfuscado
  - Anota: "[PROCESO].exe - Packed/Compressed"

  **AppData ejecutables:**
  - ¿Hay `.exe` en `C:\Users\[Usuario]\AppData\Local\Temp\`?
  - ¿O en `C:\Users\[Usuario]\AppData\Roaming\`?
  - Eso NO es normal para software legítimo
  - Anota ruta completa

  **Svchost falsos:**
  - Busca procesos `svchost.exe`
  - Pon ratón encima para ver tooltip
  - Si NO dice "Microsoft Corporation" → ❌ FAKE svchost (malware)
  - Anota: "Fake svchost detected"

- [ ] **Network Connections Tab:**
  - ¿Hay conexiones a IPs externas raras?
  - Anota IPs: "Conexión a 192.168.1.50 port 4444"
  - Busca IPs en AbuseIPDB después

- [ ] Cierra System Informer
- [ ] En libreta: "System Informer completado 15:05"

**Tiempo:** ~5 mins

---

### Acción 2B: HollowsHunter (Detección de Inyecciones)

- [ ] Abre CMD
- [ ] Navega a:
  ```
  USB A:/_IR_KIT/hollows_hunter64.exe
  ```
- [ ] **Ejecuta (click derecho > Run as admin)**

- [ ] **Consola negra aparece** (está escaneando)
- [ ] **ESPERA A QUE SE CIERRE SOLA** (no cierres manualmente)
  - Tiempo: 2-5 mins típicamente
  - Está buscando procesos con code injection (técnica APT)

- [ ] **Cuando se cierre, abre carpeta generada:**
  ```
  C:\Users\[Tu nombre]\AppData\Roaming\hollows_hunter\scan_report\
  ```

- [ ] **Abre archivo `summary.json`** con Bloc de notas

- [ ] **BUSCA esta línea:**
  ```json
  "suspicious": 0
  ```
  - **SI = 0:** Bien, sin inyección avanzada detectada ✓
  - **SI > 0:** ❌ HAY INYECCIÓN, procesos están comprometidos GRAVE

- [ ] Anota en libreta: "HollowsHunter: suspicious = [número]"

- [ ] **Si hay inyección:**
  - Copia `summary.json` a `USB C:/_REPORTS/hollows_hunter_summary.json`
  - Abre `report.html` también y cópialo

**Tiempo:** ~5 mins

---

### Acción 2C: Thor Lite (Scanner APT)

- [ ] Abre CMD
- [ ] Navega a:
  ```
  USB A:/_IR_KIT/thor/thor64-lite.exe
  ```
- [ ] **Ejecuta (click derecho > Run as admin)**

- [ ] **¿Qué pasa?**
  - **Opción A:** Se abre ventana, empieza escaneo → Perfecto, espera
  - **Opción B:** Error `"License file not found"` → Salta a Acción 2D (RogueKiller)

- [ ] **Si está escaneando:**
  - Verás output en consola blanca
  - Tiempo: 20-30 mins típicamente
  - **BUSCA LÍNEAS ROJAS** en consola:
    - `ALERT:` algo detectado
    - `C2:` comunicación maliciosa
    - `Webshell:` backdoor web
    - Anota CADA línea roja: "Linea roja detectada: [texto completo]"

  - **SI TARDA >50 MINS:** Cancela (CTRL+C). Continúa con siguientes.

- [ ] Cuando termine: Cierra Thor
- [ ] Busca reporte:
  ```
  C:\ProgramData\thor\logs\
  ```
  - Copia archivo `.html` más reciente a `USB C:/_REPORTS/thor_report.html`

- [ ] En libreta: "Thor completado 15:35"

**Tiempo:** 20-30 mins (o menos si error de licencia)

---

### Acción 2D: RogueKiller (Anti-Malware General)

- [ ] Abre:
  ```
  USB A:/_IR_KIT/RogueKiller/RogueKiller_portable64.exe
  ```
- [ ] **Click derecho > Run as admin**

- [ ] Interfaz se abre (puede tardar 10-20 segs)
- [ ] **Click en botón grande azul "Scan"**
- [ ] **ESPERA escaneo** (5-15 mins según tamaño disco)

- [ ] **Verás resultados en árbol:**
  - 🟢 **VERDE (Clean):** Archivo/proceso limpio
  - 🟡 **AMARILLO (PUP):** Adware, toolbar, potencialmente no deseado
  - 🔴 **ROJO (Malware):** Virus, troyano, CONFIRMADO malicioso

- [ ] **Si hay ROJO:**
  - Anota CADA elemento rojo: "Nombre: [exacto], Ruta: [donde está], Tipo: [Malware tipo]"
  - Ejemplo: "Name: TrojanDropper.XYZ, Path: C:\Users\CEO\AppData\Local\Temp\virus.exe, Type: Trojan.Dropper"

- [ ] **Copia reporte:**
  - Click derecho > Export Report (si existe opción)
  - O: Busca en carpeta de ejecución por archivo `.html`
  - Copia a `USB C:/_REPORTS/roguekiller_report.html`

- [ ] **NO HAGAS NADA TODAVÍA** (no elimines nada aún)
- [ ] Cierra RogueKiller

**Tiempo:** 10-15 mins

---

### Acción 2E: KAPE (Extracción de Artefactos Forenses)

**Este es el paso que diferencia especialista de aficionado.**

- [ ] Abre CMD (modo Admin)
- [ ] Navega a KAPE:
  ```cmd
  cd USB A:\_IR_KIT\KAPE\
  ```

- [ ] **Ejecuta comando (copiar exacto):**
  ```cmd
  kape.exe --tsource C: --tdest "USB C:\_KAPE_OUTPUT" --tl EvidenceOfExecution,BrowserHistory,AccountUsage --flush
  ```
  (Reemplaza `USB C:` con letra correcta si es diferente)

- [ ] **¿Qué hace?**
  - Extrae automáticamente: Event Logs, Prefetch, MRU, Registry, Browser history
  - Organiza en carpetas por tipo
  - Tarda 5-15 mins

- [ ] **Monitorea progreso:**
  - Verás output en terminal
  - Está bien si muestra `warnings` (son informativas)

- [ ] **Cuando termine:**
  ```
  Completed successfully
  ```

- [ ] **Verifica en USB C:**
  ```
  USB C:\_KAPE_OUTPUT\
  ```
  - Debe haber carpetas: `_Execution\`, `_BrowserHistory\`, `_AccountUsage\`, `_Registry\`
  - Estos contienen prefetch, browser history, Event Logs, etc.

- [ ] **Anota hallazgos importantes:**
  - Ej: "Prefetch muestra powershell.exe ejecutado a las 14:10 UTC"
  - Ej: "Browser history muestra visita a malware-hosting-site.com a las 14:05"

**Tiempo:** 10-15 mins

---

### Acción 2F: YARA Scan (Pattern Matching Avanzado)

**Solo si encontraste archivos sospechosos en RogueKiller.**

- [ ] ¿Hay archivos rojo/amarillo en RogueKiller? 
  - **SÍ:** Continúa
  - **NO:** Salta a FASE 3

- [ ] Abre CMD (Admin)
- [ ] Navega a YARA:
  ```cmd
  cd USB A:\_IR_KIT\yara\
  ```

- [ ] **Para CADA archivo sospechoso, ejecuta:**
  ```cmd
  yara.exe -r rules\ "RUTA_COMPLETA_DEL_ARCHIVO"
  ```
  
  Ejemplo:
  ```cmd
  yara.exe -r rules\ "C:\Users\CEO\AppData\Local\Temp\sospechoso.exe"
  ```

- [ ] **¿Qué significa?**
  - Si ves output tipo: `Trojan.XYZ C:\Users\...` → Detectado malware conocido
  - Si sin output → No en rules conocidas (pero puede seguir siendo malware)

- [ ] Anota CADA match: "YARA match: [familia malware] en [ruta]"

**Tiempo:** 5 mins por archivo

---

### ⚠️ DECISIÓN CRÍTICA: ¿Qué tipo de malware es?

**Basándote en hallazgos, decide:**

```
ÁRBOL DE DECISIÓN - TÚ DECIDES BASÁNDOTE EN EVIDENCIA
```

#### **¿DETECTASTE RANSOMWARE?**

**Evidencia de ransomware:**
- RogueKiller dice "Ransomware" (específica familia)
- Archivos con extensiones `.encrypted`, `.locked`, `.crypto`, etc.
- Archivo de nota rescate (`DECRYPT_ME.txt`, `README_NOW.txt`, `HOW_TO_RECOVER.txt`)
- Procesos relacionados (ej: `7za.exe`, `rar.exe` = compresores para cifrar)

**DECISIÓN TUYA (no hay "llamar a alguien"):**

Analiza:
- ¿Qué familia de ransomware es? (Conti, LockBit, Blackcat, etc)
- ¿Cuántos archivos afectados aproximadamente?
- ¿Hay backups disponibles del cliente? (Pregunta)
- ¿Es recuperable o necesita data recovery service?

**Tu evaluación en libreta:**
```
RANSOMWARE DETECTED:
Familia: [Nombre específico]
Extensión: [.ext]
Archivos afectados: ~[%]
Nota rescate: SÍ/NO
Backups disponibles: SÍ/NO

RECOMENDACIÓN:
- Restaurar desde backup más reciente anterior a infección
- Si no hay backups: Data recovery service profesional (explicar opciones)
- NO pagar rescate (comunica riesgos)
```

**ACCIÓN EN FASE 3:** Salta a FASE 3-B (CAINE para rescate de datos, NO limpieza)

---

#### **¿DETECTASTE APT / C2?**

**Evidencia de APT:**
- Thor detectó "C2 detected" o "Webshell found"
- System Informer muestra conexiones a IPs externas sospechosas
- HollowsHunter detectó `suspicious > 5` (inyección avanzada)
- YARA matchea APT families conocidas (Lazarus, APT28, etc)

**DECISIÓN TUYA:**

Analiza:
- ¿Qué IPs/dominios C2?
- ¿Cuántos procesos inyectados?
- ¿Hay lateral movement evidente? (archivos copiados a otros PCs?)
- ¿Cuándo empezó? (Timeline de KAPE)

**Tu evaluación en libreta:**
```
APT/C2 DETECTED:
Indicadores:
- C2 connections: [IPs/dominios]
- Inyecciones: [PIDs afectados]
- Timeline: [Cuándo inició]
- Lateral movement: [Evidencia]

RECOMENDACIÓN:
- Aislamiento inmediato de red
- Cambio de credenciales (contraseñas, tokens)
- Auditoría de otros PCs en red
- Considerar forensics profundos y threat hunting
- Posible implicación legal/policial (depende alcance)
```

**ACCIÓN EN FASE 3:** Limpieza + documentación IOCs para entregarle

---

#### **¿SOLO MALWARE COMMODITY?**

**Evidencia:**
- RogueKiller detecta malware genérico (Trojan, Worm, PUP, Spyware)
- Sin C2 confirmado
- Sin inyecciones avanzadas
- Sin ransomware

**DECISIÓN TUYA:**

Procede con confianza:
- Es problema solucionable
- Limpieza estándar funciona
- Probabilidad alta de éxito

**Tu evaluación en libreta:**
```
MALWARE COMMODITY:
Tipo: [Trojan/Worm/PUP/Spyware]
Ejemplos: [Nombres específicos si detectó varios]
Severidad: Media (sistema lento pero usable)

RECOMENDACIÓN:
- Limpieza offline con KRD
- Verificación post-limpieza
- Cambio de credenciales por precaución
- Análisis forense completo post-incident
```

**ACCIÓN EN FASE 3:** Limpieza normal (KRD)

---

## 💀 FASE 3: CIRUGÍA OFFLINE (T+180 a T+240 min)

**Objetivo:** Eliminar amenazas. Tú decides estrategia basándote en diagnóstico previo.

### Acción 3.0: Apagado Seguro

- [ ] **Apagado forzoso:** Mantén botón Power 10 segundos
- [ ] PC se apaga
- [ ] Espera 5 segundos (asegura cierre)
- [ ] En libreta: "PC apagado 16:05"

---

### Acción 3-A: KRD (Si Windows arranca NORMAL)

**Requisito:** Windows inicia sin bucles de reinicio

- [ ] **Conecta USB B** ("El Quirófano")
- [ ] **Reinicia PC**, presiona **F12** (o F9/DEL según fabricante)
- [ ] Menú Boot aparece
- [ ] Selecciona **USB B** en la lista
- [ ] Enter

- [ ] **Menú Ventoy aparece** con 3 ISOs
- [ ] Selecciona **"Kaspersky Rescue Disk"**
- [ ] Enter

- [ ] **KRD carga** (30-60 segs)
- [ ] Interfaz gráfica aparece

- [ ] **Click "Scan All Drives"** (o similar)
- [ ] Espera escaneo (15-45 mins)

- [ ] **Si encuentra malware (líneas rojas):**
  - Selecciona cada uno
  - Click **"Delete"** o **"Quarantine"**
  - O: "Delete All" si hay muchos

- [ ] Cuando KRD termine: Reinicia a Windows
- [ ] En libreta: "KRD limpieza completada 16:45"

---

### Acción 3-B: CAINE (Si Windows NO arranca)

**Requisito:** Windows con bucles de reinicio o errors críticos

- [ ] USB B sigue conectado
- [ ] Reinicia, presiona F12
- [ ] Menú Ventoy, selecciona **"CAINE"**
- [ ] Espera carga (2-3 mins)

- [ ] **Escritorio Linux aparece**
- [ ] En escritorio: Busca icono disco duro cliente (ej: "sda1")
- [ ] Clic derecho > **"Mount as Read-Only"**
- [ ] Carpeta abre (ves Windows folders)

- [ ] **Monta USB C:**
  - Busca icono USB C
  - Clic derecho > **"Mount as Writable"**

- [ ] **Rescata datos críticos:**
  ```
  C:\Users\[Cliente]\Documents → USB C/_RECUPERADO/
  C:\Users\[Cliente]\Desktop → USB C/_RECUPERADO/
  C:\Users\[Cliente]\Pictures → USB C/_RECUPERADO/
  ```
- [ ] Drag & drop o CP command
- [ ] Espera (5-30 mins)

- [ ] **Cuando termine:**
  - Unmount discos
  - Apaga CAINE
  - Saca USB B
  - Reinicia

- [ ] En libreta: "CAINE rescate completado, datos salvados"

**NOTA:** Este es rescate de datos, NO limpieza forense pura. Datos se recuperan pero pierdes algo de evidence chain.

---

## 🧹 FASE 4: LIMPIEZA & VALIDACIÓN (T+240 a T+360 min)

**Objetivo:** Asegurar que malware no vuelve. Verificar limpieza exitosa.

### Acción 4.1: Modo Seguro

- [ ] **En Windows:**
  1. Inicio > Botón Apagar
  2. Mantén **SHIFT** pulsado
  3. Click **"Reiniciar"**
  4. Menú azul: Solucionar problemas
  5. Opciones avanzadas
  6. Configuración de inicio
  7. Reiniciar
  8. Presiona **"4"** (Modo Seguro con red)

- [ ] Windows arranca en Safe Mode (verás en esquina)
- [ ] En libreta: "Safe Mode iniciado 17:10"

---

### Acción 4.2: Autoruns (Detección de Persistencia)

- [ ] Conecta **USB A**
- [ ] Abre:
  ```
  USB A:/_IR_KIT/Sysinternals/Autoruns64.exe (Admin)
  ```

- [ ] Interfaz: Lista de programas startup
- [ ] Menú Options > Scan Options:
  - [ ] Check VirusTotal.com
  - [ ] Verify Code Signatures

- [ ] Tabs a revisar: **Logon**, **Scheduled Tasks**, **Services**, **Image Hijacks**

- [ ] **BUSCA ROJO (malware confirmado):**
  - Líneas rojas = VirusTotal detectó malware
  - Anota CADA una: "[NOMBRE] - [RUTA] - VirusTotal positivo"

- [ ] **BUSCA amarillo/sospechoso:**
  - Rutas raras en `AppData\` o `Temp\`
  - Servicios con nombres falsos (ej: `svchost_v2`)
  - Anota: "[NOMBRE] - [RUTA] - Sospechoso"

- [ ] **ACCIÓN:**
  - Para cada rojo: Click derecho > **Delete** (elimina)
  - Para cada amarillo sospechoso: **Uncheck** (deshabilita, prueba después)

- [ ] Reinicia
- [ ] Si PC funciona bien: Vuelve a Autoruns, BORRA los deshabilitados

- [ ] En libreta: "Autoruns limpieza completada 17:25"

**Tiempo:** 10 mins

---

### Acción 4.3: RogueKiller Post-Limpieza (Verificación)

- [ ] Ejecuta nuevamente:
  ```
  USB A:/_IR_KIT/RogueKiller/RogueKiller_portable64.exe (Admin)
  ```

- [ ] Click "Scan"
- [ ] Espera resultado (5-15 mins)

- [ ] **¿RESULTADO?**
  - 🟢 **TODO VERDE:** Excelente, limpieza exitosa ✓✓✓
    - Anota en libreta: "RogueKiller post-limpieza: CLEAN ✓"
    - Continúa a acción 4.4
  - 🟡/🔴 **AÚN HAY AMARILLO O ROJO:** 
    - Anota lo encontrado
    - Continúa a acción 4.4 (Norton)

**Tiempo:** 10-15 mins

---

### Acción 4.4: Norton Power Eraser (Si sigue habiendo malware)

- [ ] **¿RogueKiller mostró todo verde?**
  - SÍ: Salta a acción 4.5
  - NO: Ejecuta Norton

- [ ] Abre:
  ```
  USB A:/_IR_KIT/Norton Power Eraser/NPE.exe (Admin)
  ```

- [ ] Click "Scan for Risks"
- [ ] Espera (10-30 mins)
- [ ] Si encuentra algo: Click "Fix" o "Repair"
- [ ] Si pide reiniciar: Permite (volverá solo)

- [ ] Cuando termine:
  - Cierra Norton
  - Reinicia Windows
  - En libreta: "Norton Power Eraser completado 17:50"

**Tiempo:** 20-30 mins

---

### Acción 4.5: Volatility Deep Dive (Análisis de Memoria - En tu casa después)

**NOTA IMPORTANTE:** Este análisis lo haces DESPUÉS en tu máquina personal. NO en campo.

- [ ] **En casa, después:**
  - Conecta USB C (tiene `memoria_FECHA.mem`)
  - Copia archivo a tu carpeta de trabajo
  - Terminal/bash:
    ```bash
    volatility3 -f memoria_FECHA.mem windows.pslist > pslist_output.txt
    volatility3 -f memoria_FECHA.mem windows.malfind > malfind_output.txt
    volatility3 -f memoria_FECHA.mem windows.netscan > netscan_output.txt
    ```
  - Analiza output
  - Copia resultados a `USB C:/_VOLATILITY_ANALYSIS/`

- [ ] **Documenta en tu REPORTE FINAL:**
  - Qué procesos raros encontraste
  - Qué inyecciones detectó
  - Qué conexiones de red había

---

## ✅ FASE 5: VALIDACIÓN Y CIERRE (T+360 a T+420 min)

**Objetivo:** Devolver sistema operativo, limpio y documentado profesionalmente.

### Acción 5.1: Reinicia Modo Normal

- [ ] Reinicia en **Modo Normal** (no Safe Mode)
- [ ] Desconecta USB A y USB C (PERO GUÁRDALOS)
- [ ] En libreta: "Reinicio a modo normal 18:15"

---

### Acción 5.2: Validación de Estabilidad

- [ ] **CPU:** Task Manager > Performance tab
  - ¿CPU <20% en reposo? ✓
  - ¿Memoria estable? ✓

- [ ] **Red:** Terminal
  ```cmd
  ping 8.8.8.8
  ```
  - ¿Responde? ✓

- [ ] **Windows Update:**
  - Settings > Windows Update
  - ¿Funciona? ✓

- [ ] **Errores recurrentes:**
  - Event Viewer > Errores
  - ¿Hay errores críticos nuevos? ❌
  - Si SÍ: Investiga, podría ser residual

- [ ] En libreta: "Validación: Sistema estable ✓"

---

### Acción 5.3: Cambio de Credenciales (OBLIGATORIO DESDE OTRO PC)

- [ ] **Cliente cambia contraseñas DESDE OTRO PC LIMPIO:**
  - Windows local
  - Correo corporativo
  - Servicios críticos (Teams, Outlook, VPN, etc)
  - Invalida tokens/API keys si aplica

- [ ] **En libreta:** "Cliente informado: cambiar contraseñas desde otro PC"

---

### Acción 5.4: Recuperación de Datos (Si falta algo)

**A. Archivos borrados (Word, Excel, Fotos)?**

- [ ] Ejecuta Recuva:
  ```
  USB A:/_IR_KIT/Recuva/recuva.exe
  ```
- [ ] Selecciona SOLO partición donde estaban
- [ ] Escaneo profundo
- [ ] Recupera a USB C (¡NUNCA al mismo disco!)

**B. Disco entero "desaparecido" (D: no aparece)?**

- [ ] Ejecuta TestDisk:
  ```
  USB A:/_IR_KIT/testdisk-7.2/testdisk_win.exe
  ```
- [ ] Pasos: Create Log > Selecciona disco > Intel partition > Analyze > Quick Search
- [ ] Si ve partición (verde): Write para restaurar
- [ ] Reinicia

---

### Acción 5.5: Crea REPORTE FINAL PROFESIONAL

**Este es TU valor como especialista. El reporte debe ser impecable.**

Crea documento Word/PDF con estructura profesional:

```markdown
═══════════════════════════════════════════════════════════
REPORTE DE RESPUESTA A INCIDENTE - CONFIDENCIAL
═══════════════════════════════════════════════════════════

DATOS DEL INCIDENTE
─────────────────
Fecha: [DD/MM/AAAA]
Hora Inicio: [HH:MM UTC]
Hora Fin: [HH:MM UTC]
Duración Total: [X horas Y minutos]
Técnico: [Tu nombre]
Cliente: [Nombre empresa/persona]
Contacto: [Teléfono/Email]

─────────────────────────────────────────────────────────

RESUMEN EJECUTIVO
──────────────
[2-3 párrafos: qué pasó, severidad, resolución]

Ejemplo:
"El 18 de enero de 2026 se detectó infección por malware 
de tipo [Trojan/Ransomware/APT]. El sistema fue aislado, 
diagnosticado, y limpiado exitosamente. Se recuperaron 
todos los datos críticos. Se recomienda implementar 
controles preventivos inmediatos."

─────────────────────────────────────────────────────────

MALWARE DETECTADO
──────────────
Nombre (COMPLETo): [ej: Trojan.Emotet.A]
Familia: [ej: Emotet, Conti, Lazarus]
Tipo: [Ransomware / APT / Trojan / Worm / PUP / etc]
Severidad: [CRÍTICA / ALTA / MEDIA / BAJA]

Cantidad detectada: [X instancias]
Ubicaciones principales:
- [Ruta 1]
- [Ruta 2]
- [Ruta 3]

─────────────────────────────────────────────────────────

INDICADORES DE COMPROMISE (IOCs)
───────────────────────────────
IP Maliciosas detectadas:
- 192.168.X.X:PUERTO [Detectado por: Thor/System Informer]
- 10.0.X.X:PUERTO

Dominios C2:
- malware-domain.ru [Detectado por: Thor]
- c2-server.com

Hashes MD5/SHA256 de archivos maliciosos:
- SHA256: a1b2c3d4... (archivo.exe)
- MD5: e5f6g7h8...

Extensiones de archivo cifradas (si ransomware):
- .encrypted
- .locked
- .crypto

─────────────────────────────────────────────────────────

TIMELINE DE INFECCIÓN (Basado en KAPE/Volatility)
──────────────────
14:00 UTC - Primeros indicios en Prefetch
14:10 UTC - Browser descarga malware desde [sitio]
14:15 UTC - Archivo .exe ejecutado (Prefetch)
14:20 UTC - Inicio de inyecciones de código (HollowsHunter)
14:30 UTC - Primera conexión C2 (System Informer)
14:45 UTC - Actividad lateral en red (si aplica)
[Continúa con eventos clave]

─────────────────────────────────────────────────────────

ANÁLISIS DE IMPACTO
─────────────────
Archivos afectados:
- Total: [Número aproximado]
- Tipo: [Documentos Word/Excel/PDF/etc]
- Ubicaciones: [Directorios principales]

Sistemas comprometidos:
- PC principal: CRÍTICO
- Servidor file share: ALTO (investigar)
- Otros PCs en red: [Investigación recomendada]

Datos potencialmente exfiltrados:
- [Listar qué tipos de datos viajarían por conexión C2]
- Ej: Credentials, email data, financial docs
- Recomendación: Cambio de credenciales inmediato

─────────────────────────────────────────────────────────

MÉTODOS DE LIMPIEZA APLICADOS
────────────────────────────
1. Aislamiento de red (Ethernet/Wi-Fi/Bluetooth desconectados)
2. Captura forense de RAM (FTK Imager - memoria_[fecha].mem)
3. Análisis de procesos (System Informer)
4. Detección de inyecciones (HollowsHunter)
5. Scanner APT (Thor Lite)
6. Anti-malware (RogueKiller)
7. Extracción de artefactos (KAPE - Event Logs, Prefetch, Registry)
8. Limpieza offline (Kaspersky Rescue Disk)
9. Detección de persistencia (Autoruns)
10. Anti-rootkit (Norton Power Eraser)
11. Análisis de memoria (Volatility 3)

Estados de verificación:
- [X] HollowsHunter post-limpieza: CLEAN
- [X] RogueKiller post-limpieza: CLEAN
- [X] Autoruns: Persistencia eliminada
- [X] Norton Power Eraser: Rootkits eliminados

─────────────────────────────────────────────────────────

ESTADO FINAL
──────────
✓ Sistema operativo: LIMPIO
✓ Rendimiento: NORMAL
✓ Conectividad: OPERATIVA
✓ Datos: RECUPERADOS (o % recuperados si faltó algo)
✓ Acceso usuario: COMPLETO

─────────────────────────────────────────────────────────

RECOMENDACIONES INMEDIATAS
────────────────────────
1. [CRÍTICA] Cambiar contraseñas de:
   - Windows local
   - Correo corporativo
   - Servicios críticos (Teams, VPN, etc)
   - Hacer DESDE OTRO PC LIMPIO
   - Plazo: Hoy

2. [CRÍTICA] Invalidar tokens/API keys activas
   - Si hay integración con cloud services
   - Plazo: Hoy

3. [ALTA] Auditar accesos RDP (si hay):
   - Revisar quién accedió en últimos 48 horas
   - Cambiar credenciales RDP
   - Plazo: Esta semana

4. [ALTA] Escanear otros PCs en red:
   - ¿Otros equipos tienen las mismas IOCs?
   - ¿Se propagó lateralmente?
   - Plazo: Esta semana

5. [MEDIA] Revisar correos phishing:
   - ¿De dónde vino el malware? (email, web, USB?)
   - Bloquear remitente si es posible
   - Entrenar staff
   - Plazo: Esta semana

─────────────────────────────────────────────────────────

RECOMENDACIONES A LARGO PLAZO
──────────────────────────
1. Instalar EDR (Endpoint Detection & Response)
   - Ejemplos: CrowdStrike Falcon, Microsoft Defender for Endpoint
   - Beneficio: Detección en tiempo real futuros ataques

2. Habilitar MFA (Multi-Factor Authentication)
   - Correo corporativo
   - Acceso RDP/VPN
   - Servicios cloud

3. Realizar backups offline
   - Backup externo (USB/HDD) sin conexión
   - Testear restauración regularmente
   - Plazo: Implementar dentro de 1 mes

4. Capacitación de phishing
   - Training staff en reconocimiento de phishing
   - Simulaciones mensuales
   - Plazo: Implementar en 2 semanas

5. Auditoría de seguridad de red
   - Revision de firewall rules
   - Segmentación de red
   - Plazo: Contratar especialista en 1 mes

6. Monitoreo de logs
   - Centralizar Event Logs
   - Alertas configuradas para patrones sospechosos
   - Plazo: Implementar en 1-2 meses

─────────────────────────────────────────────────────────

HASHES DE EVIDENCIA (Cadena de Custodia)
──────────────────
Archivo: memoria_[fecha].mem
SHA256: [hash aquí]
Fecha captura: [fecha]
Integridad verificada: SÍ ✓

KAPE Output:
SHA256: [hash de carpeta]
Contenido: Event Logs, Prefetch, Registry, Browser history
Integridad verificada: SÍ ✓

[Otros archivos de evidencia]

─────────────────────────────────────────────────────────

EVIDENCIA ENTREGADA
────────────────
El cliente recibe USB C conteniendo:
- memoria_[fecha].mem (captura RAM)
- _KAPE_OUTPUT/ (artefactos forenses)
- _REPORTS/ (reportes herramientas: Thor, RogueKiller, etc)
- _RECUPERADO/ (archivos recuperados si aplica)
- _VOLATILITY_ANALYSIS/ (análisis post-incidente)

Almacenamiento: USB C SSD externo, exFAT, 128GB+

─────────────────────────────────────────────────────────

CONCLUSIÓN
────────
[1-2 párrafos finales]

Ejemplo:
"El incidente fue respondido profesionalmente, documentado 
completamente, y el sistema fue restaurado a estado operativo. 
La implementación de las recomendaciones anteriores fortalecerá 
significativamente la postura de seguridad futura. Cualquier 
duda adicional, contactar al técnico."

─────────────────────────────────────────────────────────

FIRMA Y FECHA
─────────────
Técnico: [Tu nombre]
Fecha: [DD/MM/AAAA]
Hora finalización: [HH:MM UTC]
Firma: _____________________

CONFIDENCIAL - No distribuir sin autorización del cliente
═══════════════════════════════════════════════════════════
```

---

### Acción 5.6: Entregar Evidencia

- [ ] **Entrega USB C al cliente con:**
  - `memoria_[fecha].mem`
  - `_KAPE_OUTPUT/`
  - `_REPORTS/`
  - `_RECUPERADO/` (si aplica)
  - `_VOLATILITY_ANALYSIS/`

- [ ] **Entrega REPORTE FINAL en PDF impreso** (y copia digital en USB)

- [ ] **En libreta:** Anota
  - Fecha/hora entrega
  - Firma cliente (confirma recepción)
  - Notas finales

---

## 📊 RESUMEN DE TIEMPOS

| Fase | Duración | Actividades |
|------|----------|------------|
| **FASE 0** | 5-10 min | Fotos, observación, desconexión red |
| **FASE 1** | 30-45 min | Captura RAM (FTK) |
| **FASE 2** | 90-120 min | Diagnóstico (5 herramientas + KAPE) |
| **FASE 3** | 30-60 min | Limpieza offline (KRD o CAINE) |
| **FASE 4** | 60-90 min | Persistencia + validación |
| **FASE 5** | 15-30 min | Validación estabilidad |
| **Reporte** | 60-90 min | Documentación profesional |
| **TOTAL ON-SITE** | **5-8 horas** | Depende severidad |
| **POST-INCIDENT ANALYSIS** | **2-4 horas** | Volatility + reporte en tu máquina |

---

## 🆘 TROUBLESHOOTING EN CAMPO

### **FTK Imager no captura**
```
❌ Error: "Cannot read from source"
✅ Solución: Run as Administrator (click derecho > Run as admin)
```

### **Thor dice "License not found"**
```
❌ Error: License missing
✅ Solución: Verifica .lic en carpeta thor/. Si no existe, salta Thor.
```

### **USB B no bootea**
```
❌ No aparece en Boot Menu
✅ Solución: 
  - Presiona F12/F9/DEL MÁS LENTAMENTE
  - Intenta otros puertos USB
  - Verifica Ventoy está instalado bien (reconecta y prueba)
```

### **KAPE falla**
```
❌ Error: "Invalid source path"
✅ Solución: Usa diskpart para verificar letra disco
  diskpart
  list disk
  (nota qué letra tiene cada disco)
```

---

## ✔️ CHECKLIST ANTES DE IRTE DEL CLIENTE

- [ ] Sistema operativo: LIMPIO y FUNCIONAL
- [ ] Contraseñas: Cliente informado de CAMBIAR desde otro PC
- [ ] USB C: Contiene toda la evidencia
- [ ] Reporte: Impreso y digital en USB C
- [ ] Fotos: Capturadas al inicio
- [ ] Libreta: Todos los hallazgos documentados
- [ ] Hashes: SHA256 de archivos críticos anotados
- [ ] Contacto: Cliente tiene tu teléfono para dudas
- [ ] Datos recuperados: Verificados y en USB C
- [ ] Recomendaciones: Entregadas y explicadas verbalmente

---

**Status:** Protocolo Ejecución v2.3 ESPECIALISTA ✅ LISTO PARA CAMPO
**Rol:** Consultor independiente - Tú tomas las decisiones
**Profesionalismo:** Tu reporte define tu reputación
**Tiempo total:** 5-8 horas on-site + 2-4 horas análisis post
