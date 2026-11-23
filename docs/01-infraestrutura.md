# Infraestrutura do laboratório

## Objetivo

Manter um laboratório doméstico para acompanhar um curso de SQL Server
de 96 horas, documentando as práticas executadas, as configurações
aplicadas e os resultados validados.

O ambiente está limitado a duas máquinas virtuais funcionando
simultaneamente, sem upgrades de hardware nesta fase.

## Servidor físico

| Item | Configuração |
|---|---|
| Plataforma de virtualização | Proxmox VE 9.2.2 |
| Nome do nó no Proxmox | pve |
| Processador físico | AMD A8-5500B |
| CPUs lógicas disponíveis | 4 |
| Memória RAM | Aproximadamente 14,8 GiB |

## Estação de administração

O notebook é utilizado para acessar a interface web do Proxmox
pelo navegador e administrar as máquinas virtuais por Área de
Trabalho Remota.

As duas VMs ficam hospedadas no servidor doméstico e são utilizadas
simultaneamente.

## Máquinas virtuais

Os nomes exibidos no Proxmox são diferentes dos nomes configurados
dentro do Windows.

| Item | VM de domínio | VM de banco de dados |
|---|---|---|
| ID no Proxmox | 100 | 101 |
| Nome no Proxmox | DC01 | SQL01 |
| Nome no Windows | DCSRV | DBSRV1 |
| Sistema operacional | Windows Server 2019 Datacenter Evaluation | Windows Server 2019 Datacenter Evaluation |
| Processadores virtuais | 2 vCPU | 2 vCPU |
| Memória RAM | 4 GiB | 5 GiB |
| Disco do sistema | 60 GiB | 80 GiB |
| Controladora SCSI | VirtIO SCSI single | VirtIO SCSI single |
| Adaptador de rede | VirtIO | VirtIO |
| Bridge de rede | vmbr0 | vmbr0 |
| Drivers VirtIO | Instalados | Instalados |
| Função | Controlador de domínio e DNS | SQL Server |


A promoção do DCSRV a controlador de domínio foi concluída,
conforme validação relatada durante a montagem do laboratório.

## SQL Server

| Item | Configuração |
|---|---|
| Versão e edição | SQL Server 2019 Developer |
| Servidor retornado pela consulta de identificação | DBSRV1 |
| Tipo de instância | Padrão |
| Modo de autenticação | Misto: Windows e SQL Server |
| SQL Server Management Studio | Instalado na VM 101 |

### Armazenamento da VM 101

O Proxmox apresenta os seguintes discos virtuais:

| Dispositivo | Capacidade |
|---|---|
| scsi0 | 80 GiB |
| scsi1 | 85 GiB |
| scsi2 | 50 GiB |

No Windows, foram informadas as seguintes unidades:

| Unidade | Identificação | Finalidade |
|---|---|---|
| C: | Sistema | Windows e instalação dos programas |
| L: | vollog | Logs do SQL Server |
| P: | voldata | Dados do SQL Server |

Os caminhos de dados e logs foram definidos durante a instalação
do SQL Server, conforme relato da configuração realizada.

Os diretórios completos e a localização efetiva dos arquivos
ainda não foram conferidos nesta documentação.

## Rede e acesso

| Item | Situação registrada |
|---|---|
| Bridge da VM 100 | vmbr0 |
| Bridge da VM 101 | vmbr0 |
| DNS informado no DCSRV | 127.0.0.1 |
| DNS informado no DBSRV1 | Recebido automaticamente do roteador |
| Administração das VMs | Área de Trabalho Remota |
| Administração do Proxmox | Interface web pelo notebook |


Será solicitado acesso administrativo ao roteador para avaliar
as opções disponíveis e definir o endereçamento das duas VMs
e do host Proxmox. Nenhuma solução definitiva de endereçamento
está registrada como concluída.

## Validações realizadas

| Validação | Resultado registrado | Base do registro |
|---|---|---|
| Uso simultâneo das duas VMs | Confirmado | Relato de utilização |
| Comunicação por ping entre máquinas, incluindo o notebook | Realizada | Relato do teste |
| Acesso remoto às VMs | Funcionando | Relato de utilização |
| Ingresso do DBSRV1 no domínio | Concluído | Relato da configuração |
| Conexão local pelo SSMS com autenticação Windows | Bem-sucedida | Relato do teste |
| Conexão local pelo SSMS com autenticação SQL Server | Bem-sucedida | Relato e captura do SSMS |
| Consulta de identificação do servidor e da instância | Executada com sucesso | Captura do resultado |

### Primeira consulta SQL registrada

Foi executada a seguinte consulta no SSMS da VM 101:

~~~sql
SELECT
    SERVERPROPERTY('ServerName') AS Servidor,
    SERVERPROPERTY('InstanceName') AS Instancia;
~~~

Resultado observado:

| Servidor | Instancia |
|---|---|
| DBSRV1 | NULL |

A consulta retornou uma linha. O resultado de InstanceName
identificou a utilização de uma instância padrão.

Esse teste foi realizado no ambiente da VM 101. Ele não representa
uma conexão direta do SSMS instalado no notebook ao SQL Server.

