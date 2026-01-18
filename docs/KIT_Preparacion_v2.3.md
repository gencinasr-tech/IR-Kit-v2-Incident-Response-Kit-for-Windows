# 🛠️ KIT DE RESPUESTA A INCIDENTES - GUÍA DE PREPARACIÓN v2.3 ESPECIALISTA

> **TÚ ERES EL EXPERTO.** Este kit te prepara para ser autosuficiente en campo.
> No hay escalados a terceros. Tú tomas todas las decisiones basándote en evidencia.

---
## PASO 1: Reúne el Hardware

Necesitas físicamente esto sobre tu mesa:

- **USB A ("El Escudo")**: Un pendrive con pestaña física de bloqueo de escritura (Write Protect Switch). **Tamaño mínimo: 32GB**. Esto va contigo al campo.
- **USB B ("El Quirófano")**: Un pendrive rápido (USB 3.0) de al menos **64GB** (para 3 ISOs grandes). Esto va contigo al campo.
- **USB C ("La Evidencia")**: Un disco duro externo SSD o USB de gran capacidad **128GB+** (preferible SSD, >500MB/s). Esto va contigo al campo Y luego lo analizas en casa.

**Recomendaciones de hardware:**
- USB A: Sandisk Extreme Pro (buena velocidad, buen write-protect)
- USB B: Samsung Fit Plus o similar (rápido, durable)
- USB C: Seagate Barracuda SSD o Crucial X6 (velocidad + capacidad)

---

## PASO 2: Preparando el USB A ("El Escudo")

**Objetivo**: Llevar herramientas de diagnóstico portables. Tú eres autosuficiente en campo.

### 2.1 Formateo del USB A

```
Formateo: NTFS
Etiqueta: HERRAMIENTAS
Tamaño: Full USB
```

**Cómo hacerlo:**
1. Conecta USB A a tu PC
2. Clic derecho > Formatear
3. Sistema de archivos: **NTFS**
4. Nombre: `HERRAMIENTAS`
5. Click Iniciar (se borra TODO)
6. Espera a que termine

### 2.2 Crear Estructura de Carpetas

Crea una carpeta llamada `_IR_KIT` en la raíz del USB.

```
USB A:/
└─ _IR_KIT/
   ├─ FTK Imager/
   ├─ SystemInformer/
   ├─ Sysinternals/
   ├─ thor/
   ├─ Norton Power Eraser/
   ├─ RogueKiller/
   ├─ KAPE/
   ├─ yara/
   ├─ Recuva/
   ├─ testdisk-7.2/
   └─ README.txt
```

### 2.3 Lista de Herramientas (Descarga e Instalación)

#### 1. **FTK Imager (Versión Portable - CRÍTICO)**

**Descarga:**
- Accede a: https://www.accessdata.com/products-services/forensic-toolkit/ftk-imager (requiere registro)
- O: Busca `FTK Imager Pro portable` en Google

**Instalación portátil:**
1. Descarga el instalador en tu PC
2. Ejecuta `FTK Imager_x64.exe` (instalación normal en tu máquina)
3. Ve a `C:\Program Files\AccessData\FTK Imager`
4. Copia **TODA LA CARPETA** `FTK Imager` a `USB A/_IR_KIT/`
5. Ahora funciona sin necesidad de instalar en el PC del cliente

**Verificación:** `USB A/_IR_KIT/FTK Imager/FTK Imager.exe` debe existir

---

#### 2. **System Informer (Portable)**

**Descarga:**
- https://github.com/winsiderss/si-builds/releases
- Busca `system-informer-x.x-setup.exe` (última versión 64-bit)

**Instalación portátil:**
1. Descarga el `.zip` portable (NO el `.exe`)
2. Descomprime a `USB A/_IR_KIT/SystemInformer/`
3. Verifica que exista `SystemInformer.exe` en esa carpeta

**Verificación:** `USB A/_IR_KIT/SystemInformer/SystemInformer.exe` debe existir

