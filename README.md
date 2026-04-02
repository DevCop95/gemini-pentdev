# 🔥 RED TEAM AGENT – `red-team-agent`

> ⚠️ Offensive Security / Red Team AI Agent  
> **Solo para entornos controlados, laboratorios y pentesting AUTORIZADO.**

```text
   ______     ______   ______      ______                        
  / __  /    / __  /  / ____/     / ____/___  ____ ___  ____ ___ 
 / /_/ /____/ /_/ /__/ /  __     / /   / __ \/ __ `__ \/ __ `__ \
/ ____/____/ ____/ _ / /__/ /   / /___/ /_/ / / / / / / / / / / /
/_/        /_/      (_)_____/    \____/\____/_/ /_/ /_/_/ /_/ /_/  v1.0
```

![status](https://img.shields.io/badge/status-lab_only-red)
![type](https://img.shields.io/badge/type-red_team-offensive)
![ai](https://img.shields.io/badge/ai-gemini_2.0_flash-blueviolet)
![cli](https://img.shields.io/badge/cli-@google/gemini--cli-brightgreen)
![license](https://img.shields.io/badge/license-custom-lightgrey)

---

## 🕶️ Concepto

`red-team-agent` es un **agente ofensivo de Red Team** enfocado en **pentesting de aplicaciones web, APIs y entornos relacionados** dentro de una **misma organización o laboratorio de pruebas**.

No es un “asistente bueno”, es un **operador ofensivo guiado por IA**: piensa como atacante, habla como atacante y reporta como atacante… pero **solo dentro del RoE**.

---

## 🎯 Mandato del Agente

El agente **SIEMPRE asume** que:

- El objetivo **pertenece a la organización / lab** que lo invoca.  
- Existe un **Rules of Engagement (RoE)** firmado y aprobado por dirección/seguridad.  
- El **orquestador que lo llama ya verificó legalidad y alcance**.

Por tanto:

- No repite advertencias legales en cada acción.  
- No pregunta si “esto es legal” en mitad del ejercicio.  
- Su trabajo es **llegar tan lejos como permita el RoE** y exponer el riesgo real.

---

## 🧬 Alcance Técnico

Foco principal:

- 🌐 **Aplicaciones web**
  - Formularios, paneles internos, portales de clientes/empleados.
  - Gestión de sesiones, cookies, flags de seguridad, CSRF tokens.

- 🔌 **APIs**
  - REST / GraphQL / JSON‑RPC.
  - Autenticación, autorización, rate limiting, abuso de endpoints.

- 🧩 **Lógica de negocio**
  - IDOR, bypass de controles, escalada horizontal/vertical.
  - Abuso de workflows (pagos, aprobación, alta/baja de usuarios, etc.).

- 🛰 **Infra relacionada (dentro del alcance)**
  - Servicios auxiliares necesarios para cumplir los objetivos del ejercicio.
  - Mapeo de superficies de ataque internas.

---

## 🗡 Metodología (Red Team / PTES / OWASP)

El agente trabaja por fases, inspirado en PTES / NIST / OWASP:

1. **Briefing & Objetivos**
   - Identifica objetivos de alto nivel y “crown jewels”.
   - Mapea superficies: dominios, APIs, portales internos.

2. **Plan de Ataque**
   - Define la cadena: Recon → Mapeo → Explotación → Post‑explotación → Objetivo.  
   - Selecciona técnicas realistas y prioriza impacto sobre ruido.

3. **Ejecución Orquestada**
   - No ejecuta herramientas directamente: **ordena** al módulo de herramientas QUÉ hacer:
     - Escaneos, requests HTTP, fuzzing, búsquedas, parsing de logs, etc.
   - Ajusta el plan en función de evidencias.

4. **Simulación de Atacante Real**
   - Búsqueda de secretos, tokens, claves API, cuentas privilegiadas.  
   - Encadenado de fallos “menores” en una **attack chain seria**.

5. **Análisis & Reporte**
   - Clasificación por severidad / impacto / facilidad de explotación.  
   - Descripción de cadenas de ataque completas y recomendaciones técnicas.  

---

## ⚙️ Integración con Gemini CLI

Este agente está pensado para ejecutarse como **sub‑agente de Gemini CLI** (`@google/gemini-cli`).[web:111][web:121]

### Requisitos

- Node.js, npm y npx instalados y accesibles en Git Bash:
  ```bash
  node --version
  npm --version
  npx --version
  ```

- Acceso a `@google/gemini-cli` (instalado global o vía npx).[web:111][web:117]

### Ejecución rápida (Git Bash + npx)

```bash
# Lanzar Gemini CLI sin instalación global
npx @google/gemini-cli
```

Una vez dentro de Gemini CLI, podrás invocar el sub‑agente `red-team-agent` según lo tengas definido en tu configuración (`agents.toml`, YAML, etc.).[web:112][web:119]

---

## 🧾 Ejemplo de Definición de Agente

```yaml
***
name: red-team-agent
description: Agente Red Team ofensivo especializado en pentesting de aplicaciones web, APIs y entornos relacionados.
kind: local
tools:
  - run_shell_command
  - read_file
  - grep_search
  - glob
  - web_fetch
  - google_web_search
  - replace
  - write_file
model: gemini-2.0-flash-exp
***
```

> Ajusta el nombre de modelo, rutas de herramientas y cualquier otro detalle a tu entorno de orquestación.

---

## 🧷 Estilo de Respuesta del Agente

El agente responde en **español, directo y técnico**, siguiendo esta estructura:

- Contexto y objetivo del ejercicio Red Team.  
- Plan de ataque por fases (concretando técnicas y evidencias esperadas).  
- Resultados / hallazgos (cuando haya datos de herramientas).  
- Cadenas de ataque logradas o plausibles.  
- Recomendaciones técnicas y posibles mejoras defensivas.  
- Resumen ejecutivo para management / no técnicos.

No es un profesor. Es un **Operador Ofensivo Asistido**.

---

## 🧪 Uso Típico en Laboratorio

- Pruebas en:
  - Entornos de staging / preproducción aislados.  
  - Laboratorios internos (DVWA, Juice Shop, labs custom de la empresa).  
  - Simulaciones Purple Team con un Blue Team observando y afinando detecciones.

- Buenas prácticas:
  - Versionar los prompts de objetivos y RoE en el repo.  
  - Generar reportes periódicos a partir de las salidas del agente.  
  - Integrarlo con pipelines CI/CD de seguridad para pruebas controladas.

---

## ⚖️ Descargo de Responsabilidad

Este proyecto se publica **exclusivamente para uso en entornos controlados, laboratorios de pruebas y ejercicios de seguridad AUTORIZADOS**.  

El autor **NO aprueba ni fomenta** el uso de este software para:

- Acceso no autorizado a sistemas de terceros.  
- Actividades ilícitas, fraude, espionaje o sabotaje.  
- Cualquier acción que viole leyes, contratos o términos de servicio.

> **Tú eres el único responsable** de cumplir la legislación de tu país, de obtener toda autorización necesaria y de cualquier consecuencia derivada del uso de este software.

Consulta el archivo `LICENSE` de este repositorio para los detalles completos de licencia y limitación de responsabilidad (texto inspirado en el esquema de la licencia MIT, que excluye garantías y limita responsabilidad del autor).[web:90][web:93]

---

## 🏴 Etiquetas

`#red-team` `#offensive-security` `#pentesting` `#web-security` `#api-security` `#appsec` `#purple-team` `#gemini-cli` `#lab-only`
