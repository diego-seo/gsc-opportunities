---
name: gsc-opportunities
description: Detecta oportunidades de mejora SEO en datos de Google Search Console usando la matriz de 4 cuadrantes (Posición × CTR). Usa este skill cuando el usuario suba datos de GSC (CSV, tabla, texto), pida "analizar oportunidades", "detectar quick wins", "qué puedo mejorar", "diagnóstico SEO", "análisis de rendimiento", o mencione queries, keywords, CTR, posiciones o impresiones de Search Console. También actívalo cuando pidan priorizar optimizaciones, encontrar páginas para mejorar snippets, identificar contenido cerca de primera página, o cualquier análisis orientado a acción sobre datos de GSC. NO es para generar informes mensuales completos (usa seo-reports para eso).
---

# GSC Opportunities Detector

Skill para diagnosticar datos de Google Search Console y detectar oportunidades de mejora priorizadas usando la metodología de los 4 cuadrantes.

## Filosofía

> "Optimizar con cabeza es mucho más efectivo que optimizar a lo loco. El tiempo es un recurso finito y debemos elegir con precisión quirúrgica dónde invertir nuestro esfuerzo para obtener el mayor retorno real."

Hay páginas que con 15 minutos de trabajo duplican su tráfico. Otras, ni con 15 horas logran mover la aguja. La diferencia está en el diagnóstico previo.

---

## Input esperado

El usuario proporciona datos de GSC en cualquier formato:

| Formato | Ejemplo |
|---------|---------|
| CSV exportado | Archivo de rendimiento de GSC |
| Tabla copiada | Datos pegados en el chat |
| Texto con métricas | "Tengo una keyword en posición 8 con CTR del 1.2%" |
| Captura de pantalla | Imagen del panel de GSC |

### Columnas requeridas (mínimo)

- Query o Keyword
- Clics
- Impresiones
- CTR (o calculable: clics/impresiones)
- Posición promedio

### Columnas opcionales que enriquecen el análisis

- URL/Página
- Dispositivo
- País
- Fecha/Período

---

## Las 4 métricas fundamentales

| Métrica | Qué revela |
|---------|------------|
| **Clics** | El tráfico real que entra |
| **Impresiones** | El mercado potencial |
| **CTR** | La Atracción: qué tan tentador es tu resultado |
| **Posición** | La Ubicación: el nivel de confianza que Google te otorga |

Solas son datos. Cruzadas en la matriz, son una hoja de ruta.

---

## La Matriz de Diagnóstico: 4 Cuadrantes

Al cruzar Ubicación (Posición) con Atracción (CTR), cada query cae en uno de estos estados:

### Cuadrante 1: Ranking Alto + CTR Alto → LOS GANADORES 🏆

**Criterio:** Posición ≤ 10 AND CTR ≥ CTR promedio del sitio

**Estado:** Top 10 y la gente hace clic.

**Acción:** **NO TOCAR.** Proteger. El esfuerzo para pasar de posición 2 a 1 es desproporcionado. Cualquier cambio estructural podría romper el equilibrio que Google ya premió.

**Etiqueta en output:** `🏆 Ganador - No tocar`

---

### Cuadrante 2: Ranking Alto + CTR Bajo → LOS INVISIBLES ATRACTIVOS 👻

**Criterio:** Posición ≤ 10 AND CTR < CTR promedio del sitio

**Estado:** Primera página, pero el usuario te ignora.

**El problema:** El snippet (title + meta description) es aburrido o no responde a la intención de búsqueda.

**Acción:** **MEJORAR SNIPPET.** Reescribir Title y Meta Description. Un mejor CTR no solo trae más visitas, sino que envía señal de relevancia a Google que mejorará el ranking.

**Tips específicos:**
- Revisar si hay Featured Snippets robando clics
- Usar plugins como Yoast para diseñar el snippet
- Si Google ignora tu meta description, probar sinónimos o lenguaje menos directo

**Etiqueta en output:** `👻 Invisible - Mejorar snippet`

**Impacto:** ALTO (ya estás en primera página)
**Esfuerzo:** BAJO (15 minutos por página)

---

### Cuadrante 3: Ranking Bajo + CTR Alto → LAS PROMESAS OCULTAS ⭐

**Criterio:** Posición > 10 AND CTR ≥ CTR promedio del sitio

**Estado:** Página 2 o inferior, pero quien te ve, hace clic.

**El problema:** Contenido atractivo para humanos, pero Google no tiene confianza técnica suficiente.

**Acción:** **MEJORAR CONTENIDO Y E-E-A-T.** Optimización on-page, estructura de títulos, enlaces internos, demostrar expertise.