---

#### 3. **HollowsHunter (Portable)**

**Descarga:**
- https://github.com/hasherezade/hollows_hunter/releases
- Busca el archivo `.zip` más reciente con `hollows_hunter64.exe`

**Instalación:**
1. Descomprime el ZIP
2. Copia `hollows_hunter64.exe` a `USB A/_IR_KIT/`
3. Listo, no necesita carpeta separada

**Verificación:** `USB A/_IR_KIT/hollows_hunter64.exe` debe existir

**Nota importante:** HollowsHunter genera reportes en `%appdata%\hollows_hunter\scan_report\`. Cópialos a USB C después para tu análisis.

---

#### 4. **Sysinternals Suite**

**Descarga:**
- https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
- Click "Download Sysinternals Suite"

**Instalación:**
1. Descomprime el ZIP
2. Copia TODO a `USB A/_IR_KIT/Sysinternals/`
3. **Asegúrate especialmente de:**
   - `Autoruns64.exe`
   - `Tcpview64.exe`

**Verificación:** Ambos archivos `.exe` deben existir en la carpeta

---

#### 5. **Thor Lite (Scanner APT)**

**Descarga:**
- https://www.nextron-systems.com/thor-lite/ (requiere email)
- O: Si ya lo tienes descargado localmente, úsalo

**Instalación:**
1. Descomprime carpeta `thor` completa a `USB A/_IR_KIT/`
2. **CRÍTICO:** También debes tener el archivo de licencia `.lic` (te llega al email)
3. Copia el archivo `.lic` DENTRO de `USB A/_IR_KIT/thor/`
4. **Sin el `.lic`, Thor no arranca**

**Verificación:**
- `USB A/_IR_KIT/thor/thor64-lite.exe` existe
- `USB A/_IR_KIT/thor/[licencia].lic` existe (cualquier nombre `.lic`)

**Nota importante:** Thor genera reportes detallados en `.html` y `.txt`. Busca los logs en `C:\ProgramData\thor\logs\` o en carpeta de ejecución. Cópialos a USB C para incluir en tu reporte final.

---

#### 6. **Norton Power Eraser (NPE)**

**Descarga:**
- https://www.symantec.com/security_response/tools/npe.jsp
- O búsca directo `Norton Power Eraser portable`

**Instalación:**
1. Descarga el ejecutable
2. Copia `NPE.exe` a `USB A/_IR_KIT/Norton Power Eraser/`
3. O copia el ejecutable solo a `USB A/_IR_KIT/` si no tiene dependencias

**Verificación:** `USB A/_IR_KIT/NPE.exe` o `Norton Power Eraser/NPE.exe` existe

**Nota importante:** NPE genera logs. Busca en `C:\ProgramData\Norton\...` y copia a USB C.

---

#### 7. **RogueKiller Portable**

**Descarga:**
- https://www.adlice.com/download/roguekiller/ (Búsca versión Portable)
- O: GitHub releases si lo mantienen ahí

**Instalación:**
1. Descomprime carpeta portable
2. Copia a `USB A/_IR_KIT/RogueKiller/`
3. Debe haber `RogueKiller_portable64.exe` en esa carpeta

**Verificación:** `USB A/_IR_KIT/RogueKiller/RogueKiller_portable64.exe` existe

**Nota importante:** RogueKiller genera reporte `.html`. Lo guardará en carpeta de ejecución o Desktop. Cópialos a USB C.

---

#### 8. **KAPE (Artifact Collection) - [NUEVO]**

**Descarga:**
- https://www.kroll.com/en/services/cyber/incident-response-recovery/kroll-artifact-parser-and-extractor-kape
- O directo: GitHub de Eric Zimmerman

**Instalación:**
1. Descarga el ZIP de KAPE
2. Descomprime a `USB A/_IR_KIT/KAPE/`
3. Debe haber `kape.exe` en esa carpeta

**Verificación:** `USB A/_IR_KIT/KAPE/kape.exe` existe

**Nota importante:** KAPE genera estructura de carpetas organizadas. Output va directo a USB C en `_KAPE_OUTPUT/`. Esto es crítico para tu análisis posterior.

---

#### 9. **YARA (Pattern Matching) - [NUEVO]**

**Descarga:**
- https://github.com/VirusTotal/yara/releases
- Busca `yara-x.x.x-windows-x64.zip`

**Instalación:**
1. Descomprime a `USB A/_IR_KIT/yara/`
2. Debe haber `yara.exe` en esa carpeta
3. **TAMBIÉN necesitas rules.** Descarga en la misma carpeta:
   - https://github.com/Yara-Rules/rules (descarga ZIP)
   - Descomprime y copia la carpeta `rules/` a `USB A/_IR_KIT/yara/rules/`

**Verificación:**
- `USB A/_IR_KIT/yara/yara.exe` existe
- `USB A/_IR_KIT/yara/rules/` contiene muchos archivos `.yar`

**Nota importante:** YARA es tu herramienta de detección avanzada. Las rules deben estar actualizadas. Descárgalas regularmente (cada 3 meses).

---

#### 10. **Recuva Portable**

**Descarga:**
- https://www.ccleaner.com/recuva/download (Busca versión Portable)

**Instalación:**
1. Descarga ZIP portable
2. Descomprime a `USB A/_IR_KIT/Recuva/`
3. Debe haber `recuva.exe` o `RecuvaCommandLine.exe`

**Verificación:** Archivos ejecutables existen en la carpeta

---

#### 11. **TestDisk & PhotoRec**

**Descarga:**
- https://www.cgsecurity.org/wiki/TestDisk_Download
- Busca versión Windows 64-bit

**Instalación:**
1. Descomprime carpeta `testdisk-7.2-WIP/` (o versión que sea)
2. Copia TODA la carpeta a `USB A/_IR_KIT/testdisk-7.2/`
3. Debe haber `testdisk_win.exe` en esa carpeta

**Verificación:** `USB A/_IR_KIT/testdisk-7.2/testdisk_win.exe` existe

---

### 2.4 README.txt para el USB A

Crea un archivo `USB A/_IR_KIT/README.txt` con esto:

```
=== IR KIT v2.3 ESPECIALISTA ===
Professional Incident Response Toolkit

