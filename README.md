# IR-Kit-v2  
**Professional Incident Response Kit for Windows – Methodology, Tools & Playbooks**  
**Kit profesional de Respuesta ante Incidentes en Windows – Metodología, Herramientas y Playbooks**

---

## 🌐 Overview | Descripción general

**EN**  
IR-Kit-v2 is a practical, field-oriented Incident Response (IR) kit focused on **Windows endpoints**.  
It combines:

- A complete **IR execution protocol**
- A **preparation kit** for analysts
- **Forensic artifacts**, case studies and real-world reports
- References to **industry-grade tools** (FTK, Autoruns, Kaspersky Rescue Disk, etc.)

The goal is to provide a **repeatable, professional workflow** that a Tier 1–Tier 2 analyst can follow during security incidents on Windows systems.

**ES**  
IR-Kit-v2 es un kit práctico y orientado a campo para **Respuesta ante Incidentes en endpoints Windows**.  
Incluye:

- Un **protocolo completo de ejecución IR**
- Un **kit de preparación** para analistas
- **Artefactos forenses**, casos de estudio e informes reales
- Referencias a **herramientas de nivel profesional** (FTK, Autoruns, Kaspersky Rescue Disk, etc.)

El objetivo es ofrecer un **flujo de trabajo repetible y profesional** que pueda seguir un analista de nivel 1–2 durante incidentes de seguridad en sistemas Windows.

---

## 📁 Repository Structure | Estructura del repositorio

> Nota: los nombres de carpetas pueden ajustarse ligeramente respecto a este esquema.  
> Note: folder names may slightly differ from this layout.

```text
IR-Kit-v2/
├── case-study/           # Real-world case, reports and artifacts
├── docs/                 # Core methodology & procedures
├── recursos/             # Extra resources, templates, checklists (ES)
├── .gitignore
├── LICENSE
└── README.md
```

### `docs/` – Core Documentation | Documentación principal

**EN**

- `PROTOCOLO_IR_Ejecucion_v2.3_ESPECIALISTA.md`  
  Step-by-step **Incident Response Execution Protocol** for Windows endpoints: triage, containment, analysis and eradication.

- `KIT_Preparacion_v2.3_ESPECIALISTA.md`  
  **Preparation Kit** for IR specialists: checklist of tools, boot media, accounts, network requirements and environment hardening before an incident.

**ES**

- `PROTOCOLO_IR_Ejecucion_v2.3_ESPECIALISTA.md`  
  Protocolo de **ejecución de Respuesta ante Incidentes** en endpoints Windows: triaje, contención, análisis y erradicación paso a paso.

- `KIT_Preparacion_v2.3_ESPECIALISTA.md`  
  **Kit de preparación** para especialistas IR: checklist de herramientas, medios de arranque, cuentas, requisitos de red y endurecimiento del entorno previo al incidente.

---

### `case-study/` – Forensic Case Study | Caso de estudio forense

**Typical contents | Contenido típico:**

- `RPT-2026-0118-CLIENTEA.md.pdf`  
  **Full incident report**: timeline, findings, indicators of compromise (IoCs), recommendations.

- `Guillermo_thor_2026-01-17_2003.html`  
  HTML output from **THOR Lite** or similar scanning tool.

- `scan_report.json`, `dump_report.json`  
  Machine-readable scan results and dumps.

- `Guillermo_files_md5s.csv`  
  File hash listing (MD5) used to validate integrity and support forensic analysis.

**EN**  
This folder illustrates how to document a real case from **initial detection to final report**, including raw artifacts and analyst-facing documentation.

**ES**  
Esta carpeta ilustra cómo documentar un caso real desde la **detección inicial hasta el informe final**, incluyendo artefactos brutos y documentación para el analista.

---

### `recursos/` – Additional Resources | Recursos adicionales

**EN**  
Intended for templates, checklists, quick-reference guides and any reusable material that supports the IR process.

**ES**  
Pensada para plantillas, checklists, guías rápidas y cualquier material reutilizable que apoye el proceso de respuesta ante incidentes.

---

## 🧰 Tools Referenced | Herramientas referenciadas

The kit assumes familiarity with, or access to, the following tools:

**EN**

- **FTK / FTK Imager** – Acquisition and forensic imaging of disks and memory.
- **Autoruns** – Detailed inspection of persistence and autostart locations in Windows.
- **Norton Power Eraser** – Aggressive malware removal for highly suspicious systems.
- **Kaspersky Rescue Disk** – Offline scanning and cleaning from a trusted boot environment.
- **THOR Lite** – IOC & behavior-based scanner for compromise assessment.
- Other Windows system utilities and forensic helpers referenced inside the docs.