**Por qué es la MAYOR OPORTUNIDAD:**
- Estás a un empujón de primera página
- El snippet ya funciona (CTR alto)
- Solo falta convencer a Google

**Prioridad especial:** Queries en posiciones 11-15 con buen CTR son las que más rápido saltan a primera página.

**Etiqueta en output:** `⭐ Promesa Oculta - Mejorar contenido`

**Impacto:** MUY ALTO (multiplicar tráfico al entrar a página 1)
**Esfuerzo:** MEDIO-ALTO (requiere trabajo de contenido)

---

### Cuadrante 4: Ranking Bajo + CTR Bajo → EL LASTRE 🗑️

**Criterio:** Posición > 10 AND CTR < CTR promedio del sitio

**Estado:** Ni te ven, ni interesas.

**Acción:** **EVALUAR O IGNORAR.** Si no es keyword estratégica para el negocio, es "basurilla digital". No malgastar tiempo rescatando lo que no tiene potencial.

**Excepciones para trabajar este cuadrante:**
- Keywords con volumen de impresiones muy alto (mercado grande)
- Keywords estratégicas para el negocio aunque no rindan aún
- Keywords transaccionales o de alta intención comercial

**Etiqueta en output:** `🗑️ Lastre - Evaluar si vale la pena`

---

## Umbrales dinámicos

Los umbrales no son fijos. Se adaptan al contexto real del sitio.

### Paso 1: Clasificar el sitio por madurez SEO

Antes de analizar, determinar en qué etapa está el sitio:

| Etapa | Señales típicas | Enfoque del análisis |
|-------|-----------------|---------------------|
| **Emergente** | <1K impresiones/mes, mayoría posiciones >30, pocos o cero clics | Buscar señales de vida, cualquier query con impresiones es oportunidad |
| **En crecimiento** | 1K-10K impresiones, mix de posiciones, algunos clics | Identificar dónde enfocar esfuerzos limitados |
| **Establecido** | 10K-100K impresiones, queries en primera página, clics constantes | Optimizar lo que ya funciona, escalar |
| **Maduro** | >100K impresiones, muchas keywords top 10, tráfico significativo | Refinamiento y protección de posiciones |

**Ojo:** Un sitio puede tener mucho contenido pero seguir siendo "emergente" en SEO si nunca se optimizó.

### Paso 2: Calcular líneas base relativas al sitio

#### CTR promedio (línea divisoria vertical)

**Fórmula:** `CTR_promedio = (Total clics / Total impresiones) * 100`

**Interpretación según etapa:**

| Etapa | CTR promedio típico | Qué significa |
|-------|---------------------|---------------|
| Emergente | 0.1% - 0.5% | Normal, posiciones bajas = pocos clics |
| En crecimiento | 0.5% - 2% | Empezando a captar atención |
| Establecido | 2% - 4% | Rendimiento saludable |
| Maduro | 3% - 6%+ | Snippets optimizados, buenas posiciones |

**Si el CTR promedio del sitio es muy bajo (<0.5%), no significa que todo esté mal.** Significa que el sitio está en etapa temprana y el análisis debe ajustarse.

#### Posición promedio (línea divisoria horizontal)

Usar la posición promedio del sitio, no un número fijo.

- Si posición promedio = 45, entonces "ranking alto" es < 45
- Si posición promedio = 12, entonces "ranking alto" es ≤ 10 (estándar)

**Ajuste para sitios emergentes:** Considerar "buena posición" todo lo que esté en top 30-50, no solo top 10.

### Paso 3: Umbral de impresiones (filtro de ruido)

| Etapa del sitio | Umbral mínimo | Razonamiento |
|-----------------|---------------|--------------|
| Emergente | ≥ 10 impresiones | Cada señal cuenta |
| En crecimiento | ≥ 30 impresiones | Filtrar el ruido mínimo |
| Establecido | ≥ 100 impresiones | Enfocarse en volumen real |
| Maduro | ≥ 500 impresiones | Priorizar impacto masivo |

### Paso 4: Ajustar la matriz al contexto

#### Para sitios EMERGENTES (bajo tráfico general)

La matriz tradicional no aplica igual. Usar esta adaptación:

| Cuadrante adaptado | Criterio | Interpretación |
|--------------------|----------|----------------|
| **Señales de vida** | Cualquier query con clics > 0 | ¡Algo está funcionando! Analizar qué y por qué |
| **Potencial detectado** | Impresiones > promedio del sitio, sin clics | Google te muestra, ahora toca atraer clics |
| **En el radar** | Posición < 50, cualquier impresión | Estás apareciendo, hay esperanza |
| **Invisibilidad total** | Posición > 50 o sin impresiones | Requiere trabajo estructural antes de optimizar |