HERRAMIENTAS INCLUIDAS (Portable - Sin instalación requerida):
- FTK Imager: Captura forense de RAM
- System Informer: Análisis avanzado de procesos
- HollowsHunter: Detección de code injection
- Sysinternals: Suite profesional (Autoruns, Tcpview, etc)
- Thor Lite: Scanner APT y detección C2
- Norton Power Eraser: Anti-rootkit especializado
- RogueKiller: Anti-malware general
- KAPE: Extracción automática de artefactos forenses
- YARA: Pattern matching contra familias malware
- Recuva: Recuperación de archivos borrados
- TestDisk: Recuperación de particiones perdidas

FLUJO DE EJECUCIÓN:
1. FTK Imager → Captura memoria completa (CRÍTICO)
2. System Informer → Análisis de procesos vivos
3. HollowsHunter → Detección de inyecciones
4. Thor Lite → Scanner APT
5. RogueKiller → Antimalware general
6. KAPE → Extracción de artefactos
7. YARA → Pattern matching avanzado
8. Kaspersky Rescue Disk (USB B) → Limpieza offline
9. Autoruns → Detección de persistencia
10. Norton Power Eraser → Rootkits agresivos

TODOS LOS REPORTES GENERADOS:
- Cópialos a USB C después de ejecución
- Los usarás para análisis post-incidente en tu máquina
- Incluirás en reporte final profesional

