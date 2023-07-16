# aws

### AMAZON Lightsail

- Como criar instâncias no Lightsail;
- Entendendo as especificações dos serviços de computação na plataforma;
- Gerenciamento via ssh (client e web);
- Configurando as regras de firewall;
- Utilização do IPV4 e IPV6.
- Trabalhando com buckets para armazenamento de objetos;
- Adicionando discos a instâncias;
- Configurando um novo disco na VM.
- Conhecendo o ambiente de gerenciamento de containers;
- Fazendo deploy de um container;
- Alterando a versão do deploy.

### AMAZOn EC2 (Elastic Compute Cloud) é o serviço que nos permite ter máquinas rodando na AWS;
- t2.micro
- sob demanda
- spot
- host dedicado
- Security groups são o equivalente a ferramenta de segurança, controlam o acesso a rede da instância, podemos bloquear ou liberar tráfego, como fazemos com firewalls.
- AWS. Vamos acessar "EC2 > Instâncias > Instâncias > Zona de disponibilidade".
- Uma região geralmente recebe o nome da cidade onde se encontra. São Paulo, por exemplo, é uma região da AWS. E dentro dessa região, há 3 espaços físicos que possuem sub-redes conectadas entre si. Estes espaços físicos são chamados de zonas de disponibilidade. Cada zona de disponibilidade pode ser uma sala, um andar ou até um prédio diferente dentro da região em questão.
- Regiões e Zonas de Disponibilidade da AWS que inclusive nos permitem criar uma infraestrutura mais tolerante a falhas;

- Marketplace de imagens que nos permitem criar instâncias já com softwares pré-instalados;
- Definir em qual zona de disponibilidade nossa instância será criada, que é a partir da seleção de sub-rede.

- Imagem é relacionado ao software enquanto Modelo é ao hardware.
Ao criarmos uma instância a partir de uma imagem, podemos selecionar todo o hardware (tipo de instância, rede, etc) e algum software já vem pré-instalado.Já com o Modelo, nós podemos selecionar qualquer imagem e o hardware já estará pré-configurado.

## ddns ip static
O uso do Elastic IP garante que a sua máquina mantenha um IP único, mesmo que seja desligada.
Como o recurso de IP Dedicado funciona em relação à cobrança?
Um IP por EC2 é gratuito, caso a máquina mantenha-se ligada.
Esta é a condição para que você tenha o Elastic IP de forma gratuita. Caso haja mais IPs anexados a uma instância ou a instância seja desligada, você será cobrado.


### AWS RDS (Relational Database Service)
 - forma manual
ver qual sistema na instancia. "uname -a"
atualizar   "sudo apt update"
instalar banco de dados "sudo apt install postgresql
 - forma automatica
 - criar banco da forma facil pelo rds
 - É possível utilizar vários tipos de bancos de dados, como MySQL, MariaDB, Oracle, etc. Mas nem todos estão na categoria Free tier.

###  Load balancing
- grupos de destino (target groups).
- Para usarmos o load balancer da AWS nós precisamos definir um target group que pode ser para instâncias, IPs, etc.

### Auto scaling
- como definir um grupo de auto scaling que consegue criar (ou encerrar) instâncias automaticamente para nós.
- Quando uma outra instância do grupo for desligada ou encerrada.
Se alguma instância do grupo for desligada, o grupo criará uma nova para manter a capacidade desejada.
Quando a aplicação em uma das instâncias estiver inacessível.
Ao configurar o grupo de auto scaling nós habilitamos verificações de integridade. Se uma das instâncias não estiver mais acessível, o grupo pode criar outra. Isso foi habilitado quando na Etapa 3 (Configurar opções avançadas) nós marcamos a opção ELB em “Verificações de integridade”.

- balanceador de carga na AWS para distribuir as requisições entre nossas 2 instâncias;
- configurar um domínio para apontar para o load balancer da AWS através de seu DNS público;
- escalonamento automático (auto scaling) para que novas instâncias possam ser criadas automaticamente;
- definir políticas de escala para que regras sejam analisadas e a partir delas, novas instâncias sejam criadas no grupo de auto scaling.