**Mentalidad para sitios emergentes:** No buscar "quick wins de CTR" (no hay suficiente volumen). Buscar **dónde Google ya te está dando oportunidad** y construir desde ahí.

#### Para sitios EN CRECIMIENTO

Matriz híbrida:

- Usar cuadrantes tradicionales para queries con >100 impresiones
- Usar cuadrantes adaptados para el resto
- Priorizar queries donde ya hay ALGÚN clic (señal de relevancia)

#### Para sitios ESTABLECIDOS y MADUROS

Matriz tradicional de 4 cuadrantes aplica completamente.

---

## Análisis para sitios con datos limitados

### Cuando hay pocos o cero clics

**No significa que no haya oportunidades.** Significa que el análisis cambia:

1. **Enfocarse en impresiones:** ¿Dónde aparece el sitio aunque no genere clics?
2. **Analizar posiciones:** ¿Hay queries en posición 20-50? Esas son el punto de partida.
3. **Buscar patrones:** ¿Qué tipo de contenido genera más impresiones?

**Preguntas clave para sitios sin clics:**
- ¿Cuál es la query con más impresiones? → Ahí hay demanda
- ¿Cuál es la mejor posición lograda? → Eso es replicable
- ¿Hay alguna query con posición <30? → Oportunidad de subir

### Cuando el CTR es muy bajo en todo el sitio

Si el CTR promedio es <0.5%, el problema probablemente NO es el snippet individual. Puede ser:

1. **Problema de posición:** Si todo está en posición >20, el CTR bajo es consecuencia lógica
2. **Problema de intención:** El contenido no coincide con lo que busca el usuario
3. **Problema de competencia:** SERPs dominadas por resultados enriquecidos o grandes marcas

**Diagnóstico antes de optimizar:** Revisar manualmente las SERPs de las top queries para entender el contexto competitivo.

### Cuando las posiciones son todas malas (>30)

El sitio necesita **trabajo de cimientos** antes de optimización fina:

1. **Autoridad:** ¿Tiene backlinks? ¿Antigüedad?
2. **Contenido:** ¿Hay contenido suficiente y de calidad?
3. **Técnico:** ¿Indexación correcta? ¿Velocidad?

**Output adaptado:** En vez de "mejorar snippet", recomendar acciones estructurales.

---

## Señales de oportunidad en sitios emergentes

Aunque no haya clics ni posiciones top 10, buscar estas señales positivas:

| Señal | Qué indica | Acción |
|-------|------------|--------|
| Query con >50 impresiones | Google asocia tu sitio con ese tema | Fortalecer ese contenido |
| Posición <30 en alguna query | Estás en el juego para esa keyword | Optimizar esa página específica |
| Variedad de queries | El sitio tiene alcance temático | Identificar el cluster más fuerte |
| Query con 1-2 clics | Alguien te encontró y eligió | Analizar qué funcionó ahí |
| Mejor posición que el promedio | Contenido que Google valora más | Replicar lo que hace esa página |

---

## Recomendaciones adaptadas por etapa

### Para sitio EMERGENTE

```
🌱 DIAGNÓSTICO: Sitio en etapa emergente

Tu sitio tiene [X] impresiones totales y [Y] clics. 
Esto es normal para un sitio [nuevo/no optimizado/de nicho pequeño].

📍 DÓNDE ESTÁS:
- Posición promedio: [X] (lejos de primera página)
- CTR promedio: [X]% (bajo, pero esperado para estas posiciones)

✅ SEÑALES POSITIVAS ENCONTRADAS:
1. [Query con más impresiones] → Google te asocia con este tema
2. [Query con mejor posición] → Tu contenido más valorado

🎯 PRÓXIMOS PASOS (en orden):
1. Fortalecer el contenido de [página con mejor señal]
2. Crear contenido relacionado con [cluster temático detectado]
3. Trabajar autoridad: enlaces internos, backlinks básicos

⏳ EXPECTATIVA: En sitios emergentes, los resultados toman 3-6 meses.
No optimizar snippets aún (primero necesitas posiciones decentes).
```

### Para sitio EN CRECIMIENTO

```
📈 DIAGNÓSTICO: Sitio en crecimiento

Tienes señales mixtas: algunas queries funcionan, otras no.
Es momento de enfocar recursos en lo que ya muestra tracción.

🔥 OPORTUNIDADES DETECTADAS:
[Lista priorizada combinando matriz tradicional + adaptada]

🎯 ENFOQUE RECOMENDADO:
1. Quick wins en queries con posición <20 (ya tienes pie adentro)
2. Expandir contenido en el cluster temático más fuerte
3. Ignorar queries en posición >40 por ahora
```