NOTAS:
- TODO es portable, NO instales nada en PC cliente
- USB A debe estar en LOCK (read-only)
- USB B booteable con Ventoy + 3 ISOs
- USB C para almacenar evidencia (exFAT, >128GB)
```

---

### 2.5 ACABADO FINAL USB A

- [ ] Pon el USB en modo LOCK (mueve la pestaña pequeña a "LOCK")
- [ ] Pon una pestaña roja: "READ ONLY - HERRAMIENTAS FORENSES"
- [ ] Guarda el USB en estuche protector (mochila, caja, etc)
- [ ] Verifica que tenga todo listado arriba

---

## PASO 3: Preparando el USB B ("El Quirófano")

**Objetivo**: USB booteable profesional con múltiples sistemas de rescate offline.

### 3.1 Instalar Ventoy

**Descarga:**
- https://github.com/ventoy/Ventoy/releases
- Busca `Ventoy-x.x.x-windows.zip`

**Instalación:**
1. Descomprime el ZIP
2. Ejecuta `Ventoy2Disk.exe`
3. Selecciona tu **USB B** en la lista (⚠️ ATENCIÓN: Borra TODO lo que haya)
4. Click **Install** (espera 2-3 mins)
5. Cuando termine, el USB B estará listo para ISOs

### 3.2 Descargar las ISOs (Enlaces Oficiales)

#### ISO 1: Kaspersky Rescue Disk (KRD)

**Descarga:**
- https://www.kaspersky.com/downloads/thank-you/free-rescue-disk
- O búsca `Kaspersky Rescue Disk ISO` directamente

**Archivo:** `kav_rescue_disk.iso` (~600 MB)

**Por qué:** KRD es la herramienta más efectiva para limpieza offline sin instalar Windows fresh. Te permite eliminar malware persistente sin que pueda interferir.

---

#### ISO 2: CAINE Linux (Forense)

**Descarga:**
- https://www.caine-live.net/page5/page5.html
- Busca versión **"CAINE 13.0 Warp (64bit) ISO"** o superior

**Archivo:** `CAINE-13.0-Warp-64bit.iso` (~2.5 GB)

**Por qué:** Si Windows no arranca, CAINE te permite rescatar datos y hacer análisis forense sin instalar nada. Es tu plan B crítico.

---

#### ISO 3: Windows 10/11 Instalador

**Descarga:**
- https://www.microsoft.com/es-es/software-download/windows10
- O Windows 11: https://www.microsoft.com/es-es/software-download/windows11

**Cómo:**
1. Descarga la herramienta "MediaCreationTool"
2. Ejecuta la herramienta
3. Selecciona **"Crear archivo ISO"** (NO USB)
4. Elige Windows 10 o 11 (la que uses normalmente)
5. Guarda como `Windows10-Installation.iso` o `Windows11-Installation.iso` (~5 GB)

**Por qué:** Si necesitas reinstalar Windows completamente (ransomware severo, corrupción extrema), lo tienes listo. Evita esperas innecesarias.

---

### 3.3 Copiar ISOs a USB B

Cuando tengas Ventoy instalado en USB B y las 3 ISOs descargadas:

1. Abre el Explorador de archivos
2. Ve a USB B (debería decir "Ventoy")
3. **Arrastra y suelta** los 3 archivos `.iso`:
   - `kav_rescue_disk.iso`
   - `CAINE-13.0-Warp-64bit.iso`
   - `Windows10-Installation.iso` (o Windows11)
4. Espera a que copie (puede tardar 10-20 mins según velocidad USB)

**Resultado final:**
```
USB B:/
├─ kav_rescue_disk.iso
├─ CAINE-13.0-Warp-64bit.iso
└─ Windows10-Installation.iso
```

---

### 3.4 ACABADO FINAL USB B

- [ ] Etiqueta el USB como **"BOOT / RESCUE"**
- [ ] Guarda en estuche junto a USB A
- [ ] Verifica que tenga las 3 ISOs (puedes hacer prueba de boot)

---

## PASO 4: Preparando el USB C ("La Evidencia")

**Objetivo**: SSD de almacenamiento rápido para evidencia forense. Aquí guardas TODO para análisis posterior.

### 4.1 Formateo del USB C

```
Sistema de archivos: exFAT (¡OBLIGATORIO para archivos >4GB!)
Etiqueta: EVIDENCIA
Tamaño: Full USB
```

**Cómo hacerlo:**
1. Conecta USB C / SSD externo
2. Clic derecho > Formatear
3. Sistema de archivos: **exFAT**
4. Nombre: `EVIDENCIA`
5. Click Iniciar
6. Espera a que termine

**¿Por qué exFAT?**
- NTFS tiene limite de 4GB por archivo
- RAM capturada puede ser >4GB (16GB, 32GB RAM de cliente)
- exFAT aguanta hasta 16 EB
- Compatible con Mac también (si necesitas compartir análisis)

---

### 4.2 Crear Estructura de Carpetas

En USB C, crea estas carpetas:

```
USB C:/
├─ _DUMPS/
│  └─ (aquí va memoria_ceo.mem - evidencia RAM)
├─ _KAPE_OUTPUT/
│  ├─ _Execution/
│  ├─ _AccountUsage/
│  ├─ _BrowserHistory/
│  └─ _Registry/
├─ _REPORTS/
│  ├─ thor_report.html
│  ├─ roguekiller_report.html
│  ├─ hollows_hunter_summary.json
│  ├─ npe_log.txt
│  └─ (todos los reportes de herramientas)
├─ _RECUPERADO/
│  └─ (archivos recuperados con Recuva)
├─ _VOLATILITY_ANALYSIS/
│  └─ (análisis post-incidente en tu máquina)
└─ _REPORTE_FINAL/
   └─ Reporte_Incidente_[FECHA].pdf (lo creas tú)
