Packer CSD
==========

## Descripción

Script para generar una máquina virtual VBOX con las herramientas necesarias para el curso Certified Scrum Developer

## Cómo generar la máquina Virtual?

### Paso 1: Instalar herramientas

Packer:

	http://www.packer.io/docs/installation.html

Librarian-puppet:

    $ gem install librarian-puppet

### Paso 2: Descargar módulos externos para el provisionamiento
    $ librarian-puppet install --path provisioning/modules-vendor

### Paso 3: Generar la máquina virtual
	$ packer build ubuntu.json

## Qué contiene?
- JDK
- Jenkins (Puerto 8080), Plugins (Greenballs)
- Apache
- Subversion (Puerto 80)
- RVM, Ruby, Gems (Cucumber,RSpec,Sinatra)
- Desktop Apps (Firefox, Gedit, Rapidsvn)
- Carpeta con ejercicios para el CSD

## Cómo logearse?

Usuario: kleer
Password: kleer

## Development

Ruby 2.+

	https://www.ruby-lang.org/en/

Puppet:

	https://docs.puppetlabs.com/guides/install_puppet/pre_install.html

Verificar la sintaxis de puppet

	$ puppet parser validate provisioning/manifests/init.pp

Mostrar que va a hacer puppet pero sin cambiar nada

	$ puppet apply manifests/init.pp –-noop --modulepath=modules:modules-vendor 

Reprosionar con vagrant luego del primer "vagrant up"

	$ vagrant reload --provision

Verificar el template de packer

	$ packer validate ubuntu.json