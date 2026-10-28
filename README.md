<h1 align="center">🧪 Testing de una Agencia de Empleos</h1>

<p align="center">
  Suite de <b>tests unitarios y de integración con JUnit</b> para un sistema de agencia de empleos, con casos diseñados por <b>caja negra y caja blanca</b>.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-20-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 20" />
  <img src="https://img.shields.io/badge/JUnit-4-25A162?style=for-the-badge&logo=junit5&logoColor=white" alt="JUnit 4" />
  <img src="https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white" alt="Maven" />
  <img src="https://img.shields.io/badge/UNMdP-Taller%20de%20Programaci%C3%B3n-1f6f4a?style=for-the-badge" alt="UNMdP Taller de Programación" />
</p>

---

## 📌 Sobre el proyecto

Trabajo final del **Taller de Programación** (Ingeniería Informática, UNMdP). La cátedra entregó un sistema hecho por otro equipo (`lib/LinkeFi_v2.jar`), junto con su Javadoc y su especificación de requisitos (SRS). Es una agencia que vincula **empleadores** con **empleados pretensos** mediante tickets de búsqueda, rondas de encuentros laborales y contrataciones. El objetivo fue **verificarlo**: diseñar los casos de prueba, implementarlos y reportar los defectos encontrados.

## 🔍 Qué se testeó

| Capa | Tests | Qué cubre |
| --- | --- | --- |
| **Modelo de datos** | `ClientePuntajeTest`, `EmpleadoPretensoTest`, `EmpleadorTest`, `ContratacionTest`, `TicketTestEsc1-3` | Constructores, puntajes y comparación de tickets en 3 escenarios |
| **Modelo de negocio** | `AgenciaTest`, `GatillarRondaTest`, `GeneraPostulantesTest`, `matchTest`, `CalculaPremiosCastigoAsignasionesTest`, `CrearTicketEmpleado(r)Test` | Registro y login, rondas de encuentros, generación de postulantes, *match*, premios y castigos |
| **Persistencia** | dentro de `AgenciaTest` | Guardado y lectura del estado en XML (`AgenciaDTO`) |
| **Excepciones** | en todas las capas | Contraseña incorrecta, usuario repetido, límites inválidos y otros casos |

## 🧠 Técnicas aplicadas

- **Caja negra:** clases de equivalencia derivadas del SRS, documentadas en `TpFinal.xlsx`
- **Caja blanca:** grafos de flujo, complejidad ciclomática y caminos independientes, en `Caja Blanca.xlsx` y `Caja Blanca_merged.pdf`
- **Escenarios con fixtures** (`@Before` / `@After`) para aislar el estado del *Singleton* `Agencia`
- **Informe final** con los resultados y los errores detectados: `Informe Taller.pdf`

## 🐞 Defectos encontrados

Los tests detectaron fallas en el sistema entregado, entre ellas:

- `EmpleadoPretenso.calculaComision`
- `Empleador.getRealName`
- Comparaciones de `Ticket`: carga horaria, puesto, remuneración y total
- `Agencia`: registro de empleadores, `setLimitesRenumeracion`, restauración desde `AgenciaDTO` y `gatillarRonda`

El detalle de cada caso está en `Informe Taller.pdf`.

## 📁 Estructura

```
├── Informe Taller.pdf            # informe con resultados y defectos encontrados
├── TpFinal.xlsx                  # diseño de casos de caja negra
├── Caja Blanca.xlsx / .pdf       # análisis de caja blanca
└── TrabajoFinalTaller/
    ├── lib/LinkeFi_v2.jar        # sistema bajo prueba (provisto por la cátedra)
    ├── pom.xml
    └── src/main/java/
        ├── testModeloDatos/      # tests de entidades
        ├── testModeloNegocio/    # tests de la clase Agencia y sus procesos
        └── promo/                # tests de promociones y utilidades
```

## 🚀 Cómo correr los tests

Requisitos: **JDK 20+**. La forma más simple es abrir la carpeta `TrabajoFinalTaller/` como proyecto en **Eclipse** o **IntelliJ**, agregar `lib/LinkeFi_v2.jar` al *build path* y ejecutar los tests con JUnit.

## 👥 Autores

- **Ignacio Cantando Flego** · [GitHub](https://github.com/ignacantando)
- **Gonzalo León** · [GitHub](https://github.com/GonzaloLeon01)
- **Pedro Arias**