```

**Cómo:**
1. Abre Explorador en USB C
2. Clic derecho > Nueva carpeta > `_DUMPS`
3. Repite para todas las carpetas
4. Listo

---

### 4.3 ACABADO FINAL USB C

- [ ] Verifica que tenga **mínimo 128GB libres** (idealmente vacío)
- [ ] Si es SSD externo, verifica que **NO tenga datos críticos de clientes anteriores**
- [ ] Etiqueta como **"EVIDENCIA - [Tu nombre]"**
- [ ] Guarda en estuche junto a USB A y B

---

## PASO 5: Configuración en tu Máquina de Análisis (POST-INCIDENTE)

**IMPORTANTE:** Estas herramientas **NO se llevan al campo.** Se instalan en tu PC personal para analizar **DESPUÉS de volver del incidente.**

**Línea temporal correcta:**
- Lunes-Jueves (hoy): Preparas PASO 1-4 (USBs)
- Viernes (incidente): Llevas 3 USBs, ejecutas PROTOCOLO_IR_Ejecucion en campo (5-8 horas)
- Viernes tarde/Sábado: Vuelves a casa, usas PASO 5 para análisis profundo (2-4 horas)

### 5.1 Volatility 3 (Análisis avanzado de memoria)

**Qué es:** Herramienta forense que analiza memoria capturada. Detecta procesos inyectados, malware fileless, encryption keys, credenciales.

**Requisitos:**
- Python 3.6+
- pip (gestor de paquetes Python)

**Instalación:**
```bash
# En terminal/bash
pip install volatility3

