# Unidad 4: Arquitectura Web ÔÇö Renderizado Distribuido, APIs y Datos

---

## 1. Introducci├│n
La web moderna es un sistema distribuido donde la pregunta "┬┐d├│nde se arma la pantalla?" define rendimiento, SEO, costos de infraestructura y experiencia. Esta unidad recorre el modelo cliente-servidor, las estrategias de renderizado (CSR/SSR/SSG/ISR), el dise├▒o de APIs REST documentadas como contrato, y el stack de referencia React/Next.js + FastAPI/NestJS sobre PostgreSQL.

---

## 2. Conceptos Clave
* **Modelo Cliente-Servidor:** El cliente (navegador) solicita; el servidor procesa y resuelve recursos bajo el protocolo HTTP sin estado.
* **CSR (Client-Side Rendering):** El navegador descarga un esqueleto JS y arma la interfaz en el dispositivo del usuario.
* **SSR (Server-Side Rendering):** El servidor genera el HTML completo de cada petici├│n y lo env├¡a listo para pintar.
* **SSG / ISR:** Generaci├│n est├ítica anticipada (build) o re-validada peri├│dicamente: velocidad de est├ítico con frescura controlada.
* **React / Next.js:** Biblioteca de UI por componentes y framework con h├¡bridos de renderizado, rutas y optimizaciones integradas.
* **REST y GraphQL:** Estilos de exposici├│n de datos: recursos + verbos HTTP con contratos OpenAPI, o consulta declarativa con esquema tipado.
* **FastAPI / NestJS:** Frameworks backend (Python/TypeScript) con validaci├│n, inyecci├│n de dependencias y documentaci├│n autom├ítica.
* **PostgreSQL:** Base relacional transaccional, est├índar de facto para dominios con integridad fuerte.

---

## 3. Analog├¡a Pedag├│gica Cotidiana
* **El restaurante explica los tres renderizados:** CSR es comprar comida congelada y hornearla en tu casa: viaja liviana pero tu horno trabaja al final. SSR es comer en el sal├│n: el chef arma el plato completo y te lo sirve listo, aunque cada pedido carga al personal del local. SSG es el buffet preparado a media ma├▒ana: sale instant├íneo, pero lo que no se agot├│ se regenera cada tanto.
* **Una API REST bien dise├▒ada es la carta del restaurante con precios y descripciones exactas:** sab├®s qu├® pod├®s pedir, c├│mo y qu├® vas a recibir antes de hacerlo.

---

## 4. Ejemplo Pr├íctico
**Consigna:** API de turnos m├®dicos consumida por un frontend Next.js.
1. **Contrato primero (`SPEC.md`):** recursos `/turnos`, `/turnos/{id}`, verbos, c├│digos HTTP (`201` creaci├│n, `409` turno ocupado), paginaci├│n `?page=&size=`, y errores con cuerpo uniforme `{"code", "message", "details"}`.
2. **Implementaci├│n FastAPI:** routers por recurso, Pydantic para validaci├│n de entrada/salida, y documentaci├│n OpenAPI/Swagger autogenerada en `/docs` que funciona como contrato verificable.
3. **Consumo Next.js:** server components para listados (SSR + cach├®), client components solo donde hay interacci├│n; manejo de estados de carga y error seg├║n Unidad 3.
4. **Persistencia PostgreSQL:** tablas normalizadas, constraint de unicidad `(medico_id, fecha_hora)` para que la "doble reserva" sea imposible a nivel base y no solo a nivel c├│digo.

---

**Diagrama ilustrativo — SSR/CSR y contrato de API:**

```mermaid
sequenceDiagram
    actor U as Usuario
    participant N as Next.js Servidor
    participant A as API FastAPI
    Note over U,N: SSR primera carga
    U->>N: GET /
    N->>A: GET /turnos
    A-->>N: JSON
    N-->>U: HTML listo SSR
    Note over U,A: CSR interaccion posterior
    U->>N: navega a nuevo turno
    N-->>U: bundle JS CSR
    U->>A: POST /turnos
    A-->>U: 201 Created
```

---

## 5. Tabla Comparativa: CSR vs SSR vs SSG

| Eje | CSR | SSR | SSG |
| :--- | :--- | :--- | :--- |
| **┬┐D├│nde se arma la p├ígina?** | Navegador del usuario | Servidor en cada request | Servidor en tiempo de build |
| **TTFB / primer render** | Lento inicial | R├ípido | Instant├íneo |
| **SEO** | Requiere hidrataci├│n cuidadosa | Excelente | Excelente |
| **Carga del servidor** | Baja | Alta (por request) | Casi nula |
| **Datos en vivo** | Ideal (llama APIs desde el cliente) | Frecuentes y personalizadas | Contenido que cambia poco (+ISR) |
| **Casos t├¡picos** | Dashboards tras login | E-commerce, portales p├║blicos | Landing, docs, blogs |

---

## 6. Fuentes y Marcos de Referencia (Tabla Unificada)
* **[MDN Web Docs]** Referencia can├│nica de HTTP, CORS, fetch y rendering web: [developer.mozilla.org](https://developer.mozilla.org/)
* **[Next.js Documentation]** Estrategias de renderizado y arquitectura de aplicaci├│n: [nextjs.org/docs](https://nextjs.org/docs)
* **[REST API Design Rulebook]** Mark Masse ÔÇö convenciones de recursos, verbos y c├│digos HTTP: O'Reilly Media.
* **[FastAPI]** Gu├¡a oficial con validaci├│n Pydantic y OpenAPI integrado: [fastapi.tiangolo.com](https://fastapi.tiangolo.com/)
* **[OpenAPI Specification]** Contrato legible por m├íquinas para APIs: [spec.openapis.org](https://spec.openapis.org/)

---

## 7. Para Practicar (con R├║brica de Auditor├¡a)
1. **Ejercicio 1 ÔÇö Contrato API en SPEC.md:** Defin├¡ en tu `SPEC.md` el contrato JSON completo de un recurso de tu proyecto: campos con tipos, validaciones, c├│digos HTTP de ├®xito/error y ejemplos de request/response. *Se eval├║a:* completitud de c├│digos de error y presencia de Non-Goals ("esta versi├│n no pagina m├ís all├í de 100 registros").
2. **Ejercicio 2 ÔÇö Diagrama de secuencia:** Model├í en Mermaid el flujo cliente ÔåÆ API ÔåÆ base de datos de una operaci├│n cr├¡tica tuya, incluyendo el caso de error.
   ```mermaid
   sequenceDiagram
     participant C as Cliente (Next.js)
     participant A as API (FastAPI)
     participant D as PostgreSQL
     C->>A: POST /turnos {paciente, medico, fecha}
     A->>D: INSERT (constraint unicidad)
     alt hueco disponible
       D-->>A: OK
       A-->>C: 201 Created
     else turno ocupado
       D-->>A: violation unique
       A-->>C: 409 Conflict {code:"TURNO_OCUPADO"}
     end
   ```
