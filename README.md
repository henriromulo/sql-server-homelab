# SQL Server Homelab

Laboratório doméstico para acompanhar um curso de SQL Server de 96 horas,
transformando as práticas em um projeto técnico documentado.

## Objetivo

Desenvolver conhecimentos práticos em SQL Server e na infraestrutura
Windows utilizada pelo laboratório.

A documentação registra o que foi executado, as configurações aplicadas
e os resultados validados, separando as atividades concluídas das pendências.

## Visão geral do ambiente

O laboratório utiliza Proxmox VE e duas máquinas virtuais:

| Máquina | Função |
|---|---|
| DCSRV | Controlador de domínio e DNS |
| DBSRV1 | SQL Server 2019 Developer e SSMS |

As duas VMs utilizam Windows Server 2019 Datacenter Evaluation.
Notebook para acesso ao proxmox e acesso as Vm´s.

## Tecnologias

- Proxmox VE.
- Windows Server 2019.
- Active Directory Domain Services e DNS.
- SQL Server 2019 Developer.
- SQL Server Management Studio — SSMS.

## Andamento

A infraestrutura inicial está instalada.

Já foram realizados o ingresso do servidor SQL no domínio,
testes de comunicação por ping, conexões locais pelo SSMS com
autenticação Windows e SQL Server e uma consulta de identificação
do servidor e da instância.

Permanecem pendentes os ajustes de endereçamento estável,
a validação detalhada de rede e DNS e a conexão direta do notebook
ao SQL Server.

As próximas práticas serão registradas conforme o avanço no curso.
O curso de 96 horas ainda não está documentado como concluído.

## Documentação

- [Infraestrutura, configurações e validações iniciais](docs/01-infraestrutura.md)

Novos documentos, scripts e evidências serão adicionados conforme
as atividades forem executadas e revisadas.

