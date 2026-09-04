# Testing de Consistencia y Trazabilidad para Desarrollo Asistido por IA

> **Módulo avanzado** · Unidad 6 · Herramientas, Tecnologías e Integración
>
> Este módulo complementa la [Unidad 6 — Integración y Prueba](../06-integracion-y-prueba/README.md) y el [ADR-006 del proyecto modelo](https://github.com/IES9018/proyecto-adi-2026/blob/main/03-proyectos/A-gobernanza-digital/03_ARQUITECTURA/adr/ADR-006-estrategia-testing.md). No duplica la pirámide de testing ni la teoría de CI/CD: los reutiliza y lleva al siguiente nivel.

---

## 1. Vocabulario inicial

Si alguno de estos términos te suena nuevo, pará y leé la definición antes de continuar. No se da por sabido.

| Término | Definición | Analogía |
|:--------|:-----------|:---------|
| **E2E** (End-to-End) | Prueba que simula el recorrido completo de un usuario, desde abrir la app hasta que la operación se confirma. | Hacer el recorrido completo de un trámite en una sede gubernamental: entrás, llenás el formulario, lo entregás, te dan el comprobante. |
| **Test case** (caso de prueba) | Descripción de una situación concreta que se va a verificar: qué se hace, qué se espera, qué pasa. | Una receta de cocina con los pasos exactos y el resultado esperado. |
| **Test suite** (suíte de pruebas) | Conjunto organizado de casos de prueba que se ejecutan juntos. | El libro de recetas completo de un restaurante. |
| **Assertion** (aserción) | Afirmación que verificá: "esto tiene que ser verdad". Si no lo es, el test falla. | Decir "la temperatura del horno tiene que ser 180°" y verificar con un termómetro. |
| **Test oracle** (oráculo de prueba) | La fuente de verdad que define si el resultado es correcto o no. | El enunciado del examen: sin él, no sabés si tu respuesta está bien. |
| **Fixture** | Conjunto de datos y configuración preparada antes de ejecutar un test. | Los ingredientes pesados y listos antes de empezar a cocinar. |
| **Seed** | Estado inicial conocido que se carga en el sistema antes de los tests. | La masa base que ya tenés lista para hacer cualquier pizza. |
| **Reset** | Acción de devolver el sistema a un estado limpio después de cada test. | Lavar los platos entre recetas para que no se mezclen los sabores. |
| **Teardown** | Limpieza final después de que todos los tests terminaron. | Lavajar toda la cocina cuando cerrás el restaurante. |
| **Selector** | Identificador que Playwright usa para encontrar un elemento en la pantalla. | La dirección postal que le das al cadetero para encontrar tu casa. |
| **Trace** (traza) | Registro detallado de todo lo que pasó durante la ejecución de un test, incluyendo screenshots cuando falla. | La cámara de seguridad que graba todo lo que pasó en la tienda. |
| **Flaky test** (test inestable) | Test que a veces pasa y a veces falla sin que el código haya cambiado. | Un foco que parpaea: a veces anda, a veces no, y no sabés por qué. |
| **Smoke test** (test de humo) | Prueba rápida que verifica que lo más básico funcione antes de hacer pruebas más profundas. | Prender el auto y ver que enciende antes de revisar el motor. |
| **Happy path** (camino feliz) | El escenario donde todo sale bien, sin errores ni excepciones. | Ir al supermercado, encontrar todo, pagar y volver a casa sin problemas. |
| **Secret** (secreto) | Credencial sensible que no debe exponerse: API key, contraseña, token JWT. | La llave de tu casa: si la perdés, cualquiera puede entrar. |
| **Secret scanning** (escaneo de secretos) | Herramienta que busca credenciales hardcodeadas en código y documentación. | Un detector de metales en el aeropuerto: busca cosas que no deberían estar ahí. |
| **Credential rotation** (rotación de credenciales) | Cambiar una contraseña o token que pudo haberse expuesto. | Cambiar la cerradura de tu casa si perdiste la llave. |
| **Redaction** (redacción) | Ocultar información sensible en reportes y logs. | Tapar los números de tu tarjeta de crédito en una foto. |

---

## 2. Testing como producción de evidencia

Tester no es "ver si anda". Tester es **producir evidencia verificable** de que el sistema cumple lo que promete.

La evidencia tiene tres componentes:

1. **Fuente** (oráculo): ¿qué dice que debería pasar? (SPEC, caso de uso, ADR, regla de negocio)
2. **Ejecución** (test): ¿qué se hizo concretamente?
3. **Resultado** (reporte): ¿qué se observó y qué se concluyó?

Sin fuente, no hay criterio. Sin ejecución, no hay prueba. Sin resultado, no hay evidencia.

> **Para recordar:** Un test que pasa sin aserciones significativas no es evidencia. Es solo ruido.

---

## 3. Pirámide de pruebas (reutilización)

Ya conocés la pirámide de la [Unidad 6 — Integración y Prueba](../06-integracion-y-prueba/README.md):

```
        /\
       / E2E\        ← Pocos, lentos, costosos. Solo flujos críticos.
      /------\
     / Integración\  ← Medios. Verifican conexión entre capas.
    /--------------\
   /    Unitarios    \ ← Muchos, rápidos, baratos. Lógica pura.
  /------------------\
```

**Lo que cambia en este módulo:** no agregamos más tests E2E. Aprendemos a **seleccionar cuáles** E2E construir y **qué pueden demostrar realmente**.

| Nivel | Cuándo usar | Cuándo NO usar |
|:------|:------------|:---------------|
| Unitario | Lógica de negocio, validaciones, cálculos | Conexión entre capas, UI |
| Integración | API + DB, frontend + API, contratos | Experiencia completa del usuario |
| E2E | Flujos críticos del usuario, regresión visual | Cada funcionalidad, cada validación |

---

## 4. Qué puede y qué NO puede validar un E2E

Esta es la sección más importante del módulo. Un navegador puede verificar comportamiento observable, no arquitectura ni decisiones internas.

### Lo que SÍ puede validar un E2E

| Qué se valida | Cómo se verifica | Ejemplo |
|:--------------|:-----------------|:--------|
| Flujos del usuario | Navegar y completar pasos | Login → ver dashboard |
| Validación de formularios | Enviar datos inválidos | Sin email → mensaje de error |
| Persistencia observable | Logout → re-login → datos presentes | Registro persiste tras reiniciar |
| Control de acceso | Intentar acceder sin permiso | Usuario sin rol → redirigido a login |
| Mensajes de error | Producir errores intencionalmente | Campo vacío → "Este campo es obligatorio" |
| Navegación | Verificar que los links funcionan | Click en "Inicio" → llega al home |
| Respuesta a interacciones | Doble clic, botones, formularios | Click rápido → no crea registro duplicado |

### Lo que NO puede validar un E2E (y necesita otra técnica)

| Qué se quiere validar | Por qué E2E no alcanza | Técnica adecuada |
|:----------------------|:-----------------------|:-----------------|
| Arquitectura hexagonal | El navegador no ve la estructura interna | Revisión arquitectónica, análisis estático |
| Uso de estado global | El navegador no inspecta el framework | Unitarios, code review |
| ADR de autenticación JWT | El navegador ve "logueado", no ve el token | Integración, test de API |
| Contrato frontend-API | El navegador no ve las llamadas HTTP | Tests de contrato |
| Modelo de datos | El navegador no consulta la DB directamente | Integración |
| Reglas de negocio complejas | Pueden requerir cálculos que el navegador no observa | Unitarios |
| Rendimiento real | El navegador no mide tiempos internos | Lighthouse, benchmarks |
| Seguridad profunda | OWASP va más allá de lo visible | Análisis estático, pentest |

> **Para recordar:** Un E2E que pasa demuestra que el usuario puede completar un flujo. No demuestra que la arquitectura esté bien diseñada, que los ADR se respeten o que el código sea mantenible.

### Matriz de capacidades

| Elemento | E2E | Integración | Unitario | Revisión humana | Análisis estático |
|:---------|:---:|:-----------:|:--------:|:---------------:|:-----------------:|
| SPEC y requisitos | ✅ | ⚠️ | ⚠️ | ✅ | ❌ |
| Casos de uso | ✅ | ⚠️ | ❌ | ✅ | ❌ |
| Reglas de negocio | ⚠️ | ✅ | ✅ | ⚠️ | ❌ |
| ADR arquitectónico | ❌ | ⚠️ | ❌ | ✅ | ✅ |
| Contrato API | ⚠️ | ✅ | ✅ | ❌ | ✅ |
| Modelo de datos | ❌ | ✅ | ✅ | ❌ | ⚠️ |
| Wireframe vs implementación | ❌ | ❌ | ❌ | ✅ | ❌ |
| UX real | ❌ | ❌ | ❌ | ✅ | ❌ |
| Accesibilidad | ⚠️ | ❌ | ❌ | ✅ | ⚠️ |
| Seguridad de roles | ✅ | ✅ | ✅ | ⚠️ | ✅ |

- ✅ = técnica principal
- ⚠️ = parcialmente validable
- ❌ = no aplica

---

## 5. Oráculo de prueba

Un **test oracle** (oráculo de prueba) es la fuente de verdad que define si el resultado es correcto. Sin oráculo, estás adivinando.

### Jerarquía de oráculos

Cuando un test produce un resultado, ¿contra qué lo comparás?

1. **SPEC o requisito vigente y aprobado** → la fuente primaria
2. **Regla de negocio confirmada** → lo que el negocio define como correcto
3. **Caso de uso vigente** → el flujo documentado
4. **ADR aceptado** → para decisiones técnicas
5. **Contrato de API o modelo de datos** → para contratos entre capas
6. **Wireframe o prototipo** → para interfaz
7. **Código implementado** → solo como último recurso

> **Importante:** El código NO es un oráculo. Si el código hace algo distinto a lo que dice el SPEC, el que está mal es el código, no el SPEC.

### Protocolo de contradicciones

Cuando dos fuentes difieran (ej: el SPEC dice una cosa y el código hace otra):

1. **Registrar** la inconsistencia con archivo, sección y versión.
2. **No modificar** automáticamente ni código ni documentación.
3. **Determinar** cuál fuente necesita una decisión.
4. **Resolver** mediante revisión del estudiante y profesor.
5. **Actualizar** la fuente incorrecta.
6. **Ejecutar** nuevamente la prueba.

### Estados para la matriz de trazabilidad

| Estado | Significado |
|:-------|:------------|
| **Pasa** | El comportamiento observado coincide con el oráculo |
| **Falla** | El comportamiento observado no coincide |
| **Parcial** | Cumple parcialmente, falta algo |
| **No evaluado** | No se pudo verificar con esta técnica |
| **Bloqueado** | No se puede evaluar por contradicción entre fuentes |

---

## 6. Matriz de trazabilidad

La matriz de trazabilidad es el corazón del módulo. Conecta cada requisito con su prueba y su evidencia.

### Estructura

| ID | Fuente | Comportamiento esperado | Tipo de prueba | Evidencia | Resultado |
|:---|:-------|:------------------------|:---------------|:----------|:----------|
| RF-01 | SPEC §3.1 | El sistema permite registrar un usuario con email y contraseña | E2E | Trace + reporte | Pasa |
| CU-01.3 | Caso de uso | Si el email ya existe, mostrar mensaje de error | E2E + humano | Captura | Parcial |
| RN-04 | Regla de negocio | Impedir registros con emails duplicados | Unitario + integración | Test | Pasa |
| ADR-003 | ADR | Autenticación mediante JWT | Integración/revisión | Test API | No evaluado por E2E |

### Cómo construirla

1. **Listar** los requisitos clave de tu SPEC (RF-01, RF-02, etc.)
2. **Identificar** el oráculo para cada uno
3. **Decidir** qué técnica de prueba aplica (E2E, integración, unitario, humano)
4. **Ejecutar** la prueba
5. **Registrar** el resultado con evidencia

> **Para recordar:** No todo se prueba con E2E. La matriz te obliga a pensar cuál técnica es adecuada para cada afirmación.

---

## 7. Selección de flujos críticos

No podés testear todo con E2E. Es costoso, lento y frágil. Elegí con criterio.

### Criterios para elegir un flujo crítico

| Criterio | Pregunta |
|:---------|:---------|
| **Frecuencia** | ¿Lo usan todos los días? |
| **Impacto** | ¿Si falla, se pierden datos o dinero? |
| **Complejidad** | ¿Tiene múltiples pasos y decisiones? |
| **Regresión** | ¿Se ha roto antes? |
| **Visible** | ¿Lo ve el usuario final? |

### Ejemplo: selección para un sistema de gestión de solicitudes

| Flujo | ¿Crítico? | Por qué |
|:------|:----------|:--------|
| Login | ✅ Sí | Sin login no hay uso del sistema |
| Crear solicitud | ✅ Sí | Función principal del sistema |
| Evaluar solicitud | ✅ Sí | Decisión de negocio crítica |
| Ver historial | ⚠️ Parcial | Importante pero no crítico |
| Exportar PDF | ❌ No | Funcionalidad secundaria |

---

## 8. Datos sintéticos

Los datos sintéticos son datos de prueba creados intencionalmente para los tests. Nunca usés personas reales ni datos de producción.

### Conceptos clave

| Concepto | Definición | Ejemplo |
|:---------|:-----------|:--------|
| **Seed** | Estado inicial conocido | "Sistema con 3 usuarios y 5 solicitudes" |
| **Fixture** | Datos reutilizables para un test | "Usuario solicitante con email y contraseña conocidos" |
| **Reset** | Devolver el sistema a estado limpio | Borrar todos los usuarios creados en el test |
| **Teardown** | Limpieza final después de la suite | Cerrar conexiones, borrar archivos temporales |
| **Determinismo** | Mismo test = mismo resultado | No depender de la fecha actual ni de datos aleatorios |
| **Aislamiento** | Tests independientes entre sí | El test de login no debe depender del test de registro |
| **Idempotencia** | Poder preparar el ambiente varias veces sin duplicar | Crear el mismo usuario dos veces no debería fallar ni duplicar |

### Ejemplo de usuarios sintéticos

| Usuario sintético | Rol | Uso en tests |
|:------------------|:----|:-------------|
| `solicitante.e2e@example.test` | Solicitante | Crear y verificar solicitudes |
| `tecnico.e2e@example.test` | Técnico | Evaluar solicitudes |
| `directivo.e2e@example.test` | Directivo | Aprobar o rechazar |
| `sin-permiso.e2e@example.test` | Rol restringido | Verificar que el sistema rechaza el acceso |

### Reglas obligatorias

| Regla | Por qué |
|:------|:--------|
| Usar dominios reservados (`example.test`, `test.com`) | Evitar envíos reales de email |
| No usar personas reales | Privacidad y datos ficticios controlados |
| No copiar datos institucionales | Proteger información real |
| No enviar emails, WhatsApp ni notificaciones reales | Los tests no deben afectar el mundo real |
| No ejecutar contra producción | Producción tiene datos reales de personas |
| No depender de datos que otros modifican | Aislamiento entre estudiantes |
| No subir dumps con información personal | Seguridad y privacidad |
| No incluir capturas con datos reales | Los datos reales no deben aparecer en evidencia |

### Protección con `E2E_BASE_URL`

El sistema de tests debe verificar que solo se ejecuta contra ambientes autorizados:

```javascript
// Al inicio de la suite de tests
const baseUrl = process.env.E2E_BASE_URL;
if (!baseUrl || (!baseUrl.includes('localhost') && !baseUrl.includes('127.0.0.1'))) {
  throw new Error('E2E_BASE_URL debe ser localhost o un dominio autorizado');
}
```

> **Para recordar:** Una advertencia escrita no sustituye una protección técnica. El test debe detenerse si detecta una URL productiva.

---

## 9. Playwright y navegación real

Playwright es la herramienta E2E oficial de este módulo. Puppeteer puede mencionarse como alternativa, pero no se configura aquí.

### Por qué Playwright y no Puppeteer

| Característica | Playwright | Puppeteer |
|:---------------|:-----------|:----------|
| Navegadores soportados | Chromium, Firefox, WebKit | Solo Chromium |
| Esperas automáticas | Sí | Parcial |
| Fixtures para datos | Sí (test project) | No |
| Capturas y video | Sí, con trace | Sí, básico |
| Selectores accesibles | Rol, etiqueta, texto | Limitados |
| Soporte multi-usuario | Sí | No |

### Instalación mínima

```bash
# En la raíz de tu proyecto
npm init -y
npm install -D @playwright/test
npx playwright install chromium
```

### Archivo de configuración básico

```javascript
// playwright.config.js
const { defineConfig } = require('@playwright/test');

module.exports = defineConfig({
  testDir: './e2e',
  timeout: 30000,
  retries: 0,                    // No reintentar flaky tests
  workers: 1,                    // Serial cuando los datos no estén aislados
  use: {
    baseURL: process.env.E2E_BASE_URL || 'http://localhost:3000',
    screenshot: 'only-on-failure',
    trace: 'on-first-retry',
  },
});
```

### Orden de selectores (de más estable a menos)

1. **Rol y nombre accesible:** `page.getByRole('button', { name: 'Registrarse' })`
2. **Etiqueta del campo:** `page.getByLabel('Correo electrónico')`
3. **Texto visible:** `page.getByText('Registro exitoso')`
4. **`data-testid`:** `page.locator('[data-testid="submit-btn"]')` — último recurso

> **Para recordar:** `data-testid` no es un selector semántico. Es un recurso técnico de respaldo. Si podés usar rol, etiqueta o texto visible, hacelo.

### Lo que NO debe hacerse

| Anti-patrón | Por qué está mal | Cómo hacerlo |
|:------------|:-----------------|:-------------|
| `waitForTimeout(5000)` | Pausa fija, innecesaria, inestable | Esperar un elemento, URL o mensaje |
| Reintentos para ocultar flaky | Enmascara problemas reales | Arreglar la causa del flaky |
| Selectores por posición (`nth-child`) | Se rompen con cambios de UI | Usar selectores semánticos |
| Testear implementación (IDs internos) | Cambia con refactorizaciones | Testear comportamiento |

---

## 10. Aserciones

Las aserciones son el corazón de un test. Sin aserciones significativas, el test no prueba nada.

### Buenas aserciones

```javascript
// ✅ Verificar que el mensaje de éxito aparece
await expect(page.getByText('Registro exitoso')).toBeVisible();

// ✅ Verificar que el usuario fue redirigido
await expect(page).toHaveURL('/dashboard');

// ✅ Verificar que un campo tiene un valor
await expect(page.getByLabel('Nombre')).toHaveValue('Juan Pérez');

// ✅ Verificar que un botón está habilitado
await expect(page.getByRole('button', { name: 'Guardar' })).toBeEnabled();
```

### Malas aserciones

```javascript
// ❌ Solo verificar que no hay error (no prueba nada específico)
const error = await page.locator('.error').count();
expect(error).toBe(0);

// ❌ Verificar que un elemento existe (puede estar oculto)
const elem = await page.locator('#mi-elemento').count();
expect(elem).toBe(1);
```

---

## 11. Determinismo y flaky tests

Un test debe ser **determinista**: mismo input, mismo resultado, siempre.

### Causas comunes de flaky tests

| Causa | Ejemplo | Solución |
|:------|:--------|:---------|
| Datos compartidos | Dos tests crean el mismo usuario | Aislamiento o reset entre tests |
| Tiempo real | `new Date()` en el test | Mockear la fecha o usar seed |
| Red | Llamadas a servicios externos | Mockear servicios o usar fixtures |
| UI asíncrona | Elemento que carga después | Esperar el estado, no un tiempo |
| Orden de ejecución | Test B depende de que A corra primero | Cada test debe ser independiente |

### Regla de oro

> Si un test falla, debe fallar siempre en las mismas condiciones. Si a veces pasa y a veces no, es un flaky test y hay que arreglarlo, no ignorarlo.

---

## 12. Evidencias de ejecución

La evidencia es lo que demostrás al profesor o al tribunal.

### Qué entregar

| Evidencia | Descripción | Formato |
|:----------|:------------|:--------|
| **Reporte de ejecución** | Salida completa de Playwright | Archivo HTML o JSON |
| **Trace** | Registro detallado con screenshots al fallar | Archivo `.zip` de Playwright |
| **Matriz de trazabilidad** | Tabla completa con resultados | Markdown |
| **Capturas de inspección humana** | Screenshots deliberados de UI/UX | PNG con justificación |

### Cuándo capturar

| Momento | Capturar | No capturar |
|:--------|:---------|:------------|
| Test pasa | No (o una mínima si es documental) | Captura innecesaria |
| Test falla | Sí, siempre (screenshot + trace) | — |
| Inspección humana | Sí, 1-2 capturas con justificación | Acumular capturas sin sentido |

---

## 13. UI, UX, QA y accesibilidad

Estos cuatro conceptos se confunden frecuentemente. Son diferentes.

### Definiciones

| Concepto | Definición | Ejemplo |
|:---------|:-----------|:--------|
| **UI** (User Interface) | Los elementos con los que la persona interactúa: botones, campos, colores, disposición. | El formulario de registro con sus campos y botón "Enviar". |
| **UX** (User Experience) | Qué tan comprensible, confiable, eficiente y satisfactoria resulta la experiencia completa. | Si el usuario entiende qué hacer, si siente confianza, si no se frustra. |
| **QA** (Quality Assurance) | Conjunto de procesos para prevenir y detectar problemas de calidad. Incluye automatización y revisión humana. | La suite de tests, el code review, la auditoría de seguridad. |
| **QA visual** | Detección de cambios inesperados en la apariencia. | Comparar screenshots entre versiones para detectar regresiones visuales. |
| **Prueba de usabilidad** | Observar a una persona intentando completar una tarea. | Pedirle a alguien que se registre sin explicarle nada y ver qué tan fácil le resulta. |

### Qué puede automatizarse y qué requiere humano

|Qué se verifica | Automatización | Humano |
|:---------------|:--------------:|:------:|
| Botón funciona al hacer clic | ✅ | — |
| Mensaje de error aparece | ✅ | — |
| Mensaje es comprensible | — | ✅ |
| Usuario sabe qué hacer después | — | ✅ |
| Formulario se ve bien en distintos tamaños | ⚠️ Parcial | ✅ |
| Navegación con teclado funciona | ⚠️ Parcial | ✅ |
| Colores tienen suficiente contraste | ✅ | ✅ |
| La experiencia genera confianza | — | ✅ |

### Ejemplos que DEBE revisar una persona

1. **Registro guardado sin confirmación:** El sistema guarda, pero no muestra "Registro exitoso". El usuario no sabe si se guardó.
2. **Doble clic crea duplicados:** El botón permite clics rápidos y crea dos registros iguales.
3. **Error técnico visible:** Aparece "Error 409" en vez de "Ese correo ya está registrado".
4. **Pérdida de datos:** El formulario borra todos los campos después de un error de validación.
5. **Confirmación efímera:** El mensaje de éxito aparece 1 segundo y desaparece. Nadie lo lee.
6. **Usuario perdido:** Después del registro, queda en la misma pantalla sin orientación.
7. **Jerarquía visual invertida:** El botón "Cancelar" tiene más destaque que "Guardar".
8. **Inaccesibilidad con teclado:** La aplicación funciona con mouse pero no se puede navegar con Tab.
9. **Sin indicador de progreso:** Un proceso tarda 10 segundos sin mostrar que está trabajando.
10. **Sesión expirada sin aviso:** El sistema deja de responder sin explicar que la sesión caducó.
11. **Éxito fantasma:** El mensaje dice "éxito" pero el registro no quedó persistido.

### Sobre el costo de la automatización visual con IA

La comparación visual determinista (diferencias de píxeles) puede ser económica y no necesita un LLM. Lo costoso es enviar grandes cantidades de capturas a un modelo visual para que emita juicios de UX. Además, aunque hubiera presupuesto, **un modelo no reemplaza completamente a usuarios reales**. La UX requiere criterio humano sobre claridad, confianza, frustración y adecuación al contexto.

---

## 14. Desarrollo asistido por IA

La IA puede ayudarte a crear, explicar y revisar pruebas. Pero el estudiante debe comprenderlas y defenderlas.

### Qué pedirle a la IA

| Tarea | Ejemplo de prompt |
|:------|:------------------|
| Explicar un test | "Explicá qué verifica este test y por qué es importante" |
| Relacionar aserción con requisito | "¿Qué requisito de mi SPEC demuestra esta aserción?" |
| Proponer casos borde | "¿Qué pasa si el email tiene caracteres especiales?" |
| Revisar selectores frágiles | "¿Este selector es estable o se romperá con cambios de UI?" |
| Detectar partes no cubiertas | "¿Qué escenarios de mi caso de uso NO tienen test?" |
| Generar datos sintéticos | "Creá fixtures para un usuario solicitante con email y contraseña" |
| Preparar preguntas de defensa | "¿Qué preguntas podría hacerme el profesor sobre esta suite?" |

### Cuestionar a la IA

| Pregunta | Por qué importa |
|:---------|:----------------|
| ¿Qué fuente usaste como verdad? | Para verificar que el oráculo es correcto |
| ¿Qué afirmación demuestra esta aserción? | Para que no genere aserciones vacías |
| ¿Qué parte no está cubierta? | Para identificar huecos |
| ¿El test observa comportamiento o detalles internos? | Para evitar tests frágiles |
| ¿Puede dar un falso positivo? | Para no confiar ciegamente |
| ¿Puede fallar de manera intermitente? | Para detectar flaky tests |
| ¿Introdujiste una credencial? | Para evitar secretos en tests |
| ¿Este ejemplo es realmente ejecutable? | Para no copiar código que no funciona |

> **Para recordar:** Todo fragmento no ejecutado debe etiquetarse como "ejemplo educativo no verificado". No presentes como funcional algo que no corriste.

---

## 15. Detección y tratamiento de secretos

Un **secreto** es cualquier credencial que no debe exponerse. Si se publica en un repositorio público, debe considerarse comprometido aunque se borre del archivo, porque puede continuar en el historial, clones, cachés o registros externos.

### Dónde se esconden los secretos

| Ubicación | Ejemplo |
|:----------|:--------|
| Código fuente | `const API_KEY = "sk-abc123..."` |
| Archivos `.env` | `DB_PASSWORD=mi contraseña` |
| Configuraciones | `jwt_secret: "secreto123"` en YAML |
| Scripts | Credenciales en scripts de deploy |
| Tests y fixtures | Tokens hardcodeados en datos de prueba |
| Docker Compose | Variables de entorno con valores reales |
| Documentación Markdown | Cadenas de conexión en README |
| Issues y PR | Credenciales pegadas en描述s |
| Logs | Mensajes que imprimen tokens |
| Capturas | Screenshots que muestran credenciales |
| Dumps | Backups con datos reales |
| Historial de Git | Secretos en commits anteriores |

### Tipos de secretos

- API keys
- Tokens de acceso
- JWT secrets
- Contraseñas
- Cadenas de conexión con credenciales
- Claves privadas
- Credenciales SMTP
- Webhooks privados
- Cookies o tokens de sesión

### Prevención

| Medida | Cómo |
|:-------|:-----|
| Variables de entorno | `process.env.API_KEY` nunca en código |
| `.gitignore` | Excluir `.env`, credenciales, dumps |
| `.env.example` | Sin valores reales, solo la estructura |
| GitHub Actions Secrets | Para CI/CD, nunca versionados |
| Separación por ambiente | `.env.development`, `.env.test`, `.env.production` |
| Mínimo privilegio | Credenciales con el menor alcance posible |
| Nunca en prompts de IA | No pegar secretos reales en chats de IA |

### Detección determinista

Usar herramientas como **Gitleaks** o **truffleHog**:

```bash
# Escaneo del árbol actual
gitleaks detect --source . --verbose

# Escaneo del historial Git completo
gitleaks detect --source . --log-refs --verbose
```

### Corrección ante un secreto real

1. **Detener** su uso inmediatamente.
2. **Revocarlo** o rotarlo (generar uno nuevo).
3. **Sustituirlo** por una referencia segura (variable de entorno).
4. **Corregir** `.gitignore` y ejemplos.
5. **Verificar** nuevamente con Gitleaks.
6. **Registrar** evidencia redactada (sin el valor real).
7. **Evaluar** el historial Git.

> **Importante:** Borrar el texto del último commit no invalida el secreto expuesto. Rotar es prioritario. Reescribir historial es excepcional y requiere autorización explícita. Nunca publicar el secreto dentro de un Issue.

### Para credenciales sintéticas E2E

- Deben pertenecer exclusivamente al ambiente de pruebas.
- No deben otorgar acceso a sistemas reales.
- Preferir variables `E2E_*`.
- Proveer `.env.e2e.example` sin valores sensibles.
- En CI, usar secretos del entorno, no valores versionados.

---

## 16. Diferencia entre simulación educativa y producción

Este módulo se ejecuta en sistemas educativos. Las prácticas son las mismas que en producción, pero el contexto es diferente.

| Aspecto | Simulación educativa | Producción real |
|:--------|:---------------------|:----------------|
| **Datos** | Sintéticos, controlados | Reales, sensibles |
| **Usuarios** | Ficticios (`example.test`) | Personas reales |
| **Ambiente** | Local o de pruebas | Servidor público |
| **Consecuencia de error** | Aprendizaje | Daño a personas o negocio |
| **Disponibilidad** | Cuando el estudiante quiere | 24/7 |
| **Seguridad** | Importante para aprender | Crítica, legalmente obligatoria |

Se pueden enseñar prácticas de producción (seguridad, testing, trazabilidad, CI, datos sintéticos), pero siempre diferenciando estos tres niveles.

---

## 17. Preguntas de reflexión y defensa

Prepará respuestas a estas preguntas. No son para memorizar, sino para pensar.

### Sobre el módulo

1. ¿Por qué un E2E no puede validar que se respete un ADR de arquitectura hexagonal?
2. ¿Qué es un test oracle y por qué es indispensable?
3. ¿Qué diferencia hay entre un fixture y un seed?
4. ¿Por qué un test exitoso no significa que el sistema cumple el requisito?
5. ¿Cuándo es legítimo usar `data-testid` como selector?

### Sobre la trazabilidad

6. ¿Qué pasa si tu SPEC dice una cosa y tu código hace otra?
7. ¿Cuál es el oráculo primario en un test de aceptación?
8. ¿Cómo decidís qué flujo seleccionar como crítico?

### Sobre los datos sintéticos

9. ¿Por qué no podés usar personas reales en tus tests?
10. ¿Qué es la idempotencia y por qué importa en los fixtures?
11. ¿Qué protección técnica debés implementar para evitar ejecutar tests contra producción?

### Sobre UI, UX y QA

12. Definí UI, UX y QA con tus palabras. Dá un ejemplo de cada una.
13. ¿Por qué la UX no puede automatizarse completamente?
14. ¿Qué tipo de screenshot debés tomar y cuándo?

### Sobre IA y secretos

15. ¿Qué preguntas le harías a la IA antes de aceptar un test que generó?
16. ¿Por qué un secreto en un commit público debe considerarse comprometido aunque lo borres?
17. ¿Cuál es el primer paso ante un secreto expuesto: borrar el commit o rotar la credencial?

---

## Fuentes

### Playwright Docs
https://playwright.dev/docs/intro
Documentación oficial de Playwright: instalación, selectores, assertions, fixtures, trace.

### Martin Fowler — "Test Driven Development"
https://martinfowler.com/bliki/TestDrivenDevelopment.html
Referencia clásica sobre TDD y pirámide de testing.

### OWASP — Secrets Management
https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html
Guía de OWASP sobre gestión segura de secretos.

### Gitleaks
https://github.com/gitleaks/gitleaks
Herramienta de escaneo de secretos en repositorios Git.

### WCAG 2.1
https://www.w3.org/TR/WCAG21/
Guías de accesibilidad web. Nivel AA como estándar mínimo.

---

## Para practicar

1. **Construí una matriz de trazabilidad** para un flujo de tu proyecto con al menos 4 requisitos.
2. **Escribí un test E2E con Playwright** que verifique el happy path de un formulario de registro.
3. **Agregá un escenario de error** al mismo test: ¿qué pasa si el email ya existe?
4. **Prepará datos sintéticos** para 3 roles diferentes y documentá por qué son necesarios.
5. **Ejecutá Gitleaks** en tu repositorio y documentá los hallazgos (redactados).
6. **Hacé una inspección humana** de tu UI: capturá 2 screenshots y escribí qué mejorarías de UX.
7. **Prepará 5 preguntas** para tu defensa oral basándote en las preguntas de reflexión.