**ES**

- **FTK / FTK Imager** – Adquisición e imagen forense de discos y memoria.
- **Autoruns** – Inspección detallada de persistencia y puntos de arranque en Windows.
- **Norton Power Eraser** – Eliminación agresiva de malware en sistemas muy sospechosos.
- **Kaspersky Rescue Disk** – Escaneo y limpieza offline desde un entorno de arranque confiable.
- **THOR Lite** – Escáner basado en IoCs y comportamiento para evaluar compromiso.
- Otros utilitarios de sistema y herramientas forenses mencionados en la documentación.

> ⚠️ EN: Binaries for these tools are **not** redistributed here.  
> Download them from their official vendors and verify hashes before usage.  
> ⚠️ ES: Los binarios de estas herramientas **no** se redistribuyen aquí.  
> Descárgalos de sus sitios oficiales y verifica los hashes antes de usarlas.

---

## 🚨 Intended Use | Uso previsto

**EN**

IR-Kit-v2 is designed for:

- Training and upskilling **SOC / IR analysts**
- Building a **repeatable runbook** for Windows incident response
- Serving as a **reference** during real investigations
- Standardizing documentation and evidence collection

It is **not** a substitute for:
- Formal legal procedures
- Vendor-specific IR playbooks
- Organization-specific policies and compliance requirements

**ES**

IR-Kit-v2 está diseñado para:

- Formación y mejora de **analistas SOC / IR**
- Construir un **runbook repetible** para respuesta ante incidentes en Windows
- Servir como **referencia** durante investigaciones reales
- Estandarizar la documentación y recogida de evidencias

No pretende sustituir:

- Procedimientos legales formales
- Playbooks específicos de fabricantes
- Políticas internas y requisitos de cumplimiento normativo de cada organización

---

## ▶️ How to Use This Kit | Cómo utilizar este kit

**EN**

1. **Before an incident**
   - Review `KIT_Preparacion_v2.3_ESPECIALISTA.md`
   - Prepare boot media, tools and credentials as indicated
   - Adapt the checklists to your own environment

2. **During an incident**
   - Follow `PROTOCOLO_IR_Ejecucion_v2.3_ESPECIALISTA.md` step by step
   - Capture evidence and artifacts into a folder structure similar to `case-study/`
   - Use the referenced tools according to internal policy and legal constraints

3. **After the incident**
   - Produce a final report modeled after `RPT-2026-0118-CLIENTEA.md.pdf`
   - Update your local copy of this kit with lessons learned and new IoCs

**ES**

1. **Antes del incidente**
   - Revisa `KIT_Preparacion_v2.3_ESPECIALISTA.md`
   - Prepara medios de arranque, herramientas y credenciales según lo indicado
   - Adapta las checklists a tu propio entorno

2. **Durante el incidente**
   - Sigue `PROTOCOLO_IR_Ejecucion_v2.3_ESPECIALISTA.md` paso a paso
   - Recoge evidencias y artefactos en una estructura similar a `case-study/`
   - Utiliza las herramientas referenciadas respetando la política interna y el marco legal

3. **Después del incidente**
   - Redacta un informe final siguiendo el modelo `RPT-2026-0118-CLIENTEA.md.pdf`
   - Actualiza tu copia local de este kit con lecciones aprendidas y nuevos IoCs

---

## 🤝 Contributions | Contribuciones

**EN**

Contributions are welcome, especially:

- Improvements to the IR protocol
- New case studies (with sanitized data)
- Additional checklists, templates and playbooks
- Tool usage guides and troubleshooting notes

Open a **Pull Request** or start a **Discussion/Issue** describing the proposal.

**ES**

Las contribuciones son bienvenidas, especialmente:

- Mejoras al protocolo de respuesta
- Nuevos casos de estudio (con datos anonimizados)
- Checklists, plantillas y playbooks adicionales
- Guías de uso de herramientas y notas de troubleshooting

Abre un **Pull Request** o crea una **Issue/Discussion** explicando la propuesta.

---

## ⚖️ License | Licencia

This project is released under the **MIT License**.  
Este proyecto se publica bajo la **licencia MIT**.

For details, see the `LICENSE` file.  
Para más detalles, consulta el archivo `LICENSE`.
