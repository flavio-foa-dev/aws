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

### aws cli
- aws configure = aws access key id [***********************]
- aws secret acces key [***********************]
- aws help
- CLI documentation
- default regian name
- iam controle de acesso
- mfa autenticacao
- permissionamento ao criar um novo usuário. Isso e feito através do serviço IAM;
- AWS CLI, que é a interface de linha de comando para gerenciar tudo na AWS;
- comandos da AWS CLI para gerenciar instâncias EC2 como describe-instances e stop-instances. etc

### Amazon VPC (virtual private cloud) redes na aws
- VPC, basicamente, é o serviço da Amazon que nos permite configurar a rede de nossa infraestrutura na AWS;
- VPC padrão e as sub-redes que vêm configuradas nela,
- Cada sub-rede está em uma zona de disponibilidade diferente;
- Criar uma nova instância EC2  e configurar de forma consciente as configurações de rede.
- security groups, partindo da premissa deles serem stateful e só suportarem regras de permissão e não de bloqueio;
- ACLs elas nos permitem regras mais granulares tanto de bloqueio quanto de permissão, além de entendermos que elas são stateless;
- como utilizá-los em conjunto.
- sudo tcptraceroute www.google.com = mapea o caminho pecorrido
- a diferença entre um Internet Gateway e um NAT Gateway, ficando claro que o primeiro permite o acesso da internet até nossa sub-rede e vice-versa, enquanto o segundo apenas permite o acesso da sub-rede até a internet;
- tabelas de rotas da AWS VPC, que permitem que façamos roteamentos de um endereço (ou vários) para outro;
Configuramos uma nova tabela de rotas para tornar pública a nossa sub-rede que era originalmente privada. Essa tabela de rotas possui uma regra que manda o tráfego para um Internet Gateway;
- VPC Endpoint que liga diretamente nossa VPC a alguns serviços da AWS, podendo nos fornecer maior performance e redução de custos.
- Políticas de permissões na AWS;
- Bastion host para termos um maior controle sobre os acessos em nossas instâncias que estão na sub-rede privada.

### S3 (Amazon Simples storage Service - scalable Storage in the Cloud) armazenamento de objetos
- service = google drive. dropbox
- guarda back-up
- guarde objects
- bucket = um repositorio
- urls pre assinadas com token de expiracao
- Por padrão o acesso aos buckets / objetos é: Restrito. todos os buckets e objetos do Amazon S3 são privados. Somente o proprietário do recurso que é a conta de que criou o recurso pode acessar esse bucket.
- Para mudarmos o permissionamento de um bucket privado para público é necessário: a mudança da configuração em Block all public access seguindo com a criação de uma policy com as devidas regras de acesso.
- Criar um bucket Público;
- Configurar uma policy de acesso;
- Como conceder acesso a um usuário através da console;
- Utilizar o IAM para criar usuários e grupos;
- Diferença entre as políticas de acesso.

### AWS CLI
Vamos acessar a documentação em https://docs.aws.amazon.com/AmazonS3/latest/userguide/setup-aws-cli.html. Neste link, vamos instalar a CLI da AWS com todas as suas subferramentas para linha de comando. Essa ferramenta não serve apenas para o S3, ela é aplicável, por exemplo, para criação de máquinas virtuais, bancos de dados e outros serviços.
Versionamento dos objetos;
Configurando um bucket com versionamento;
Utilizar comandos s3api;
Conceito sobre ciclo de vida dos objetos;
Aplicar regras de ciclo de vida.