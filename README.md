# -Laboratorios-del-Modulo-IX-
Practica 2 Desplieque de una VM con terraform en digital Ocean(1Pts)
 Comandos para instalar Terraform y desplegar VM en Digital Ocean usando Terraform (en CentOS)

1. sudo dnf install -y dnf-plugins-core  
   - Instala plugins necesarios para manejar repositorios en CentOS.

2. sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo  
   - Añade el repositorio oficial de HashiCorp para instalar Terraform.

3. sudo dnf install terraform -y  
   - Instala Terraform desde el repositorio agregado.

4. terraform -version  
   - Verifica la versión instalada de Terraform para confirmar la instalación.

5. mkdir ~/terraform_do  
   - Crea un directorio llamado terraform_do para organizar archivos Terraform.

6. cd ~/terraform_do  
   - Entra al directorio creado para trabajar con Terraform.

7. terraform init  
   - Inicializa el proyecto Terraform, descarga proveedores y prepara el entorno.

8. terraform plan  
   - Muestra un plan con las acciones que Terraform realizará (recursos a crear, cambiar o eliminar).

9. terraform apply  
   - Aplica el plan y crea o modifica recursos en el proveedor (Digital Ocean en este caso).

10. ssh -i ~/.ssh/id_rsa root@IP_PUBLICA  
    - Conecta vía SSH a la VM creada usando la llave privada especificada y la IP pública de la VM.

11. terraform destroy  
    - Destruye (elimina) los recursos creados por Terraform, útil para limpiar el entorno.

---

# Archivos Terraform principales

- main.tf: Archivo principal que define proveedor, variables y recursos a crear.
- variables.tf: Declara variables usadas en main.tf para facilitar reutilización y seguridad.
- terraform.tfvars: Archivo donde se asignan valores concretos a las variables.

---

# Notas adicionales

- Las variables deben declararse sólo una vez en el módulo (normalmente en variables.tf).
- El token de Digital Ocean y el fingerprint SSH son sensibles, se deben manejar con cuidado.
- El fingerprint SSH se obtiene desde el portal Digital Ocean, en la sección de Security → SSH Keys.
- La IP pública de la VM se puede obtener en la salida de terraform apply o en el portal web de Digital Ocean.