### Para sitio ESTABLECIDO/MADURO

Usar el output estándar de la matriz de 4 cuadrantes.

---

## Output del análisis

### Estructura del análisis

```
1. RESUMEN DEL DATASET
   - Total queries analizadas
   - Total clics / impresiones
   - CTR promedio (línea base)
   - Posición promedio
   - Queries filtradas por bajo volumen

2. DISTRIBUCIÓN POR CUADRANTE
   - Ganadores: X queries (Y% del total)
   - Invisibles: X queries
   - Promesas Ocultas: X queries
   - Lastre: X queries

3. TOP OPORTUNIDADES PRIORIZADAS
   
   🔥 QUICK WINS (Impacto alto + Esfuerzo bajo)
   Queries del cuadrante "Invisibles" ordenadas por impresiones
   → Acción: Mejorar snippet
   
   ⭐ PROMESAS OCULTAS PRIORITARIAS
   Queries en posición 11-15 con CTR alto, ordenadas por impresiones
   → Acción: Mejorar contenido
   
   📈 OPORTUNIDADES SECUNDARIAS
   Resto de promesas ocultas (posición 16-20)

4. TABLA DETALLADA
   Query | Pos | CTR | Impr | Clics | Cuadrante | Acción

5. RECOMENDACIONES ESPECÍFICAS
   Para cada oportunidad top, incluir:
   - Qué hacer concretamente
   - Por qué (dato que lo respalda)
   - Impacto esperado
```

### Priorización automática

Ordenar oportunidades por esta lógica:

1. **Primero:** Invisibles con más impresiones (quick wins de 15 min)
2. **Segundo:** Promesas Ocultas en posición 11-15 (a punto de explotar)
3. **Tercero:** Promesas Ocultas en posición 16-20
4. **Cuarto:** Lastre con impresiones muy altas (evaluar caso por caso)

---

## Detección de patrones adicionales

Además de la matriz básica, detectar:

### Cannibalizaciones potenciales

Múltiples URLs rankeando para la misma query o queries muy similares. Señal: misma keyword aparece con diferentes páginas.

### Clusters temáticos

Queries relacionadas que sufren el mismo problema. Permite optimizaciones globales más inteligentes.

### Pogo-sticking potencial

Queries con CTR alto pero posición que baja con el tiempo. Puede indicar que el contenido no satisface la intención.

---

## Formato de entrega

El output puede ser:

| Formato | Cuándo usarlo |
|---------|---------------|
| **Análisis conversacional** | Por defecto, respuesta directa en el chat |
| **Tabla resumen** | Si hay muchas queries, tabla con las top oportunidades |
| **Documento Word** | Si el usuario pide informe formal (usar skill docx) |
| **Excel** | Si el usuario pide datos para trabajar (usar skill xlsx) |

---

## Ejemplos de análisis

### Ejemplo 1: Query en sitio establecido

**Input del usuario:**
```
Query: "recetas de pollo"
Clics: 45
Impresiones: 8,500
CTR: 0.53%
Posición: 7.2
```

**Análisis:**
```
📊 Diagnóstico: INVISIBLE ATRACTIVO (Cuadrante 2)

Situación: Estás en posición 7 (primera página), pero tu CTR de 0.53% 
está muy por debajo del benchmark (~3-5% para posición 7).

🔥 QUICK WIN detectado

Problema: El snippet no está atrayendo clics. Con 8,500 impresiones, 
estás dejando ~400 clics potenciales sobre la mesa.

Acción inmediata (15 minutos):
1. Revisar el Title actual - ¿incluye la keyword principal?
2. Reescribir Meta Description con beneficio claro
3. Verificar si hay Featured Snippet robando clics

Impacto estimado: Si subes CTR a 2%, pasarías de 45 a 170 clics/mes 
(+278%) sin cambiar tu posición.
```

### Ejemplo 2: Sitio emergente con poco tráfico

**Input del usuario:**
```
Total queries: 47
Total impresiones: 890
Total clics: 3
CTR promedio: 0.34%
Posición promedio: 52

Top queries:
- "software contable pymes colombia" | Pos: 34 | Impr: 120 | Clics: 1
- "programa facturación electrónica" | Pos: 48 | Impr: 95 | Clics: 0
- "contabilidad para emprendedores" | Pos: 29 | Impr: 78 | Clics: 2
- "cómo llevar contabilidad negocio" | Pos: 55 | Impr: 65 | Clics: 0
```

