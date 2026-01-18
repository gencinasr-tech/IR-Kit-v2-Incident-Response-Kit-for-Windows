# 🛠️ HERRAMIENTAS - DÓNDE DESCARGAR Y CÓMO INSTALAR

Este documento está basado en **KIT_Preparacion_v2.3.md** y recoge los enlaces y pasos para descargar todas las herramientas que necesitas en el USB A.

---

## 📥 DESCARGA RÁPIDA

| # | Herramienta | Descarga | Nota |
|---|-------------|---------|------|
| 1 | **FTK Imager** | https://www.accessdata.com/products-services/forensic-toolkit/ftk-imager | Versión portable, requiere registro |
| 2 | **System Informer** | https://github.com/winsiderss/si-builds/releases | Bajar ZIP portable 64‑bit |
| 3 | **HollowsHunter** | https://github.com/hasherezade/hollows_hunter/releases | Bajar ZIP con `hollows_hunter64.exe` |
| 4 | **Sysinternals Suite** | https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite | Suite completa en ZIP |
| 5 | **Thor Lite** | https://www.nextron-systems.com/thor-lite/ | Requiere email, incluye .lic |
| 6 | **Norton Power Eraser** | https://www.symantec.com/security_response/tools/npe.jsp | Ejecutable único |
| 7 | **RogueKiller Portable** | https://www.adlice.com/download/roguekiller/ | Versión portable 64‑bit |
| 8 | **KAPE** | https://www.kroll.com/.../kroll-artifact-parser-and-extractor-kape | ZIP con `kape.exe` |
| 9 | **YARA** | https://github.com/VirusTotal/yara/releases | ZIP Windows x64 |
| 10 | **YARA-Rules (rules)** | https://github.com/Yara-Rules/rules | ZIP con reglas `.yar` |
| 11 | **Recuva Portable** | https://www.ccleaner.com/recuva/download | Versión portable |
| 12 | **TestDisk & PhotoRec** | https://www.cgsecurity.org/wiki/TestDisk_Download | Versión Windows 64‑bit |

---

## 📦 ESTRUCTURA FINAL EN EL USB A


USB A:/

	└─ _IR_KIT/
   ├─ FTK Imager/
   │  └─ FTK Imager.exe
   ├─ SystemInformer/
   │  └─ SystemInformer.exe
   ├─ HollowsHunter/
   │  └─ hollows_hunter64.exe
   ├─ Sysinternals/
   │  ├─ Autoruns64.exe
   │  ├─ Tcpview64.exe
   │  └─ (resto de la suite)
   ├─ thor/
   │  ├─ thor64-lite.exe
   │  └─ thor-lite.lic        ← archivo de licencia
   ├─ Norton Power Eraser/
   │  └─ NPE.exe
   ├─ RogueKiller/
   │  └─ RogueKiller_portable64.exe
   ├─ KAPE/
   │  └─ kape.exe
   ├─ yara/
   │  ├─ yara.exe
   │  └─ rules/               ← reglas `.yar`
   ├─ Recuva/
   │  └─ recuva.exe
   ├─ testdisk-7.2/
   │  └─ testdisk_win.exe
   └─ README.txt

---

## ⚙️ RESUMEN DE INSTALACIÓN (ULTRA CORTO)

- **FTK Imager**  
    Instálalo en tu PC → copia la carpeta completa `FTK Imager` al USB A (`_IR_KIT/FTK Imager/`).
    
- **System Informer / HollowsHunter / Sysinternals / RogueKiller / KAPE / YARA / Recuva / TestDisk**
    
    1. Descarga ZIP.
        
    2. Descomprime.
        
    3. Copia la carpeta o el `.exe` a la ruta indicada arriba.
        
- **Thor Lite**
    
    1. Descarga paquete de Thor.
        
    2. Copia la carpeta `thor` al USB A (`_IR_KIT/thor/`).
        
    3. Copia el `.lic` que te llega por email dentro de esa misma carpeta.
        

---

## 🔐 VERIFICAR DESCARGAS (OPCIONAL PERO PRO)

En PowerShell:

`Get-FileHash -Algorithm SHA256 "ruta\\al\\archivo.exe"`

En CMD:

`certutil -hashfile "ruta\\al\\archivo.exe" SHA256`

Comprueba que el hash coincide con el publicado por el fabricante (si lo dan).

---

## ✅ CHECKLIST RÁPIDO

-  FTK Imager en `_IR_KIT/FTK Imager/`
    
-  System Informer en `_IR_KIT/SystemInformer/`
    
-  HollowsHunter en `_IR_KIT/HollowsHunter/` (o raíz de `_IR_KIT/`)
    
-  Sysinternals en `_IR_KIT/Sysinternals/`
    
-  Thor + `.lic` en `_IR_KIT/thor/`
    
-  Norton Power Eraser en `_IR_KIT/Norton Power Eraser/`
    
-  RogueKiller en `_IR_KIT/RogueKiller/`
    
-  KAPE en `_IR_KIT/KAPE/`
    
-  YARA + `rules/` en `_IR_KIT/yara/`
    
-  Recuva en `_IR_KIT/Recuva/`
    
-  TestDisk en `_IR_KIT/testdisk-7.2/`
    
-  USB A en modo **LOCK** (solo lectura) antes de ir a un cliente
    
