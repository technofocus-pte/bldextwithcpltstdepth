# Laboratorio 02 - Configurar Dynamics 365 Customer Service

## Objetivo

En este laboratorio se creará un grupo de seguridad en Azure para
actualizar la configuración en Copilot Studio y posteriormente activar
la versión de **prueba de Dynamics 365 Customer Service.**

## Tarea 1: Crear un grupo de seguridad en Entra ID y configurar autores en Copilot Studio

1.  Navegar a +++<https://portal.azure.com/+++> (Azure portal) e iniciar
    sesión con las credenciales de acceso.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  Seleccione **Next** en la ventana **Keep your account secure** y
    siga las indicaciones.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Descargue la aplicación **Authenticator** en el teléfono si aún no
    está instalada.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  Siga las indicaciones y complete la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  En la pantalla de bienvenida de Azure, seleccione **Get Started**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  Busque y seleccione +++Microsoft EntraID+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  Desde el panel izquierdo, seleccione **Manage** -\> **Groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  Seleccione **New group** para crear un nuevo grupo de seguridad.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  Ingrese los siguientes detalles:

- **Group type** – Seleccione **Security**

- **Group name** – Ingrese **+++copilotagentsecurity+++**

- **Microsoft Entra roles can be assigned to the group** – Seleccione
  **Yes**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. Seleccione **No owners selected**, busque y seleccione **MOD
    Administrator** en la página **Add owners** y haga clic en
    **Select**.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. De manera similar, seleccione **No members selected**, agregue **MOD
    Administrator** de la lista y haga clic en **Select.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. Seleccione **No roles selected**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. Busque y seleccione **+++Global admin+++** y haga clic en
    **Select.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. Seleccione **Create** una vez que se hayan ingresado todos los
    detalles y haga clic en **Yes** en el cuadro de diálogo de
    confirmación.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. Asegúrese de recibir un **mensaje de éxito.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. Seleccione Contoso|Grupos en la parte superior izquierda.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im2.png)

18. Seleccione Propiedades en Administrar desde el panel izquierdo.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im3.png)

19. Activa Sí en la opción **can manage access to all Azure subscriptions and management groups in this tenant** y luego haz clic en **Save**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im4.png)

20. Ahora, selecciona "Roles and administrators" en "Manage" desde el panel izquierdo.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im5.png)

21. Busca +++privileged role admin+++ y haz clic en el rol **Privileged Role Administrator** (no selecciones la casilla; haz clic en su nombre).

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im6.png)

22. Selecciona **+ Add assignments**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im7.png)

23. Selecciona **No members selected**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im8.png)

24. Selecciona **MOD Admin id** y luego selecciona **Next**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im9.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im10.png)

25. Selecciona **Assign**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im11.png)

26. Asegúrate de que la asignación del rol se haya realizado correctamente.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/im12.png)

16. Desde una nueva pestaña, navegue a
    **+++https://powerplatform.microsoft.com+++.** Seleccione **Manage**
    en el panel izquierdo y luego seleccione la opción **Tenant
    Settings**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. Seleccione **Copilot Studio Authors** de la lista disponible.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. Haga clic en el ícono **Edit** para modificar la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. Busque y seleccione el grupo **copilotagentsecurity** que creó
    anteriormente.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. Seleccione **Save** para guardar la configuración.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

## Tarea 2: Regístrese para la versión de prueba de Dynamics 365 Customer Service

1.  Inicie sesión en
    +++<https://dynamics.microsoft.com/en-us/customer-service/overview/+++>

2.  Inicie sesión utilizando los **detalles del Tenant de Office 365**
    desde la pestaña **Home,** si se solicita.

3.  Haga clic en **Try for free.**

![](./media/image28.png)

4.  Ingrese su **Office 365 Administrative Username** desde la pestaña
    **Resources**, seleccione la casilla de verificación y haga clic en
    **Start your free trial**.

![](./media/image29.png)

5.  Ingrese la región como **United States**, ingrese su número de
    teléfono y haga clic en **Submit.**

![](./media/image30.png)

6.  Si aparece la opción **Launch Trial for Engage customers**, haga
    clic en **Launch Trial**.

![](./media/image31.png)

7.  Una vez activado, se abrirá su espacio de trabajo de **Customer
    Service**.

![](./media/image32.png)

## Resumen

En este laboratorio, se ha activado **Dynamics 365 Customer Service**,
el cual se utilizará en el **Laboratorio 04 - Integrar un agente con la
aplicación Dynamics 365 Customer Service e implementar la escalación
automática de casos al agente en vivo**.

