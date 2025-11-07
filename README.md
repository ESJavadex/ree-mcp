# ⚡ REE MCP Server

<div align="center">

[![CI/CD](https://github.com/ESJavadex/ree-mcp/actions/workflows/ci.yml/badge.svg)](https://github.com/ESJavadex/ree-mcp/actions/workflows/ci.yml)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Code style: ruff](https://img.shields.io/badge/code%20style-ruff-000000.svg)](https://github.com/astral-sh/ruff)
[![Type checked: mypy](https://img.shields.io/badge/type%20checked-mypy-blue.svg)](http://mypy-lang.org/)

</div>

> Habla con la red eléctrica española a través de Claude - sin conocimientos técnicos

<a href="https://glama.ai/mcp/servers/@ESJavadex/ree-mcp">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@ESJavadex/ree-mcp/badge" alt="REE Server MCP server" />
</a>

Pregunta a Claude sobre **demanda, generación, precios y emisiones** de electricidad en España usando lenguaje natural. Él se encarga de todos los detalles técnicos.

Construido con **Domain-Driven Design** y **Clean Architecture** por [Javi Santos](https://www.linkedin.com/in/francisco-javier-santos-criado/) - Especialista en IA y Robótica con investigación publicada en visión por computador e interpretabilidad de LLMs.

> 💡 **¿Quieres aprender a construir proyectos así?** Únete a [La Escuela de IA](https://skool.com/la-escuela-de-ia-9955) - la comunidad donde aprenderás IA práctica, sin humo, con ejemplos reales en español.

---

## 🎯 ¿Qué Hace Este Servidor?

**Red Eléctrica de España (REE)** gestiona la red eléctrica española 24/7, publicando datos cada 5 minutos. Este servidor MCP hace esos datos accesibles mediante conversación natural con Claude.

### El Poder de Conversaciones con Datos Reales

*Por [Javi Santos](https://www.linkedin.com/in/francisco-javier-santos-criado/)*

En lugar de escribir scripts de Python, imagina conversaciones como esta:

**Tú:** *"Comprueba qué pasó el 28 de abril de 2025"*

**Claude:** *Analiza datos de la red...*

🚨 **EVENTO CRÍTICO DETECTADO - 28 de Abril de 2025 a las 12:35h**

**Colapso Masivo de la Red:**
- **11.000 MW perdidos en 5 minutos** (caída del 43% de capacidad)
- El sistema cayó de 25.184 MW → 14.185 MW instantáneamente
- Compatible con escenario de apagón en cascada
- La recuperación tardó más de 10 horas

**Análisis:**
- 11:00-12:30: Sistema estable, sin avisos previos
- 12:30-12:35: Fallo catastrófico instantáneo
- 12:35-13:35: Degradación continua hasta mínimo de 9.635 MW
- Causa probable: Disparo de planta nuclear → colapso de frecuencia → cascada

*Este sería uno de los peores apagones de España en la historia moderna.*

---

**Ese es el poder de este servidor.** Investiga eventos en la red, analiza tendencias renovables vs fósiles, correlaciona precios con demanda, o sigue la descarbonización de España - todo mediante conversación natural.

Sin documentación de API. Sin scripts. Solo pregunta.

---

## 🚀 Instalación (3 minutos)

### 1️⃣ Clonar e Instalar

```bash
# Clonar el repositorio
git clone https://github.com/ESJavadex/ree-mcp.git
cd ree-mcp

# Instalar uv (gestor rápido de paquetes Python)
curl -LsSf https://astral.sh/uv/install.sh | sh
# O en macOS: brew install uv

# Crear entorno virtual e instalar
uv venv
source .venv/bin/activate  # En Windows: .venv\Scripts\activate
uv pip install -e ".[dev]"
```

### 2️⃣ Configurar Token de API

```bash
# Copiar el archivo de ejemplo (incluye token demo)
cp .env.example .env

# Editar .env si necesitas tu propio token
# REE_API_TOKEN=tu_token_aqui
```

**Obtener Token:**
- **Pruebas/Demo**: Ya incluido en `.env.example`
- **Producción**: Email a consultasios@ree.es

### 3️⃣ Añadir a Claude Code

```bash
# Ejecutar el script de instalación
./INSTALL_COMMAND.sh

# Verificar
claude mcp list
```

Deberías ver `ree-mcp: ✓ Connected`.

### 4️⃣ ¡Listo! Empieza a Preguntar

Abre Claude Code y prueba:
- *"Muéstrame la demanda eléctrica actual de España"*
- *"¿Cuál es el mix de generación ahora?"*
- *"Compara generación solar vs eólica hoy"*

---

## 💬 ¿Qué Puedes Preguntar?

### 📊 Operaciones en Tiempo Real
- *"¿Cuál es la demanda eléctrica de España ahora mismo?"*
- *"Muéstrame el mix de generación al mediodía"*
- *"¿Cuánta energía exportó España ayer?"*
- *"Compara la demanda de hoy con la semana pasada"*
- *"¿Qué está generando cada central ahora? (nuclear, eólica, solar...)"*

### 🔍 Investigación y Análisis de Eventos
- *"Investiga qué pasó el 28 de abril de 2025"*
- *"¿Hubo actividad inusual en la red el mes pasado?"*
- *"Encuentra el día de pico de demanda este año y explica por qué"*
- *"Analiza la correlación entre generación eólica y precios"*
- *"Detecta patrones anómalos en la última semana"*
- *"¿Cuándo fue la última vez que hubo un apagón o evento crítico?"*

### 🌱 Energías Renovables y Emisiones
- *"¿Cuánta energía solar está generando España?"*
- *"Compara generación renovable vs fósil esta semana"*
- *"¿Cuáles son las emisiones de CO₂ actuales? (gCO₂/kWh)"*
- *"Muéstrame la tendencia de energía eólica en los últimos 30 días"*
- *"¿Qué porcentaje de la demanda viene de renovables?"*
- *"¿Cuándo fue el día más limpio (menos CO₂) este mes?"*

### 💰 Análisis de Precios y Mercado
- *"¿Cuál es el precio SPOT de electricidad ahora?"*
- *"Encuentra las horas más baratas para consumir electricidad hoy"*
- *"Compara tarifas PVPC entre días laborables y fines de semana"*
- *"¿Cuándo fue la electricidad más cara este mes? ¿Por qué?"*
- *"Muéstrame la correlación entre precios y generación renovable"*

### ⚙️ Estabilidad de Red y Almacenamiento
- *"¿Cómo está la estabilidad de la red ahora? (inercia síncrona vs renovable variable)"*
- *"¿Se están usando las centrales de bombeo para almacenar energía?"*
- *"Muéstrame los flujos de importación/exportación con Francia y Portugal"*
- *"¿Cuándo bombea agua la red y cuándo la turbina?"*

### 🔎 Descubrimiento de Datos
- *"Busca todos los indicadores relacionados con 'nuclear'"*
- *"¿Qué datos hay disponibles sobre generación hidroeléctrica?"*
- *"Muéstrame todos los indicadores de precios"*
- *"Lista los indicadores disponibles de emisiones y sostenibilidad"*

### 📈 Comparativas y Tendencias
- *"Compara la demanda de este mes vs el mismo mes del año pasado"*
- *"¿Cómo ha evolucionado la generación solar en los últimos 6 meses?"*
- *"Muéstrame el balance neto de exportación/importación del último mes"*
- *"¿Cuándo alcanzamos el pico histórico de generación renovable?"*

Claude usa automáticamente las herramientas correctas, obtiene los datos y los presenta en contexto con análisis detallado.

---

## 🎓 Aprende a Construir Proyectos como Este

Este proyecto fue creado por **[Javi Santos](https://www.linkedin.com/in/francisco-javier-santos-criado/)**, Especialista en IA y Robótica con investigación publicada en:
- 🔬 Detección de gasas quirúrgicas usando Redes Neuronales Convolucionales
- 🧠 Interpretabilidad de Modelos de Lenguaje en escenarios de conocimiento diverso

### 📚 La Escuela de IA

¿Quieres aprender IA **sin humo** y construir proyectos como este?

Únete a **[La Escuela de IA](https://skool.com/la-escuela-de-ia-9955)** - la comunidad española de aprendizaje de IA donde encontrarás:

- 🎯 **Práctica real** - Construye proyectos reales de IA, no ejemplos de juguete
- 🇪🇸 **Contenido en español** - Por fin, educación en IA en tu idioma
- 🛠️ **Recursos prácticos** - Código, tutoriales y ejemplos hands-on
- 👥 **Comunidad activa** - Aprende con otros entusiastas de la IA hispanohablantes

👉 **[Únete a La Escuela de IA](https://skool.com/la-escuela-de-ia-9955)**

### 📺 Canal de YouTube

Suscríbete a **[JavadexAI](https://www.youtube.com/@JavadexAI)** para:
- 🎥 Tutoriales de IA y recorridos de proyectos
- 💡 Aplicaciones de LLMs y servidores MCP
- 🚀 Estrategias de implementación de IA en el mundo real

### 🤝 Conecta

- **LinkedIn**: [Javi Santos](https://www.linkedin.com/in/francisco-javier-santos-criado/)
- **YouTube**: [@JavadexAI](https://www.youtube.com/@JavadexAI)
- **Escuela de IA**: [skool.com/la-escuela-de-ia-9955](https://skool.com/la-escuela-de-ia-9955)

---

## 🔥 Características Técnicas

### ✅ Listo para Producción
- Reintentos automáticos con backoff exponencial
- Manejo exhaustivo de errores y validación
- Async/await para rendimiento óptimo
- 96 tests exhaustivos con 90% cobertura

### 🏗️ Arquitectura Robusta
- **Domain-Driven Design** - Lógica de negocio pura
- **Clean Architecture** - Separación clara de responsabilidades
- **Principios SOLID** - Código mantenible y extensible
- **Type Safety** - 100% tipado con mypy modo estricto

### 📊 Datos Completos
- Acceso a **1.967+ indicadores** de REE
- Datos cada 5 minutos en tiempo real
- Histórico completo disponible
- 14 herramientas MCP especializadas

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Ver `CLAUDE.md` para guía detallada de desarrolladores.

Este código sigue principios arquitectónicos estrictos:
- Domain-Driven Design
- Clean Architecture
- Principios SOLID
- Testing exhaustivo

---

## 💬 Soporte y Recursos

### Problemas y Preguntas
- **Problemas del Servidor**: [Abrir un issue](https://github.com/ESJavadex/ree-mcp/issues)
- **Preguntas sobre API REE**: consultasios@ree.es

### Aprende Más
- 📚 [La Escuela de IA](https://skool.com/la-escuela-de-ia-9955) - Aprende IA en español
- 📺 [JavadexAI en YouTube](https://www.youtube.com/@JavadexAI)
- 🤝 [LinkedIn de Javi Santos](https://www.linkedin.com/in/francisco-javier-santos-criado/)

### Recursos
- **API eSios de REE**: https://api.esios.ree.es/
- **FastMCP**: https://github.com/jlowin/fastmcp
- **Model Context Protocol**: https://modelcontextprotocol.io/

---

## 📄 Licencia

**MIT License con Descargo de Responsabilidad** - Ver archivo `LICENSE` para detalles completos.

⚠️ **Proyecto Educativo**: Este software se proporciona "tal cual" sin garantías. Úsalo bajo tu propio riesgo.

---

<div align="center">

**Construido con ❤️ usando Domain-Driven Design y mejores prácticas modernas de Python**

⭐ **¡Dale una estrella al repo si te resulta útil!**

</div>