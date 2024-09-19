<h1>Integração Cisco PPPoE com Zabbix</h1>

<p align="center">
  <img src="https://img.shields.io/static/v1?label=Python&message=3.8&color=blue&style=for-the-badge&logo=python"/>
  <img src="https://img.shields.io/static/v1?label=Linux&message=Server&color=blue&style=for-the-badge&logo=linux"/>
</p>

> Status do Projeto: :heavy_check_mark: Concluído

### Tópicos 

:small_blue_diamond: [Descrição](#descrição)

:small_blue_diamond: [Funcionalidades](#funcionalidades)

:small_blue_diamond: [Deploy da Aplicação](#deploy-da-aplicação-dash)

:small_blue_diamond: [Como Rodar o monitoramento](#como-rodar-o-monitoramento-arrow_forward)

## Descrição 

<p align="justify">
  Este repositório contém scripts para integração do Zabbix com dispositivos Cisco para monitoramento de interfaces PPPoE. Os scripts são projetados para:

- **Descobrir** interfaces PPPoE nos dispositivos Cisco.
- **Contar** o número de conexões PPPoE em cada interface.
</p>

## Funcionalidades

:heavy_check_mark: Descoberta de interfaces PPPoE

:heavy_check_mark: Contagem de conexões PPPoE por interface

:heavy_check_mark: Compatível com Zabbix e dispositivos Cisco

## Deploy da Aplicação :dash:

Não há um deploy web para esta aplicação. Os scripts são utilizados diretamente em ambientes de monitoramento com Zabbix.

**Modificações realizadas:**

1. **Ajuste no script `discovery_interfaces_pppoe`:** Corrigidos problemas relacionados a MIBs e adição de lógica para garantir a descoberta correta das interfaces PPPoE.
 
scripts originais foram desenvolvidos por Fernando Almondes da Bee Solutions. Para mais informações e suporte, você pode entrar em contato com ele através do [Telegram](https://t.me/beesolutions).
## Como Rodar o monitoramento :arrow_forward:

No terminal, clone o projeto:

```bash
git clone https://github.com/erickbenezar218/cisco-pppoe-zabbix.git
```
Mova os scripts para o diretório de scripts do Zabbix:
```bash
mv discovery_interfaces_pppoe /usr/lib/zabbix/externalscripts/
mv ciscocontador /usr/lib/zabbix/externalscripts/
mv discovery_interfaces_pppoe_exe /usr/lib/zabbix/externalscripts/
```
Dê permissão de execução para os scripts:
```bash
chmod +x /usr/lib/zabbix/externalscripts/discovery_interfaces_pppoe
chmod +x /usr/lib/zabbix/externalscripts/ciscocontador
chmod +x /usr/lib/zabbix/externalscripts/discovery_interfaces_pppoe_exe
```
Configure as macros no Zabbix:
```bash
{$PORTA}: Porta SSH
{$SENHA}: Senha SSH
{$USUARIO}: Usuário SSH
{$SNMP_COMMUNITY}: Comunidade SNMP
```
