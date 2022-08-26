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
* adicionar linhas com o IP e o gateway

<p><center> Figura 5: Arquivo 01-netcfg.yaml</center></p>
<img src="figures/Netplan3.png" alt=""
     title="Figura 5: Arquivo 01-netcfg.yaml" width="800" height="auto"/></br>
     
* ``sudo netplan apply``

### Configurando Usuários e Hostnames
<p><center> Figura 6: Criando usuários</center></p>

* ``sudo adduser <usuario>``

<img src="figures/criando usuário.png" alt=""
     title="Figura 6: Criando usuários" width="800" height="auto"/></br>
     
* Deve ser realizada a criação de todos os usuários dos integrantes do grupo em todas as VMs (exemplo abaixo de apenas uma VM, mas isso foi realizado em todas)
* comando para verificação de usuários em uma máquina ``getent passwd``

<p><center> Figura 7: Usuários</center></p>
<img src="figures/Captura de tela de 2022-08-12 10-37-22.png" alt=""
     title="Figura 7: Usuários" width="800" height="auto"/></br>
     

<p><center> Figura 8: Alterando hostname</center></p>

* ``sudo hostnamectl set-hostname <hostname>``

<img src="figures/alterando hostnames.png" alt=""
     title="Figura 8: Alterando hostname" width="800" height="auto"/></br>

### Atualizando definições e versões de pacotes/bibliotecas dos repositórios do ubuntu
##### Ligando a internet
* placa de rede em NAT
* editar arquivo ``01-netcfg.yaml``, comentando as alterações que tinham sido feitas no passo anterior
##### Atualizando definições e versões de pacotes/bibliotecas
* ``sudo apt update``
* ``sudo apt upgrade -y``

### Instalando o SSH
* verificar o estado do SSH: ``systemctl status ssh``
* ainda com a internet ligada, executar o comando:
* ``sudo apt-get install openssh-server``

<p><center> Figura 9: Instalando SSH</center></p>
<img src="figures/instalacaoSSH.png" alt=""
     title="Figura 9: Instalando SSH" width="800" height="auto"/></br>

### Configurando Firewall
* ``sudo ufw allow ssh``
<p><center> Figura 10: Configurando Firewall</center></p>
<img src="figures/firewallssh.png" alt=""
     title="Figura 10: Configurando Firewall" width="800" height="auto"/></br>

### Configurando conexões físicas
* colocar a placa de todas as VMs em modo bridge
<p><center> Figura 11: Placa de rede no modo bridge</center></p>
<img src="figures/placa em modo bridge.png" alt=""
     title="Figura 11: Placa de rede no modo bridge" width="800" height="auto"/></br>

### Configurando o acesso remoto à uma VM pelo terminal do PC via ssh
##### Fazer isso em apenas uma VM por PC
* habilitar segundo adaptador de rede, que deve está no modo host-only
* selecionar adaptador de rede
* editar o arquivo 01-netcfg.yaml e adicionar a interface ``enp0s8``
<p><center> Figura 12: Placa de rede no modo Host-Only</center></p>
<img src="figures/placa host-only.png" alt=""
     title="Figura 12: Placa de rede no modo Host-Only" width="800" height="auto"/></br>
     
<p><center> Figura 13: Interface de rede</center></p>
<img src="figures/interface de rede.png" alt=""
     title="Figura 13: Interface de rede" width="800" height="auto"/></br>
     
<p><center> Figura 14: Adicionando enp0s8</center></p>
<img src="figures/netplan 8.png" alt=""
     title="Figura 14: Adicionando enp0s8" width="800" height="auto"/></br>
     
### Acessando VM pelo terminal do PC via SSH
<p><center> Figura 15: Acessando VM pelo terminal do PC via SSH</center></p>
<img src="figures/Captura de tela de 2022-08-10 10-29-09.png" alt=""
     title="Figura 15: Acessando VM pelo terminal do PC via SSH" width="800" height="auto"/></br>
     
### Editando arquivo hosts
* ``sudo nano /etc/hosts``
* adicionar informações da tabela

<p><center> Figura 16: Arquivo hosts editado</center></p>
<img src="figures/telaHosts.png" alt=""
     title="Figura 16: Arquivo hosts editado" width="800" height="auto"/></br>