# O si usas Kali:
apt install volatility3
```

**Verificación:**
```bash
volatility3 --help
# Debe mostrar opciones de volatility
```

**Cómo usarlas:**
1. Conectas USB C a tu PC
2. Copias `memoria_ceo.mem` a carpeta de trabajo
3. Ejecutas comandos como:
   ```bash
   volatility3 -f memoria_ceo.mem windows.pslist
   volatility3 -f memoria_ceo.mem windows.malfind
   volatility3 -f memoria_ceo.mem windows.netscan
   ```
4. Guardas output en `USB C:/_VOLATILITY_ANALYSIS/`

---

### 5.2 Registry Explorer (Eric Zimmerman Tool)

**Qué es:** Herramienta que analiza Registry de Windows offline, sin necesidad de ejecutar el sistema. Ves: servicios, programas que se ejecutan, USB devices conectados, timeline de actividades.

**Descarga:**
- https://ericzimmerman.github.io/#!index.md
- Busca "Registry Explorer"

**Instalación:**
1. Descarga el ZIP
2. Descomprime en `C:\Tools\Registry Explorer\` (o donde quieras)
3. Ejecutable: `RegistryExplorer.exe`

**Cómo usarla:**
1. Conectas USB C
2. Copias archivos de Registry de `_KAPE_OUTPUT/_Registry/` a tu máquina
3. Abres Registry Explorer
4. Cargas SYSTEM hive
5. Buscas: `CurrentControlSet\Services\` (servicios raros)
6. Cargas NTUSER.DAT
7. Buscas: `Software\Microsoft\Windows\CurrentVersion\Run` (programas startup)
8. Documentas hallazgos

---

### 5.3 Timeline Explorer (Eric Zimmerman Tool)

**Qué es:** Herramienta que visualiza artefactos cronológicamente. Combina KAPE output, prefetch, Event Logs y crea timeline de qué pasó y cuándo.

**Descarga:**
- https://ericzimmerman.github.io/#!index.md
- Busca "Timeline Explorer"

**Instalación:**
1. Descarga el ZIP
2. Descomprime en `C:\Tools\Timeline Explorer\`
3. Ejecutable: `TimelineExplorer.exe`

**Cómo usarla:**
1. Importas KAPE output
2. Visualizas qué se ejecutó primero, cuándo, dónde
3. Identificas "Patient Zero" (cómo empezó la infección)
4. Documentas timeline en tu reporte

---

### 5.4 Wireshark (PCAP Analysis)

**Qué es:** Analizador de tráfico de red. Si capturaste PCAP en campo, aquí ves IPs maliciosas, dominios C2, data exfiltration.

**Descarga:**
- https://www.wireshark.org/download/

**Instalación:**
- Descarga e instala normal en tu PC

**Cómo usarla:**
1. Conectas USB C
2. Abres Wireshark
3. File > Open > Busca PCAP capturada
4. Filtras por IP sospechosa: `ip.dst == 192.168.1.100`
5. Ves qué datos se transmitieron
6. Documentas IOCs (IPs, dominios)

---

## PASO 6: Cadena de Custodia y Hashing

**Esto es crítico para tu profesionalismo.** Cuando entregu evidencia, debe ser verificable.

### Hash de Archivo (Verificación de Integridad)

Apunta esto para verificar archivos sin que se modifiquen:

### PowerShell (Windows):
```powershell
Get-FileHash -Algorithm SHA256 "Archivo.exe"
```

### CMD (Windows):
```cmd
certutil -hashfile "Archivo.exe" SHA256
```

### Linux/Kali:
```bash
sha256sum archivo.exe
```

**Cuándo usarla:**
1. Cuando captures `memoria_ceo.mem`: Anota SHA256
2. Cuando extraigas artefactos con KAPE: Anota SHA256 de carpeta
3. En tu REPORTE FINAL: Incluye todos los hashes
4. Cliente puede verificar que nada se modificó

---

## ✅ CHECKLIST FINAL DE VERIFICACIÓN (Antes de primer incidente real)

**Haz esto HOY en tu casa ANTES de aceptar clientes:**

### USB A ("El Escudo")
- [ ] **FTK Imager:** Abre `USB A/_IR_KIT/FTK Imager/FTK Imager.exe`. ¿Se abre sin errores?
- [ ] **System Informer:** Abre `USB A/_IR_KIT/SystemInformer/SystemInformer.exe`. ¿Se ve interfaz?
- [ ] **HollowsHunter:** Ejecuta `USB A/_IR_KIT/hollows_hunter64.exe`. ¿Aparece consola?
- [ ] **Thor:** Ejecuta `USB A/_IR_KIT/thor/thor64-lite.exe`. ¿Empieza a escanear o pide licencia? (OK si pide licencia, significa archivo `.lic` está bien ubicado)
- [ ] **RogueKiller:** Abre `USB A/_IR_KIT/RogueKiller/RogueKiller_portable64.exe`. ¿Carga interfaz?
- [ ] **KAPE:** Ejecuta `USB A/_IR_KIT/KAPE/kape.exe --help`. ¿Muestra opciones?
- [ ] **YARA:** Ejecuta `USB A/_IR_KIT/yara/yara.exe`. ¿Aparece sin errores?
- [ ] **Bloqueo de escritura:** Mueve USB A a LOCK. Intenta crear un archivo en USB. Windows debe decir "Disco de sólo lectura" ✓

### USB B ("El Quirófano")
- [ ] **Boot:** Reinicia tu PC con USB B conectado. Presiona F12/F9. ¿Aparecen 3 ISOs en menú Ventoy? ✓
- [ ] **KRD:** Selecciona Kaspersky Rescue Disk. ¿Carga sin errores?
- [ ] **CAINE:** Vuelve atrás (ESC), selecciona CAINE. ¿Carga escritorio Linux?
- [ ] **Windows Installation:** Vuelve atrás, selecciona Windows. ¿Empieza instalador?

### USB C ("La Evidencia")
- [ ] **Acceso:** ¿Puedo leer Y escribir archivos?
- [ ] **Capacidad:** ¿Muestra tamaño correcto? (128GB+ libres)
- [ ] **Carpetas:** ¿Existen todas las carpetas `_DUMPS/`, `_KAPE_OUTPUT/`, etc?
- [ ] **Formato:** ¿Está en exFAT? (Clic derecho > Propiedades > Sistema de archivos)

### Tu Máquina de Análisis
- [ ] **Volatility 3:** Terminal > `volatility3 --help`. ¿Funciona?
- [ ] **Registry Explorer:** ¿Se abre sin errores?
- [ ] **Timeline Explorer:** ¿Se abre sin errores?
- [ ] **Wireshark:** ¿Se instala y abre?
- [ ] **Espacio disco:** ¿Tienes >500GB libres? (Para análisis de clientes grandes)

---

## 📋 CHECKLIST PRE-SALIDA (Antes de ir a cliente)

Cuando todo esté listo y probado:

- [ ] USB A en LOCK, etiquetado "READ ONLY - HERRAMIENTAS"
- [ ] USB B con Ventoy + 3 ISOs, booteable confirmado
- [ ] USB C formateado exFAT, carpetas creadas, capacidad verificada
- [ ] Volatility 3 instalado y testeado en mi máquina
- [ ] Registry Explorer / Timeline Explorer descargados y funcionales
- [ ] Todas las herramientas en USB A testeadas y funcionan
- [ ] Tengo libreta + bolígrafo para notas en campo
- [ ] Tengo cámara/móvil para fotografías de evidencia
- [ ] Tengo número de cliente, contacto de emergencia
- [ ] Tengo 5-8 horas libres para incidente
- [ ] Tengo mochila/estuche con los 3 USBs + cables + adaptadores
- [ ] Tengo acceso a internet para validar hashes, descargar (si falta algo)

---

## 🎯 PRÓXIMO PASO

Cuando todo esté listo, lee el otro documento:

**"PROTOCOLO_IR_EJECUCION_v2.3_ESPECIALISTA.md"** ← Paso a paso de cómo ejecutar en campo

---

**Status:** Kit de Preparación v2.3 ESPECIALISTA ✅ LISTO
**Versión:** Para consultores/especialistas independientes
**Tiempo de preparación primera vez:** 6-8 horas (descargas + setup)
**Tiempo de mantenimiento:** 30 mins cada 3 meses (actualizar YARA rules, ISOs)
**Actualización recomendada:** Cada 6 meses (nuevas versiones herramientas)
