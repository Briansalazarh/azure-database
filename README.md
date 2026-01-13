# azure-database
Documentación para configurar la base de datos SQL en Azure.

# Configurando um Banco de Dados no Azure (SQL Database)

Este repositório documenta o processo de provisionamento de uma instância de Banco de Dados Relacional na nuvem Microsoft Azure.

## Objetivo
Configurar uma instância de **Azure SQL Database** (PaaS), compreendendo as configurações de servidor lógico, firewall e dimensionamento de custos.

## Passo a Passo da Configuração

### 1. Criação do Recurso
* No Portal do Azure, pesquisei por **"SQL Databases"**.
* Cliquei em **Create**.

### 2. Configurações Básicas (Basics)
* **Subscription:** Assinatura Azure.
* **Resource Group:** Selecionei o grupo de recursos existente ou criei um novo chamado `rg-db-lab`.
* **Database Name:** `db-prod-tests`.
* **Server:** Cliquei em *Create new*.
    * *Server name:* `srv-sql-unique-name` (nome único globalmente).
    * *Location:* `East US`.
    * *Authentication:* SQL authentication (Admin: `azureuser`, Senha forte).

### 3. Computação e Armazenamento (Compute + Storage)
* Para fins de laboratório e otimização de custos, cliquei em **Configure Database**.
* Selecionei o modelo **DTU-based** > **Basic** ou a camada **Serverless** para reduzir gastos.
* Cliquei em Apply.

### 4. Networking e Segurança (Networking)
* **Connectivity method:** Public endpoint.
* **Firewall rules:**
    * *Allow Azure services and resources to access this server:* **Yes** (Para permitir conexões de aplicações hospedadas no Azure).
    * *Add current client IP address:* **Yes** (Para permitir a conexão local via SQL Management Studio ou DBeaver).

### 5. Revisão e Deploy
* Avancei para **Review + create**.
* Validei as configurações e iniciei o deploy.

## Conexão
Após o deploy, a string de conexão JDBC pode ser utilizada para integrar com aplicações Java:

```text
jdbc:sqlserver://srv-sql-unique-name.database.windows.net:1433;database=db-prod-tests;user=azureuser@srv-sql-unique-name;password={sua_senha_aqui};encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;

```

# Configuración de una Base de Datos en Azure (SQL Database)

Este repositorio documenta el proceso de aprovisionamiento de una instancia de Base de Datos Relacional en la nube de Microsoft Azure.

## Objetivo
Configurar una instancia de **Azure SQL Database** (PaaS), comprendiendo las configuraciones de servidor lógico, firewall y dimensionamiento de costos.

## Paso a Paso de la Configuración

### 1. Creación del Recurso
* En el Portal de Azure, busqué **"SQL Databases"**.
* Hice clic en **Create**.

### 2. Configuraciones Básicas (Basics)
* **Subscription:** Suscripción de Azure utilizada.
* **Resource Group:** Seleccioné un grupo existente o creé uno nuevo llamado `rg-db-lab`.
* **Database Name:** `db-prod-tests`.
* **Server:** Clic en *Create new*.
    * *Server name:* `srv-sql-unique-name` (debe ser único globalmente).
    * *Location:* `East US`.
    * *Authentication:* SQL authentication (Admin: `azureuser`, contraseña segura).

### 3. Cómputo y Almacenamiento (Compute + Storage)
* Para fines de laboratorio y optimización de costos, hice clic en **Configure Database**.
* Seleccioné el modelo **DTU-based** > **Basic** o la capa **Serverless** para reducir gastos según el uso.
* Hice clic en Apply.

### 4. Networking y Seguridad (Networking)
* **Connectivity method:** Public endpoint.
* **Firewall rules:**
    * *Allow Azure services and resources to access this server:* **Yes** (Para permitir conexiones de aplicaciones hospedadas en Azure).
    * *Add current client IP address:* **Yes** (Para permitir la conexión local desde mi equipo mediante SQL Management Studio o DBeaver).

### 5. Revisión y Despliegue
* Avancé a **Review + create**.
* Validé las configuraciones e inicié el despliegue (deploy).

## Conexión
Una vez finalizado el despliegue, se puede utilizar la cadena de conexión JDBC para integrar la base de datos con aplicaciones Java:

```text
jdbc:sqlserver://srv-sql-unique-name.database.windows.net:1433;database=db-prod-tests;user=azureuser@srv-sql-unique-name;password={tu_contraseña_aquí};encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;
