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

