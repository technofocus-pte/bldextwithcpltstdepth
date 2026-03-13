# Laboratorio 9: Probar, medir y mejorar agentes de IA

A medida que los agentes de IA asumen roles críticos en los procesos
empresariales, se vuelve esencial contar con pruebas confiables y
repetibles. La evaluación de agentes permite generar pruebas que simulan
escenarios del mundo real para su agente. Estas pruebas abarcan más
preguntas de manera más rápida que las pruebas manuales caso por caso.
Luego, puede medir la precisión, relevancia y calidad de las respuestas
a las preguntas realizadas al agente, en función de la información a la
que el agente puede acceder. Al utilizar los resultados del conjunto de
pruebas, puede optimizar el comportamiento del agente y validar que
cumple con los requisitos de negocio y calidad.

**Objetivo**

En este laboratorio, aprenderá a probar y evaluar sistemáticamente un
agente de IA utilizando las capacidades integradas de evaluación y
análisis de Copilot Studio. Creará un conjunto de pruebas automatizado
que simule escenarios de usuario del mundo real, medirá la calidad y
precisión de las respuestas del agente y analizará los datos de
rendimiento para identificar brechas y oportunidades de mejora. Al final
del laboratorio, podrá validar que su agente cumple con los estándares
de negocio, confiabilidad y calidad antes de su uso en producción.

## Tarea 1: Crear un conjunto de pruebas para evaluar su agente

Antes de implementar un agente de IA en flujos de trabajo empresariales
reales, es fundamental validar qué tan bien responde a preguntas
realistas de los usuarios. Las pruebas manuales consumen mucho tiempo y
a menudo omiten casos límite. En esta tarea, utilizará las capacidades
de evaluación de agentes de Copilot Studio para generar automáticamente
un conjunto de pruebas que simule escenarios del mundo real. Ejecute
estas pruebas contra su agente, revise los resultados de aprobación y
falla e identifique las brechas en precisión, relevancia o
comportamiento que requieran mejora.

1.  Desde Copilot Studio, seleccione el **agente Hiring**.

![](./media/image1.png)

2.  En la barra de menú superior, seleccione **Evaluation**. Seleccione
    **Create a test set**.

![](./media/image2.png)

3.  Existen varias opciones para crear el conjunto de pruebas.
    Seleccione **Generate 10 questions** en este caso.

![](./media/image3.png)

4.  Revise el **conjunto de pruebas** y luego guarde el **conjunto de
    pruebas**.

![](./media/image4.png)

5.  Ahora, haga clic en **Evaluate** para evaluar el agente.

![](./media/image5.png)

6.  Seleccione su tenant id y haga clic en **Run**.

![](./media/image6.png)

7.  Espere hasta que la ejecución finalice.

![](./media/image7.png)

8.  Una vez completada la evaluación, haga clic en ella para ver los
    detalles.

![](./media/image8.png)

9.  Revise cada pregunta para identificar por qué ha fallado y cuáles
    han pasado. Esto le ayudará a mejorar su agente según sea necesario.

![](./media/image9.png)

## Tarea 2: Obtener información mediante análisis de agentes

Una vez que un agente ha sido evaluado y se encuentra en uso activo, es
fundamental realizar un monitoreo continuo para garantizar un
rendimiento y confiabilidad consistentes a gran escala. En esta tarea,
explorará las capacidades de Analytics en Copilot Studio para obtener
información sobre el uso del agente, tendencias de ejecución y
utilización de componentes. Aprenderá cómo los datos de análisis ayudan
a identificar cuellos de botella en el rendimiento, comprender patrones
de interacción de los usuarios y orientar la optimización continua de su
agente a lo largo del tiempo.

1.  En la barra de menú superior, seleccione **Analytics**.

> ![](./media/image10.png)

2.  Cuando haya un mayor número de ejecuciones y el agente se use cada
    vez más, el tráfico aumenta y podrá encontrar el **AI Summary** en
    la pestaña **Analytics**.

> ![](./media/image11.png)

3.  La sección **Overview** proporciona una visión general sobre las
    ejecuciones y los créditos.

> ![](./media/image12.png)

4.  La sección **Run outcomes** muestra las tendencias de duración
    promedio.

> ![](./media/image13.png)

5.  Desplácese hacia abajo y, en la sección **Use**, podrá ver el uso de
    **triggers, tools y knowledge sources**.

> ![](./media/image14.png)

6.  Cada uno de estos elementos le permite evaluar el uso de cada
    componente del agente y actualizar, mejorar o corregir las
    funcionalidades del agente según corresponda.

## Resumen

En este laboratorio, implementó la evaluación y el análisis
automatizados para evaluar la calidad y confiabilidad de un agente de
IA. Generó un conjunto de pruebas para simular interacciones realistas
de los usuarios, ejecutó evaluaciones para medir la precisión y
relevancia de las respuestas, y revisó los resultados de
aprobación/falla para identificar áreas de mejora.

También exploró los análisis de agentes para comprender los patrones de
uso, tendencias de ejecución y utilización de componentes en triggers,
tools y knowledge sources. Estas capacidades permiten ir más allá de las
pruebas manuales y adoptar un enfoque escalable y basado en datos para
la validación de agentes. Este laboratorio demuestra cómo las pruebas y
análisis automatizados ayudan a garantizar que sus agentes sean
confiables, eficientes y listos para escenarios empresariales reales.
