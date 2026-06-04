# AGENTS: Guía rápida para agentes de IA

Este archivo resume lo esencial para que un agente de IA sea productivo rápidamente en este repositorio Java + Gradle que usa Serenity BDD.

1) Visión general
- Proyecto: pruebas automatizadas con Serenity + JUnit 5 (Screenplay + WebDriver + REST + Cucumber disponibles).
- ArtifactId / root: `reto-automatizacion-serenity` (ver `settings.gradle`).

2) Puntos clave de construcción e ejecución
- Plugin serenity (en `build.gradle`):

```groovy
id 'net.serenity-bdd.serenity-gradle-plugin' version '4.2.34'
```

- Dependencias principales (ejemplos extraídos de `build.gradle`):

```groovy
testImplementation "net.serenity-bdd:serenity-core:${serenityVersion}"
testImplementation "net.serenity-bdd:serenity-junit5:${serenityVersion}"
testImplementation "net.serenity-bdd:serenity-screenplay-webdriver:${serenityVersion}"
testImplementation 'org.junit.jupiter:junit-jupiter:5.10.2'
```

- Comandos (Windows PowerShell; usar el wrapper incluido `gradlew.bat`):

```powershell
# Limpiar y ejecutar pruebas
.\gradlew.bat clean test

# Ejecutar solo pruebas
.\gradlew.bat test

# Enumerar tareas (útil para localizar tareas de Serenity)
.\gradlew.bat tasks --all
```

3) Salida / Reportes
- Serenity genera reportes en `target/site/serenity` (esta ruta está en `.gitignore`). Abrir el `index.html` dentro de ese directorio tras una ejecución exitosa.

4) Estructura del código y convenciones encontradas
- Código Java estándar en `src/main/java` (ej.: `org.example.Main`).
- Tests y recursos de pruebas deberían situarse en `src/test/java` y `src/test/resources`.
- No hay archivos `.feature` en el árbol actual; si se usan características de Cucumber, colócalas en `src/test/resources/features`.

5) Archivos importantes a revisar
- `build.gradle` — plugins, versiones (`serenityVersion`) y configuración de JUnit (`test { useJUnitPlatform() }`).
- `settings.gradle` — nombre del proyecto.
- `.gitignore` — patrones específicos para Serenity: `target/`, `site/`, `screenshots/`, `serenity-reports/`.

6) Patrones de integración detectados
- El proyecto incluye dependencias para Screenplay (WebDriver y REST) y Cucumber. Buscar clases/archivos que usen paquetes `net.serenity-bdd.*`, `io.cucumber.*`, o anotaciones de JUnit 5 para entender cómo se integran.

7) Qué documentar o modificar si amplías el repositorio
- Añadir un README de pruebas con ejemplos mínimos de un test Screenplay y una feature de Cucumber.
- Añadir perfiles/configuración de WebDriver (propiedades o archivo `serenity.conf` / `serenity.properties`) si se van a ejecutar pruebas de navegador.

8) Troubleshooting rápido (lugares donde mirar)
- Errores de compilación: salida de `gradlew.bat test` y stack traces en la consola.
- Fallos en tests E2E: capturas y reportes en `target/site/serenity` y `screenshots/`.
- Dependencias/versión: revisar `serenityVersion` en `build.gradle`.

9) Checklist para un agente que quiera contribuir automáticamente
- [ ] Ejecutar `.\gradlew.bat clean test` y capturar salida.
- [ ] Confirmar existencia/ubicación de tests (buscar clases que extiendan Screenplay or usen `@Test`).
- [ ] Si faltan configuraciones para WebDriver, crear `serenity.properties` o `serenity.conf` bajo `src/test/resources`.
- [ ] Generar un ejemplo mínimo de test y documentarlo en `README.md` o `docs/`.

Referencias: revisar documentación oficial de Serenity Gradle plugin para tareas adicionales (aggregación de reportes, screenshots, etc.).

---
Generado automáticamente: incluye ejemplos extraídos de `build.gradle`, rutas de reportes y convenciones detectadas en `.gitignore`.

