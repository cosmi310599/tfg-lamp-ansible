# Instalación de un servidor LAMP con ANSIBLE en una máquina virtual.

<p align="center">
  <img src="https://prezigram-assets.prezi.com/25f8f05f9bc162b1314d168cc6ba516c88b5b96b775380369cd7f61a70dbc55a122936abe711b0d796ba1b7c672ebc50e8faafe8fa44b90014f2829ed5d9886f" alt="ansible" width="650"/>
</p>

Se va a realizar la implementación y configuración de una Raspberry pi 3 en la que contendrá el software de Ansible para administrar los distintos nodos posibles que tendremos a nuestra disposición.


Software necesario para que funcione la implementación del servidor LAMP.

Como el servidor de ansible esta implementado en una Raspberry Pi vamos a hacer uso de las imagenes oficiales de la página de Raspberry [https://www.raspberrypi.org/downloads/]

```
Ubuntu Server 20.04 LTS 
```
Y en la máquina cliente necesitaremos una distribución Debian (o Ubuntu).

```
Debian 9.12
```
## Pasos para la instalación de ansible en una distribución Linux Ubuntu.

```
apt-get install software-properties-common
```
```
apt-add-repository ppa:ansible/ansible
```
```
apt get update
```
```
apt-get install ansible
```
## Pasos para dejar configurado el nodo.
Instalamos ```openssh-server``` y editamos el siguiente fichero: ```/etc/ssh/sshd_config``` , descomentamos la línea 
de ```PermitRootLogin``` y añadimos ```Yes``` a continuación.
Reiniciamos el servicio haciendo un ```/etc/init.d/ssh restart``` o ```systemctl restart ssh```.

## Importante 
Aunque en este proyecto se realice todo con el usuario ```root``` es aconsejable realizar todas las operaciones posibles con un usuario que tenga el nivel de privilegios mas bajo por cuestión de seguridad y escalada de privilegios.


## Pasos para reaizar la conexión.
Nos vamos al controlador donde tenemos Ansible instalado y ejecutamos el siguiente comando:
```ssh-copy-id usuario@ip_nodo_a_controlar```

## Pasos para lanzar el playbook
El primer paso es comprobar que la conexión SSH se ha configurado correctamente lanzando el siguiente comando:

```ansible -m ping lamp```

Si devuelve el siguiente mensaje podemos continuar: ```"ping":"pong"```

Nos situamos dentro de la carpeta ```tfg-lammp-ansible```  y ejecutamos el playbook de la siguiente fomra:
```ansible-playbook playbook.yml --ask-vault-pass``` ya que tenemos una de las variabes cifrada y requiere contraseña para poder ser ejecutado.
Introducimos la contraseña que en este caso es ```root``` y comenzará la ejecución del playbook.

Link presentación: https://prezi.com/i/vmrbdcbcosw5/tfg/
-------------------------------------------------------------------------------------------------------------------------
# Installing a LAMP sever with Ansible in a virtual machine.

The implementation and configuration of a raspberry pi 3 will be carried out that will contain the ansible software to manage the different possible nodes that we will have at our disposal.

Software required for the LAMP server implementation to work.

As the ansible server is implemented in a Raspberry Pi we are going to make use of the official images of the Raspberry page [https://www.raspberrypi.org/downloads/]

```
Ubuntu Server 20.04 LTS
```
And on the client machine we will need a Debian (or Ubuntu) distribution.

```
Debian 9.12
```
## Steps for installing ansible on a Linux Ubuntu distribution.

```
apt-get install software-properties-common
```
```
apt-add-repository ppa: ansible / ansible
```
```
apt get update
```
```
apt-get install ansible
```
## Steps to leave the node configured.
We install ```openssh-server ``` and edit the following file: ``` / etc / ssh / sshd_config```, uncomment the line
of ``` PermitRootLogin``` and add ``` Yes``` below.
We restart the service by doing a ``` /etc/init.d/ssh restart``` or ``` systemctl restart ssh```.

## Important 
Although in this project everything is done with the ```root``` user, it is advisable to carry out all possible operations with a user who has the lowest level of privileges for reasons of security and privilege escalation.

## Steps to make the connection.
We go to the controller where we have Ansible installed and execute the following command:
```ssh-copy-id user@ip_node_to_control```

## Steps to launch the playbook
The first step is to check that the SSH connection has been configured correctly by issuing the following command:

```ansible -m ping lamp```

If it returns the following message we can continue: ```" ping ":" pong "```
We place ourselves in the folder ```tfg-lammp-ansible``` and run the playbook as follows:
```ansible-playbook playbook.yml --ask-vault-pass``` since we have one of the variables encrypted and requires a password to be able to be executed.
We enter the password which in this case is ```root ``` and the playbook will start to run.

  
