# Convenciones de Código y Estilo C# (.NET)

Para garantizar la legibilidad y cohesión del código escrito por los tres integrantes del equipo, se seguirán las convenciones oficiales de Microsoft y las directrices internas definidas para el proyecto.

---

## 1. Convenciones de Nomenclatura

El equipo utilizará los siguientes estándares de nomenclatura para los identificadores en C#:

| Convención | Uso o Destino | Ejemplo |
| :--- | :--- | :--- |
| **PascalCase** | Clases, Estructuras, Interfaces, Métodos, Propiedades Públicas, Constantes, Namespaces | `ClienteEmpresarial`, `CalcularTotal()`, `PrecioUnitario`, `IExportarDatos` |
| **camelCase** | Parámetros de métodos, Variables locales | `rutaArchivo`, `pedidoId`, `comprasRealizadas` |
| **_camelCase** | Atributos privados (campos) de una clase | `_clientes`, `_fecha`, `_exportador` |
| **snake_case** | Columnas o claves en archivos JSON/CSV de entrada | `id_cliente`, `tipo_cliente`, `email_cliente` |

### Reglas Adicionales de Nombre:
1.  **Nombres Significativos y Descriptivos**: Evitar abreviaturas confusas (por ejemplo, usar `decimal totalConImpuesto` en lugar de `decimal tci`).
2.  **Interfaces con "I" Mayúscula**: Toda interfaz debe comenzar con la letra `I` seguida de un nombre en PascalCase (ejemplo: `IExporterReporte`).
3.  **Clases en Singular**: Los nombres de las clases que representan entidades deben estar en singular (usar `Cliente` y `Pedido` en lugar de `Clientes` y `Pedidos`).
4.  **Constantes**: Microsoft recomienda usar `PascalCase` para constantes públicas. En caso de ser privadas, pueden nombrarse con `_camelCase` o `PascalCase`.

---

## 2. Convenciones de Sintaxis y Estilo de Código

### A. Uso de Llaves `{ }` (Estilo Allman)
En C#, las llaves de apertura y cierre siempre deben ir en su propia línea, alineadas con la declaración que abren:
```csharp
// Correcto (Allman Style)
public class Cliente
{
    public void Guardar()
    {
        if (true)
        {
            // Lógica
        }
    }
}
```

### B. Namespaces con Ámbito de Archivo (File-Scoped Namespaces)
Para evitar niveles innecesarios de indentación a lo largo del código, se utilizarán namespaces con ámbito de archivo (disponibles desde C# 10):
```csharp
// Correcto
namespace ProyectoFinal.Modelos;

public class Producto
{
    // ...
}
```

### C. Uso del Tipado Implícito (`var`)
Se recomienda usar `var` cuando el tipo de la variable sea evidente en el lado derecho de la asignación. Esto mantiene el código conciso sin perder claridad:
```csharp
// Correcto
var clientes = new List<Cliente>(); // Evidente
var lector = LectorFactory.ObtenerLector("json"); // Evidente

// Evitar cuando no es evidente o afecta la legibilidad
decimal total = CalcularTotalPedido(); // Preferir el tipo explícito para mayor claridad
```

### D. Una Clase por Archivo
Cada clase, interfaz o enum debe estar definido en su propio archivo `.cs` cuyo nombre coincida exactamente con el nombre de la entidad (ejemplo: `Cliente.cs`, `IExporterReporte.cs`). No se deben agrupar múltiples clases en un único archivo.

### E. Propiedades Auto-Implementadas vs. Campos Privados
Para encapsular atributos de forma limpia, usar propiedades auto-implementadas cuando no se necesite lógica adicional en el `get` o `set`, y campos privados (`_campo`) solo cuando haya lógica de respaldo o encapsulación interna:
```csharp
// Para atributos públicos simples:
public string Nombre { get; set; }

// Para atributos de lectura exclusiva o lógica especial:
private string _email;
public string Email
{
    get => _email;
    set
    {
        if (ValidarEmail(value))
        {
            _email = value;
        }
    }
}
```
