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