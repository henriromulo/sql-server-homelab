# Infraestrutura do laboratório

## Objetivo

Documentar a infraestrutura utilizada para acompanhar um curso de SQL Server
de 96 horas e realizar práticas em um ambiente doméstico.

O laboratório está limitado a duas máquinas virtuais funcionando
simultaneamente, sem upgrades de hardware nesta fase.

## Servidor físico

| Item | Configuração |
|---|---|
| Plataforma de virtualização | Proxmox VE 9.2.2 |
| Processador | AMD A8-5500B |
| CPUs lógicas | 4 |
| Memória RAM | Aproximadamente 14,8 GiB |

## Estação de administração

O acesso e a administração do laboratório são realizados por um notebook
com pouca memória RAM.

As máquinas virtuais ficam hospedadas no servidor doméstico.

## Máquinas virtuais

### Primeira VM

| Item | Configuração registrada |
|---|---|
| ID no Proxmox | 100 |
| Nome no Windows | DCSRV |
| Sistema operacional | Windows Server 2019 |
| Processadores virtuais | 2 vCPU |
| Memória RAM | 4 GiB |
| Disco virtual | 60 GiB |
| Drivers VirtIO | Instalados |
| Função prevista | AD DS e DNS |

### Segunda VM

| Item | Planejamento inicial |
|---|---|
| Sistema operacional | Windows Server 2019 |
| Aplicação | SQL Server 2019 |
| Função prevista | Servidor de banco de dados |
| ID no Proxmox | A confirmar |
| Nome no Windows | A confirmar |
| Processadores virtuais | A confirmar |
| Memória RAM | A confirmar |
| Disco virtual | A confirmar |
| Edição do SQL Server | A confirmar |

## Rede

O planejamento inicial identificou uma limitação no roteador doméstico:
não é possível alterar a faixa DHCP nem cadastrar reservas de endereços.

A configuração de endereçamento adotada e os testes de comunicação
serão documentados após a conferência do ambiente atual.

## Limites do projeto

Nesta fase, não fazem parte do escopo:

- Terceira máquina virtual.
- pfSense ou outro firewall dedicado.
- Cluster.
- Acesso externo.
- Upgrades de hardware.

## Conferência do estado atual

As informações acima refletem as configurações já registradas e o
planejamento inicial.

As instalações foram informadas como concluídas. Antes de atualizar o
estado detalhado da documentação, ainda serão conferidos:

- Conclusão da promoção do DCSRV a controlador de domínio.
- Configuração do DNS.
- Configuração final da segunda VM.
- Edição e instância do SQL Server.
- Endereçamento utilizado.
- Testes de comunicação e conexão realizados.
