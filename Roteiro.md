# Roteiro

* Roteiro da criação de um ambiente de rede, no qual contém 8 máquinas virtuais com o S.O. Ubuntu Server.

### Criação das VMs
* importar arquivo .OVA
* alterar nome da VM
* selecionar pasta de destino
* gerar novos endereços MAC para todas as placas de rede
<p><center> Figura 1: Criação da VM</center></p>
<img src="figures/CriarVM.png" alt=""
     title="Figura 1: Criação da VM" width="800" height="auto"/></br>
     
### Instalação das ferramentas de rede na duas VM
* `` sudo apt install net-tools -y``
* ``ifconfig -a``
<p><center> Figura 2: Instalando net-tools</center></p>
<img src="figures/net-tools.png" alt=""
     title="Figura 2: Instalando net-tools" width="800" height="auto"/></br>
<p><center> Figura 3: ifconfig -a</center></p>
<img src="figures/ifconfig.png" alt=""
     title="Figura 3: ifconfig -a" width="800" height="auto"/></br>

### Configuração das NICs das VMs
* placa de rede no modo rede interna
<p><center> Figura 4: Placa como rede interna</center></p>
<img src="figures/Rede interna.png" alt=""
     title="Figura 4: Placa como rede interna" width="800" height="auto"/></br>
     
* editar arquivo 01-netcfg.yaml
* ``sudo nano /etc/netplan/01-netcfg.yaml``
* adicionar linhas como o IP e o gateway

<p><center> Figura 5: Arquivo 01-netcfg.yaml</center></p>
<img src="figures/Netplan3.png" alt=""
     title="Figura 5: Arquivo 01-netcfg.yaml" width="800" height="auto"/></br>
     
* ``sudo netplan apply``

### Configurando Usuários e Hostnames
<p><center> Figura 6: Criando usuários</center></p>

*``sudo adduser <usuario>``

<img src="figures/criando usuário.png" alt=""
     title="Figura 6: Criando usuários" width="800" height="auto"/></br>
     


<p><center> Figura 7: Alterando hostname</center></p>

*``sudo hostnamectl set-hostname <hostname>``

<img src="figures/alterando hostnames.png" alt=""
     title="Figura 7: Alterando hostname" width="800" height="auto"/></br>

### Atualizando definições e versões de pacotes/bibliotecas dos repositórios do ubuntu
##### Ligando a internet
* placa de rede em NAT
* editar arquivo ``01-netcfg.yaml``, comentando as alterações que tinham sido feitas no passo anterior
##### Atualizando definições e versões de pacotes/bibliotecas
* ``sudo apt update``
* ``sudo apt update -y``

### Instalando o SSH
* verificar o estado do SSH: ``systemctl status ssh``
* ainda com a internet ligada, executar o comando:
* ``sudo apt-get install openssh-server``

<p><center> Figura 8: Instalando SSH</center></p>
<img src="figures/instalacaoSSH.png" alt=""
     title="Figura 8: Instalando SSH" width="800" height="auto"/></br>

### Configurando Firewall
* ``sudo ufw allow ssh``
