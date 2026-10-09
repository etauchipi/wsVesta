# wsVesta - WCF Service

Este repositorio contiene el código fuente de **wsVesta**, un servicio web basado en la tecnología WCF (Windows Communication Foundation) de Microsoft. Este proyecto proporciona una plantilla o estructura inicial para la creación de servicios SOAP y maneja operaciones básicas con contratos de datos (`DataContract`) e interfaces (`ServiceContract`).

## Pila Tecnológica (Tech Stack)

Basado en el análisis del código fuente, el proyecto utiliza las siguientes tecnologías:

*   **Lenguaje:** Visual Basic .NET (VB.NET)
*   **Framework:** .NET Framework 4.5.2
*   **Tecnología de Servicio:** Windows Communication Foundation (WCF)
*   **Entorno de Desarrollo:** Visual Studio 2015 (compatible con versiones más recientes)
*   **Servidor Web (Desarrollo):** IIS Express

## Estructura de Carpetas

A continuación se presenta un resumen de la estructura principal del repositorio:

```text
/ (Raíz)
├── wsVesta.sln                 # Archivo principal de la solución para Visual Studio.
└── wsVesta/                    # Directorio principal del proyecto WCF.
    ├── wsVesta.vbproj          # Archivo de configuración del proyecto de VB.NET.
    ├── wsVesta.vb              # Interfaz del servicio (`wsVesta`) y definición de contratos de datos (`CompositeType`).
    ├── wsVesta.svc             # Punto de entrada (endpoint) del servicio WCF.
    ├── wsVesta.svc.vb          # Implementación (Code-Behind) de las operaciones definidas en la interfaz del servicio.
    ├── Web.config              # Archivo de configuración principal de la aplicación web y WCF (bindings, comportamientos).
    ├── Web.Debug.config        # Transformación de configuración para el entorno de depuración.
    ├── Web.Release.config      # Transformación de configuración para el entorno de producción.
    └── My Project/             # Configuraciones, propiedades y recursos de la aplicación VB.NET.
```

## Instrucciones de Instalación y Configuración Local

Sigue estos pasos para levantar el proyecto localmente en tu máquina:

### 1. Prerrequisitos
*   Tener instalado **Microsoft Visual Studio** (2015 o superior) con la carga de trabajo de **"Desarrollo de ASP.NET y web"** instalada, la cual incluye soporte para WCF y .NET Framework 4.5.2.
*   Tener instalado IIS Express (generalmente se instala de forma predeterminada con Visual Studio).

### 2. Clonar el repositorio
Abre una terminal o consola de comandos y clona el repositorio (si utilizas Git):
```bash
git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_DIRECTORIO>
```

### 3. Abrir la Solución en Visual Studio
*   Abre Visual Studio.
*   Dirígete a `Archivo` -> `Abrir` -> `Proyecto/Solución` y selecciona el archivo **`wsVesta.sln`** ubicado en la raíz del repositorio.

### 4. Restaurar Dependencias y Compilar
*   Una vez abierta la solución, haz clic derecho sobre la solución en el "Explorador de Soluciones" y selecciona **Recompilar Solución** (`Ctrl + Shift + B`).
*   Asegúrate de que no haya errores de compilación. Las dependencias base ya están referenciadas al framework (como `System.ServiceModel`, `System.Runtime.Serialization`, etc.).

### 5. Configuración del Servidor (IIS Express)
El proyecto está configurado para ejecutarse en IIS Express en el puerto `54354`. Si tienes conflictos de puerto, puedes modificarlo en las propiedades del proyecto (`wsVesta.vbproj`) en la pestaña "Web", o directamente en la configuración compartida si aplica.

## Guía Básica de Uso y Ejecución

Para iniciar el servicio y probar su funcionalidad:

1.  **Ejecutar el proyecto:** En Visual Studio, presiona `F5` o haz clic en el botón de **Iniciar Depuración**. Esto levantará IIS Express.
2.  **Cliente de prueba WCF:** Por defecto, al ejecutar un proyecto WCF en modo depuración, Visual Studio abrirá el **Cliente de prueba WCF** (WCF Test Client).
3.  **Probar métodos:** En el cliente de prueba, verás los métodos expuestos por la interfaz `wsVesta`:
    *   `GetData(value: Integer)`: Recibe un número y devuelve una cadena de texto confirmando el número ingresado.
    *   `GetDataUsingDataContract(composite: CompositeType)`: Recibe un objeto con un valor booleano (`BoolValue`) y una cadena (`StringValue`). Si `BoolValue` es verdadero, le concatena "Suffix" a la cadena y devuelve el objeto resultante.

**Acceso desde un navegador o cliente externo (ej. Postman/SoapUI):**
*   Una vez el servicio esté en ejecución, puedes obtener el WSDL (Web Services Description Language) para consumir el servicio accediendo a:
    `http://localhost:54354/wsVesta.svc?wsdl`
