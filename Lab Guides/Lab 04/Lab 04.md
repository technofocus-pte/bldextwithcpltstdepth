# Laboratorio 4: Creación de un agente de contratación inteligente para la adquisición de talento

En este laboratorio, establecerá las bases de su sistema de
automatización de contrataciones. Comenzará importando una solución
preconfigurada que contiene todas las tablas de Dataverse y la
estructura de datos necesaria para gestionar candidatos, puestos de
trabajo y flujos de trabajo de contratación. A continuación, poblará
estas tablas con datos de muestra que respaldarán su aprendizaje a lo
largo de este módulo y proporcionarán escenarios realistas para las
pruebas. Finalmente, creará el agente de contratación en Copilot Studio,
configurando la interfaz conversacional básica que servirá como piedra
angular para todas las demás funciones que añadirá en futuras misiones.

## Ejercicio 1: Importar solución

En este ejercicio, importará una solución preexistente.

1.  Diríjase a Copilot Studio en
    +++https://copilotstudio.microsoft.com+++

2.  Seleccione los **...** (tres puntos) en la navegación izquierda y
    seleccione **Solutions.**

![](./media/image1.png)

3.  Seleccione **Import solution**. Haga clic en **Browse**, seleccione
    el archivo **zip** que comienza con "Operative" desde C:\LabFiles y
    elija **Open**.

![](./media/image2.png)

![](./media/image3.png)

![](./media/image4.png)

4.  Una vez seleccionado, seleccione **Next** y luego seleccione
    **Import**.

![](./media/image5.png)

![](./media/image6.png)

5.  Esto tomará entre 3 y 5 minutos. Si tiene éxito, verá una barra de
    notificación verde con el siguiente mensaje cuando termine:
    "Solution "Operative" imported successfully."

![](./media/image7.png)

6.  Una vez que vea el mensaje "imported successfully", eche un vistazo
    a lo que ha importado seleccionando el nombre para mostrar de la
    solución (**Operative**) en la lista de soluciones.

![](./media/image8.png)

7.  Revise la solución y asegúrese de que se hayan importado los
    siguientes componentes.

![](./media/image9.png)

8.  Seleccione el botón Publish all customizations en la parte superior
    de la página.

![](./media/image10.png)

## Ejercicio 2: Importar datos de muestra

En este ejercicio, añadirá datos de muestra a algunas de las tablas que
importó en el ejercicio anterior.

1.  Desde la solución que importó en el último ejercicio, seleccione la
    aplicación **Hiring Hub Model-Driven App** marcando la casilla
    frente a la fila y seleccione el botón **Play** en la parte
    superior.

> ![](./media/image11.png)

2.  Seleccione **Job Roles** en la navegación izquierda. Seleccione el
    icono **More** (tres puntos uno debajo del otro) en la barra de
    comandos y luego seleccione la flecha a la derecha junto a **Import
    from Excel.**

![](./media/image12.png)

3.  Seleccione **Import from CSV**.

![](./media/image13.png)

4.  Seleccione el botón **Choose File**, seleccione el archivo
    **job-roles.csv** desde **C:\LabFiles** y luego seleccione **Open**.

![](./media/image14.png)

5.  Seleccione **Next.** Deje el siguiente paso como está y seleccione
    **Review Mapping**

![](./media/image15.png)

![](./media/image16.png)

6.  Asegúrese de que el mapeo sea correcto y seleccione **Finish
    Import**.

![](./media/image17.png)

7.  Seleccione **Done**. Esto puede tardar un poco, pero puede pulsar el
    botón **Refresh** para ver si la importación se ha realizado
    correctamente.

![](./media/image18.png)

![](./media/image19.png)

8.  Ahora, importará los datos de muestra de **Evaluation Criteria.**

9.  Seleccione **Evaluation Criteria** en la navegación izquierda.

10. Seleccione **Import from CSV** como hizo anteriormente. Seleccione
    el botón **Choose File**, seleccione el
    archivo **evaluation-criteria.csv** desde **C:\LabFiles**.

![](./media/image20.png)

11. Seleccione **Next**. Deje el siguiente paso como está y seleccione
    **Review Mapping**.

![](./media/image21.png)

![](./media/image22.png)

12. Ahora tenemos que trabajar un poco más en el mapeo. Seleccione el
    **icono de la lupa** junto al campo **Job Role**.

![](./media/image23.png)

13. Asegúrese de que **Job Title** esté seleccionado aquí y, si no es
    así, añádalo y seleccione **OK**.

![](./media/image24.png)

14. Asegúrese de que el resto del mapeo también sea correcto y
    seleccione **Finish Import** y luego seleccione **Done**.

![](./media/image25.png)

15. Esto puede tardar un poco, pero puede pulsar el botón **Refresh**
    para ver si la importación se ha realizado correctamente.

![](./media/image26.png)

## Ejercicio 3: Crear el agente de contratación

Ahora que ha terminado con la configuración de los requisitos previos,
¡es hora del trabajo real! ¡añadamos primero nuestro agente de
contratación!

1.  Desde Copilot Studio, seleccione Agents en el panel izquierdo.
    Seleccione el menú desplegable junto a + Create blank agent y
    seleccione Advanced create.

![](./media/image27.png)

2.  En la configuración del agente (Agent settings), seleccione la
    **Solution** como **Operative** y luego seleccione **Confirm and
    create**.

![](./media/image28.png)

3.  Seleccione **Edit** junto a los detalles del agente creado.

![](./media/image29.png)

4.  Ingrese el nombre como +++**Hiring Agent**+++ y la descripción como
    +++**Central orchestrator for all hiring activities**+++ y
    seleccione **Save**.

> ![](./media/image30.png)

## Resumen

> En este laboratorio, usted ha completado lo siguiente:

- **Comprensión del escenario**: Conocimiento integral de los desafíos
  de la automatización de contrataciones y de la solución que va a
  construir.

- **Despliegue de la solución**: Importación y configuración exitosa de
  los bloques de construcción del sistema de gestión de contrataciones.

- **Creación del agente**: Construcción de un agente de contratación que
  es el inicio del escenario que desarrollará como un Agent Academy
  Operative.