**Análisis:**
```
🌱 DIAGNÓSTICO: Sitio en etapa EMERGENTE

Con 890 impresiones y 3 clics mensuales, tu sitio está empezando 
a aparecer en el radar de Google. La posición promedio de 52 indica 
que aún no compites en primera página, pero hay señales positivas.

✅ SEÑALES DE VIDA DETECTADAS:

1. ⭐ "contabilidad para emprendedores" (Pos: 29, 2 clics)
   → TU MEJOR ACTIVO. Posición 29 = página 3, pero ya genera clics.
   → Google valora este contenido más que el resto.
   → ACCIÓN: Expandir y fortalecer esta página primero.

2. 📍 "software contable pymes colombia" (Pos: 34, 120 impr)
   → Mayor volumen de impresiones = demanda real del mercado.
   → 1 clic con posición 34 es buena señal.
   → ACCIÓN: Crear contenido más profundo sobre este tema.

3. 🎯 Cluster temático claro: Contabilidad + Pymes + Colombia
   → Google asocia tu sitio con este nicho. Eso es bueno.

❌ QUÉ NO HACER AHORA:
- No optimices snippets (primero necesitas posiciones <20)
- No te disperses en muchas keywords
- No esperes resultados en semanas (esto toma 3-6 meses)

🎯 PLAN DE ACCIÓN PRIORIZADO:

1. SEMANA 1-2: Fortalecer "contabilidad para emprendedores"
   - Expandir contenido (>1500 palabras)
   - Mejorar estructura de headings
   - Agregar enlaces internos desde otras páginas

2. SEMANA 3-4: Crear contenido satelite
   - "Cómo elegir software contable para pymes"
   - "Guía facturación electrónica Colombia 2024"
   
3. MENSUAL: Monitorear si la posición de tus mejores queries baja de 30.
   Cuando estés en posición <20, ahí sí aplica optimización de snippets.

📊 EXPECTATIVA REALISTA:
- Mes 1-2: Posiciones empiezan a mejorar
- Mes 3-4: Primeras queries entrando a página 2-3
- Mes 5-6: Posibilidad de primera página si el contenido es sólido
```

### Ejemplo 3: Sitio con cero clics pero impresiones

**Input del usuario:**
```
Mi sitio tiene 2,400 impresiones pero 0 clics. ¿Qué hago?
```

**Análisis:**
```
🔍 DIAGNÓSTICO: Visibilidad sin conversión

2,400 impresiones con 0 clics no es raro. Veamos qué significa:

PRIMERO: ¿Cuál es tu posición promedio?

→ Si posición promedio > 30: 
  El CTR de 0% es NORMAL. En posición 30+, nadie te ve realmente.
  No es problema de snippet, es problema de posición.

→ Si posición promedio 10-30:
  Hay un problema. Deberías tener algunos clics.
  Posibles causas:
  - Snippets muy malos (titles sin sentido)
  - Intención de búsqueda no coincide
  - SERPs dominadas por resultados enriquecidos

→ Si posición promedio < 10:
  Algo raro pasa. ¿Los datos están filtrados correctamente?
  ¿Es un período muy corto (pocos días)?

SIGUIENTE PASO:
Comparte las top 5 queries con su posición para diagnosticar 
si el problema es de ubicación o de atracción.
```

---

## Diferencia con skill seo-reports

| Aspecto | gsc-opportunities | seo-reports |
|---------|-------------------|-------------|
| **Propósito** | Detectar qué mejorar ahora | Reportar rendimiento mensual |
| **Output** | Acciones priorizadas | Documento ejecutivo |
| **Audiencia** | El SEO/marketer que va a optimizar | Stakeholders no técnicos |
| **Enfoque** | "¿Qué hago primero?" | "¿Cómo vamos vs mes anterior?" |
| **Formato típico** | Conversacional o tabla | Word formal |

---

## Checklist de análisis

- [ ] Calcular CTR promedio como línea base
- [ ] Filtrar queries con bajo volumen de impresiones
- [ ] Clasificar cada query en su cuadrante
- [ ] Identificar quick wins (Invisibles con más impresiones)
- [ ] Destacar Promesas Ocultas en posición 11-15
- [ ] Detectar patrones (cannibalizaciones, clusters)
- [ ] Priorizar por impacto/esfuerzo
- [ ] Dar acciones específicas para el top de oportunidades

---

## Dependencias

Ninguna específica. El análisis se hace con la información proporcionada.

Si el usuario pide output en Word → usar skill `docx`
Si el usuario pide output en Excel → usar skill `xlsx`

---

## Créditos

Metodología basada en el framework de diagnóstico de visibilidad web de Diego González.
