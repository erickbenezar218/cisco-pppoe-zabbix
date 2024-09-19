# cisco-pppoe-zabbix
Projeto de Monitoramento de Interfaces PPPoE
Este repositório contém scripts para a descoberta e monitoramento de interfaces PPPoE em dispositivos Cisco. Os scripts são destinados a serem usados com o Zabbix para facilitar o gerenciamento e a monitoração de interfaces PPPoE em tempo real.

Créditos
O projeto foi desenvolvido por Fernando Almondes da Bee Solutions. As modificações e ajustes realizados foram feitos para resolver problemas específicos relacionados às MIBs e melhorar a funcionalidade dos scripts.

Arquivos
ciscocontador: Script para contar o número de interfaces PPPoE em uma subinterface específica do dispositivo Cisco.
discovery_interfaces_pppoe: Script para descobrir interfaces PPPoE no dispositivo Cisco.
discovery_interfaces_pppoe_exe: Script executável que chama o script de descoberta com parâmetros.
Funcionalidade dos Scripts
ciscocontador
Este script conecta-se via SSH a um dispositivo Cisco para contar a quantidade de interfaces PPPoE em uma subinterface específica.

Uso:

bash
Copiar código
./ciscocontador <IP> <USUARIO> <SENHA> <SUBINTERFACE>
Parâmetros:

IP: Endereço IP do dispositivo Cisco.
USUARIO: Nome de usuário para autenticação SSH.
SENHA: Senha para autenticação SSH.
SUBINTERFACE: Nome da subinterface para a qual você deseja contar as interfaces PPPoE.
Comando Executado:

bash
Copiar código
show pppoe summary per subinterface
Saída:

O número de interfaces PPPoE encontradas na subinterface especificada. Retorna 0 se nenhuma interface for encontrada.
discovery_interfaces_pppoe
Script utilizado para descobrir todas as interfaces PPPoE disponíveis em um dispositivo Cisco e formatar os dados para o Zabbix.

discovery_interfaces_pppoe_exe
Script executável que chama o discovery_interfaces_pppoe com os parâmetros apropriados para executar a descoberta das interfaces PPPoE.

Modificações Realizadas
Arquivo Modificado: discovery_interfaces_pppoe

Modificações:

Ajustes na leitura e processamento das MIBs para evitar a leitura de informações desnecessárias e garantir que apenas interfaces relevantes sejam listadas.
Objetivo das Modificações:

Corrigir problemas relacionados à leitura de MIBs que não existem e garantir que o script funcione corretamente com o Zabbix.
Passo a Passo para Instalação
Clonar o Repositório:

bash
Copiar código
git clone <URL_DO_REPOSITORIO>
cd <DIRETORIO_DO_REPOSITORIO>
Instalar Dependências:

Certifique-se de que o sshpass está instalado. Em sistemas baseados em Debian, execute:

bash
Copiar código
sudo apt update
sudo apt install sshpass
Mover Scripts para o Diretório do Zabbix:

bash
Copiar código
sudo mv ciscocontador /usr/lib/zabbix/externalscripts/
sudo mv discovery_interfaces_pppoe /usr/lib/zabbix/externalscripts/
sudo mv discovery_interfaces_pppoe_exe /usr/lib/zabbix/externalscripts/
Configurar Permissões dos Scripts:

bash
Copiar código
sudo chmod +x /usr/lib/zabbix/externalscripts/ciscocontador
sudo chmod +x /usr/lib/zabbix/externalscripts/discovery_interfaces_pppoe
sudo chmod +x /usr/lib/zabbix/externalscripts/discovery_interfaces_pppoe_exe
Adicionar Macros no Host Zabbix:

No Zabbix, adicione as seguintes macros no host onde os scripts serão utilizados:

{$PORTA}: Porta SSH
{$SENHA}: Senha SSH
{$USUARIO}: Usuário SSH
{$SNMP_COMMUNITY}: Comunidade SNMP
Executar o Script de Descoberta:

Execute o script discovery_interfaces_pppoe_exe com os parâmetros apropriados:

bash
Copiar código
./discovery_interfaces_pppoe_exe <IP> <COMMUNITY>
Verificar a Saída:

O script imprimirá um JSON com as interfaces descobertas. Verifique a saída para garantir que os dados estejam corretos e que o Zabbix esteja recebendo as informações corretamente.

Para mais informações e suporte, entre em contato com Fernando Almondes.