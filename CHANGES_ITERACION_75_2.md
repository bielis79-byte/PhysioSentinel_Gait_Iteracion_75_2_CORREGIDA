# PhysioSentinel Gait · Iteración 75.2

Base: V75.1, que a su vez deriva de la nueva V74 construida desde V73.

## Corrección principal
- Se corrige la desaparición de las curvas COM, velocidad ML, COM/BOS, tronco y retropié cuando el usuario dejaba `Sentido de la toma frontal/posterior = No especificada`.
- V75.1 convertía esas series a NaN para evitar una interpretación anatómica errónea del signo. Esto también anulaba indebidamente magnitudes que no dependen del sentido de cámara y dejaba las gráficas vacías.

## Nuevo comportamiento
- Las series geométricas originales se conservan siempre.
- Si el sentido es Frontal o Posterior, se aplica la convención anatómica V75:
  - + derecha del paciente / - izquierda para tronco y COM;
  - + eversión / - inversión para retropié.
- Si el sentido queda `No especificada`, las curvas siguen mostrándose, pero sus leyendas cambian explícitamente a `derecha imagen + / izquierda imagen -` o `signo geométrico de imagen`.
- En ese caso se añade un aviso: las magnitudes son utilizables, pero el signo no debe interpretarse anatómicamente.
- Se recuperan por tanto excursión COM, velocidad ML absoluta/P95, COM/BOS absoluto y métricas robustas del retropié cuando el sentido no está declarado.
- El selector aclara ahora:
  - Frontal (paciente hacia la cámara)
  - Posterior (paciente se aleja de la cámara)

## Sin cambios
- No cambia la geometría Heel→BigToe ni la convención clínica toe-out+/toe-in−.
- No se recupera la antigua V74 de máscara global de marcha rectilínea.
- No se modifican las fórmulas biomecánicas de base.
