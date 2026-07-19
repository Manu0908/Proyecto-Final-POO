# Pipeline de Análisis de Clientes y Compras - Proyecto Final POO

Este proyecto consiste en una aplicación de consola en C# (.NET) diseñada para procesar, limpiar, relacionar y analizar datos transaccionales de comercio electrónico a partir de archivos externos, generando reportes analíticos automatizados.

El desarrollo se fundamenta en los principios de la Programación Orientada a Objetos (POO) y la aplicación de patrones de diseño de software.

---

## Stack Tecnológico

*   **Lenguaje**: C# (.NET 8.0 o superior)
*   **Paradigma**: Programación Orientada a Objetos (Herencia, Polimorfismo, Encapsulamiento, Abstracción)
*   **Pruebas Unitarias**: xUnit
*   **Control de Versiones**: Git y GitHub

---

## Estructura del Proyecto

```text
Proyecto Final POO/
│
├── Docs/                            # Documentación técnica del proyecto
│   ├── 1_ciclo_y_git.md            # Ciclo de vida y tutorial de Git/GitHub
│   ├── 2_convenciones_csharp.md    # Convenciones de nomenclatura y estilo C#
│   ├── 3_arquitectura_y_patrones.md # Diseño de clases y patrones (Strategy/Factory)
│   └── 4_requerimientos_y_fases.md # Requisitos del PDF y planes futuros (DTO/Serialización)
│
├── Program.cs                       # Punto de entrada de la aplicación
├── Proyecto Final POO C#.csproj    # Configuración del proyecto de .NET
└── Proyecto Final POO C#.slnx      # Solución del proyecto
```

---

## Características y Reglas de Negocio

El pipeline realiza de forma automática las siguientes fases:

1.  **Lectura Multiformato**: Carga archivos independientes de clientes y compras en formato CSV o JSON.
2.  **Limpieza de Datos**: Tolera inconsistencias, campos nulos y elimina registros duplicados.
3.  **Relación de Entidades**: Une compras con clientes a través del correo electrónico. Los pedidos cuyos clientes no existen se catalogan y aíslan de forma segura como pedidos huérfanos.
4.  **Cálculo de Impuestos**:
    *   Pedidos Nacionales: Incremento del 19% de IVA.
    *   Pedidos Internacionales: Incremento del 30% de impuesto de aduana.
5.  **Clasificación de Clientes Frecuentes**:
    *   Naturales: Más de 5 compras en el historial.
    *   Empresariales: Compras acumuladas mayores a $50,000,000 COP.
6.  **Reportes Finales**: Exporta el análisis a elección del usuario en formato JSON o XML.

---

## Patrones de Diseño Utilizados

### 1. Patrón Strategy (Estrategia)
Se utiliza para desacoplar las operaciones de entrada/salida de la lógica del pipeline.
*   **Lectura (IImportarDatos)**: Estrategias para procesar archivos CSV y JSON.
*   **Escritura (IExporterReporte)**: Estrategias para generar reportes analíticos en JSON y XML.

### 2. Patrón Factory (Fábrica)
Se utiliza para delegar la creación de las estrategias correctas en tiempo de ejecución de acuerdo a los formatos seleccionados por el usuario.
*   `LectorFactory`
*   `ExportadorFactory`

---

## Ejecución y Pruebas

### Ejecutar la Aplicación:
Para iniciar el pipeline e interactuar por consola, ejecuta en la terminal del proyecto:
```bash
dotnet run
```

### Ejecutar las Pruebas Unitarias:
Para correr el conjunto de pruebas unitarias xUnit (mínimo 5 pruebas que validan cálculos de negocio, datos corruptos e intercambio de estrategias):
```bash
dotnet test
```

---

## Integrantes y Declaración de IA
Este proyecto es desarrollado de manera colaborativa. De acuerdo con nuestros estándares éticos académicos, declaramos el uso de Inteligencia Artificial para la estructuración de ideas y aclaración de conceptos de software, recayendo las decisiones esenciales y la autoría en los integrantes del grupo.
