# Cabeça nas nuvens - AWS para iniciantes ☁️☁️☁️

## Tópicos de estudo

Resumos organizados por tópicos:

 - Introdução
   - O que é AWS?
   - Infraestrutura AWS
   - Regiões
   - Zonas de disponibilidade 
   - Pontos de presença
   - Escopo de serviço
   - Entendendo alguns serviços
 - Segurança na AWS
   - Responsabilidade compartilhada
   - IAM - Identify and Access Management
 -   Networking na AWS (Redes)
     - VPC - Virtual Private Cloud
     - Subnet
     - Internet Gateway
     - Virtual Private Gateway
     - Route Table
     - Security Groups e Network ACLs

# Introdução

 ## O que é AWS?

Amazon Web Services ou simplesmente AWS é uma plataforma de nuvem, que possui mais de 175 serviços completos de datacenters espalhados pelo mundo. Clique aqui para saber mais: [https://aws.amazon.com/pt/what-is-aws/](https://aws.amazon.com/pt/what-is-aws/)

## Infraestrutura AWS

- 24 regiões espalhadas pelo globo
- 77 zonas de disponibilidade 
- 216 pontos de presença
- 245 paises e territórios atendidos

Clique aqui par conferir a infraestrutura da AWS: https://aws.amazon.com/pt/about-aws/global-infrastructure/

## Regiões (Regions)

Uma região é composta por uma ou mais **zonas de disponibilidade**, cada região é separada geograficamente, ou seja fisicamente, e completamente independente umas das outras.

Hoje a AWS possui **24 regiões** espalhadas pelo mundo.

**Pontos importantes ao escolher uma região:**

 - **Latência**: é a rapidez com que a AWS entrega um conteúdo para o usuário. Quanto menor a latência, menor é o tempo de entrega do conteúdo.
 
 - **Custo**: São variáveis ( cuidado para não se surpreender coma fatura do cartão no final do mês hehe 😂), por exemplo: a região com menor latência provavelmente terá um maior custo em relação as outras regiões.
 
 - **Serviços Disponíveis**: Nem todas as regiões possuem os menos serviços disponíveis, antes de escolher determinada região sempre veja a lista de serviços que são oferecidos. Utilize esse link para conferir os serviços disponíveis na sua região: [https://aws.amazon.com/pt/products/](https://aws.amazon.com/pt/products/)
 
 - **Compliance**: leis do pais que aquela região se encontra, por exemplo: alguma leis que valem aqui na região da South America podem não valer em outras regiões, e você tem que seguir o compliance da região que você escolheu. 
 
## Zonas de disponibilidade (Availability Zones)

Uma AZ é um conjunto altamente redundante de datacenters, onde são projetado para operar de forma isolada das demais AZs.

As zonas de disponibilidade ficam geograficamente, ou seja fisicamente, separadas uma das outras para que em caso de algum evento numa AZ (ex: desastres naturais ou eventos causados pelo homem) outra AZ não seja impactada.

As AZs são divididas das seguintes formas:

AZ - A

AZ - B

AZ - C

AZ - D

AZ - E

AZ - F

Temos um total de no máximo (até agora) de 6 AZs por região.

**Pontos importantes:**

- A AWS faz um balanceamento de carga totalmente transparente para os usuários. Esse balanceamento é feito para que as zonas de disponibilidade não fiquem sobrecarregadas, pois por exemplo: Se todos mundo escolhesse as AZs A, B e C, elas ficariam sobrecarregadas.  Com o balanceamento feito pela AWS a AZ - A para mim pode não ser a mesma AZ - A para outro usuário, podem estar em locais diferentes e com isso a AWS evita sobrecarga em suas AZs.

- Uma AZ não é necessariamente um datacenter (é um local onde estão concentrados os sistemas computacionais de uma empresa ou organização, como um sistema de telecomunicações ou um sistema de armazenamento de dados). Uma AZ pode ser um conjunto de datacenters por exemplo.

## Pontos de presença (Edge Locations)

São **datacenters provedores de serviços considerados "globais"**. Edge locations são endpoints da AWS que são utilizados para cache de conteúdo. ao realizar o cache dos conteúdos a latência é diminuída (tem como fazer cache temporário, você poderá definir isso).

**Principais serviços hospedados em um ponto de presença:**

- Caches do CloudFront

- Serviços de CDN

- Route 53 (Serviço de DNS)

- Amazon S3 Transfer Acceleration

## Escopo de serviço

É definido se o serviço será executado dentro de uma zona de disponibilidade, dentro de todas as AZs ou se o serviço será executado globalmente, isto é, dentro de todas as regiões da AWS.

Temos 3 níveis de escopo de serviço:

- Escopo de zona de disponibilidade
- Escopo de região
- Escopo global

Escopo de zona de disponibilidade, serviços englobados:

- EC2
- RDS
- EBS
- PrivateIP

Escopo de região, serviços englobados:

- ELB
- Auto-Scaling
- AMI
- S3
- Security Group

Escopo global, serviços englobados:

- IAM
- Route 53
- Cloud Front

## Entendendo alguns serviços

**Amazon CloudFront**

É uma rede de entrega de conteúdo (CDN) rápida, altamente programável e segura.

> O Amazon CloudFront é um serviço rápido de rede de entrega de conteúdo (CDN) que entrega dados, vídeos, aplicativos e APIs a clientes em todo o mundo com segurança, baixa latência e altas velocidades de transferência em um ambiente de uso facilitado para desenvolvedores. O CloudFront é integrado com a AWS; ambos são locais físicos conectados diretamente à infraestrutura global da AWS, bem como a outros serviços da AWS. O CloudFront funciona de forma transparente com serviços como AWS Shield para mitigação de ataques DDoS; Amazon S3, Elastic Load Balancing ou Amazon EC2 como origens para os aplicativos; e Lambda@Edge para executar código personalizado mais perto dos usuários dos clientes e personalizar a experiência dos usuários. Por fim, se você usar origens na AWS, como Amazon S3, Amazon EC2 ou Elastic Load Balancing, a transferência de dados entre esses serviços e o CloudFront não será cobrada.
> https://aws.amazon.com/pt/cloudfront/

O CloudFront obtém seus conteúdos de um bucket (contêineres para objetos) do Amazon S3, uma instância do Amazon EC2, um load balancer do Amazon Elastic Load Balancing ou seu próprio servidor web, quando não está em um ponto de presença. Uma coisa legal do ClouFront é que ele pode ser usado para entregar um site ou app inteirinho incluindo conteúdo dinâmico, estático, interativo e de streaming.

**Route 53**

O Amazon é um web service de DNS (Domain Name System) altamente disponível e dimensionável.

**O que é um DNS?**

O DNS é um sistema de nomes de domínio. são os responsáveis por localizar e traduzir para números IP os endereços dos sites que digitamos nos navegadores.

Mais sobre DNS:  https://canaltech.com.br/internet/o-que-e-dns/

**Amazon S3**

O Amazon Simple Storage Service (Serviço de Armazenamento Simples) é armazenamento para a Internet. Ele foi projetado para facilitar a computação de escala na web para os devs.

Vantagens de utilizar esse serviço:

 - Criação de buckets
 - Armazenamento de dados 
 - Dowload de dados
 - Gerenciamento de permissões 
 - Uso de interfaces padrão como por exemplo REST e SOAP
 
***OBS: é recomendável utilizar o padrão API REST***

**Resumo sobre Amazon S3:**

Podemos pensar no Amazon S3 como um mapa de dados básico constituído por: **bucket + chave + ID de versão + o objeto em si**

Principais conceitos do Amazon S3

- Buckets
- Objects
- Keys
- Regions

**Buckets:** é um contêiner para armazenamento de objetos.

**Objetos:** são as entidades armazenadas dentro dos buckets esses objetos consistem em metadados e dados de objeto. **Os metadados são um conjunto de pares de nome e valor que descrevem o objeto** (pense em JSON, por exemplo). Um objeto pode ser identificado dentro de um bucket por meio de uma **chave e um ID de versão**.

**Keys:** são as chaves de identificação de falamos acima, a chave é um identificador exclusivo de um objeto em um bucket. **Cada objeto em um bucket tem exatamente uma chave**.

**Regions:** são as regiões da AWS. Você pode escolher em qual região quer criar o seu bucket e pode levar em conta alguns critérios já mencionados como custo, menor latência na entrega do conteúdo e etc. Um ponto importante é que os dados armazenados em um bucket em determinada região, não são transferidos para outra região a menos que o usuário o transfira para outra região.

Antes de começar a usar o Amazon S3 confira os endpoints que estão disponíveis na região escolhida: [https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region)

Como configurar um bucket S3 e distribuir o conteúdo usando um navegador web: https://aws.amazon.com/pt/getting-started/hands-on/deliver-content-faster/

Documentação para começara utilizar o CloudFront: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html

***OBS: É possivel utilizar o Amazon S3 gratuitamente pelo período de 12 meses***

Documentação sobre o Amazon S3: https://docs.aws.amazon.com/pt_br/AmazonS3/latest/dev/Welcome.html

# Segurança na AWS

## Responsabilidade compartilhada

Ao utilizar os serviços da AWS nós possuímos uma responsabilidade compartilhada com a empresa.

**Responsabilidade da AWS:** a AWS é responsável por proteger a infraestrutura que executa todos os serviços oferecidos na sua nuvem. Essa infraestrutura é composta por hardware, software, redes e instalações que executam os serviços.

**Responsabilidade do usuário:**  a responsabilidade do usuário será determinada pelos serviços de nuvem selecionados por ele hehehe, então cabe ao cliente ler quais "suas atribuições" para cada serviço que for utilizar.

Modelo de responsabilidade compartilhado: https://aws.amazon.com/pt/compliance/shared-responsibility-model/

## IAM - Identify and Access Management

IAM é um serviço da web que ajuda você a controlar o acesso aos recursos da AWS de forma segura

Com o IAM você controla quem é autenticado e autorizado, então é possível criar e gerenciar usuários e grupos dentro da AWS e conceder ou negar permissões por meio de polices.

**Identidades:**

- Usuários: representa uma pessoa ou serviço para interagir com recursos na AWS (quando você cria uma conta na AWS você já é um usuário).
- Grupos: conjunto de usuários com permissões atribuídas.
- Funções/Papeis: permite que delegue acesso a usuários e serviços que normalmente não tem acesso aos serviços da AWS. **Permite criar um conjunto de permissões temporários para usuários ou instâncias**.

Polices: permissões e regras de acesso a recursos da AWS, as polices são atreladas a usuários, grupos e funções/papeis

Boa práticas para a criação de usuários ou grupos:  [https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users)

# Networking na AWS (Redes)

## VPC - Virtual Private Cloud

> A Amazon Virtual Private Cloud (Amazon VPC) permite executar os recursos da AWS em uma rede virtual definida por você.
> Essa rede virtual se assemelha a uma rede tradicional que você operaria no seu datacenter, com os benefícios de usar a infraestrutura dimensionável da AWS.
> https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/what-is-amazon-vpc.html

**Resumidamente VPC é um serviço que permite o usuário criar e gerenciar uma rede privada dentro da cloud AWS. Amazon VPC é a camada de rede para as instâncias criadas no EC2.**

Principais conceitos de uma VPC:

- VPC — uma rede virtual dedicada à sua conta da AWS.

- Sub-rede — uma gama de endereços IP na VPC.

- Tabela de rotas — um conjunto de regras, chamadas de rotas, que são usadas para determinar para onde o tráfego de rede será direcionado.

- Gateway da Internet — um gateway que você anexa à VPC para permitir a comunicação entre recursos na VPC e a Internet.

- VPC endpoint — permite conectar de forma privada a VPC aos serviços compatíveis da AWS e aos serviços do VPC endpoint desenvolvidos pelo PrivateLink sem exigir um gateway da Internet, um dispositivo NAT, uma conexão VPN ou uma conexão do AWS Direct Connect. **As instâncias na sua VPC não exigem que endereços IP públicos se comuniquem com recursos no serviço. O tráfego entre a sua VPC e os outros serviços não deixa a rede da Amazon.**

Principais componentes de uma VPC:

- Networking access control list (ACLs): lista de controle de acessos, é uma camada de segurança opcional para sua VPC, **funciona como um firewall que controla o trafego de entrada e saída de uma ou mais sub redes**.

- Security group: grupo que fornece controle de entrada e saída.

- Route table: tabela de rotas que contém um conjunto de regras usadas para determinar para onde o trafego de rde ou sub rede será direcionado.

- Nat Gateway: fornece acesso a internet para instâncias EC2.

- Internet gateway: onde é liberado e fornecido acesso à internet.

***OBS: VPC tem o escopo de região, então quando você criar uma VPC ela existirá em todas as AZs daquela região.***

Infos sobre preço do serviço de VPC:  [https://aws.amazon.com/pt/vpc/pricing/](https://aws.amazon.com/pt/vpc/pricing/)

Cotas da Amazon VPC:  [https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/amazon-vpc-limits.html](https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/amazon-vpc-limits.html)

O que é o AWS Direct Connect?  [https://docs.aws.amazon.com/pt_br/directconnect/latest/UserGuide/Welcome.html](https://docs.aws.amazon.com/pt_br/directconnect/latest/UserGuide/Welcome.html)

## Subnet

A subnet faz a segmentação de endereçamentos de uma rede dentro de uma VPC na AWS.

As subnets são onde vamos disponibilizar os nossos recursos, como por exemplo uma instância EC2

 - Maior range: /16
 - Menor range: /28

**Existem dois tipos de subnet:**

 - Subnet pública: possui acesso à internet, é necessário fazer uma  configuração de entrada na route table para um internet gateway.
 - Subnet privada: não possui acesso a internet.

Documentação: https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html

## Internet gateway

Um Internet Gateway é um componente da VPC horizontalmente dimensionado, redundante e altamente disponível que permite a comunicação entre a VPC e a Internet.

 **Um gateway da internet tem duas finalidades:**
 
 - Fornecer um destino nas tabelas de rotas da VPC para o tráfego roteável na Internet.
 - Executar a NAT - Network address translation (tradução de endereços de rede) para instâncias designadas com endereços IPv4 públicos.

 Mais informações sobre NAT:
 https://www.youtube.com/watch?v=BSe7EgvDB6Q
 
https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html

Um gateway da internet oferece suporte para tráfego IPv4 e IPv6. Não causa riscos de disponibilidade ou restrições de largura de banda no tráfego de rede. **Não há custo adicional por ter um gateway da Internet na sua conta.**

Documentação: https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/VPC_Internet_Gateway.html

Resumidamente o Internet Gateway é um recurso que possibilita a comunicação das instâncias com a internet.

- Por padrão o internet gateway vem associado a VPC padrão que é gerada quando criamos nossa conta na AWS
- Cada VPC só poderá tem um Internet Gateway associado

## Virtual Private Gateway

É um recuso que possibilita conexão do ambiente on premise com sua VPC na AWS.

Existem duas formas de configurar um Virtual Private Gateway

- Blade site-to-site: https://docs.aws.amazon.com/vpn/latest/s2svpn/VPNRoutingTypes.html
- Blade direct connect: https://docs.aws.amazon.com/pt_br/directconnect/latest/UserGuide/Welcome.html

**Blade: espaço dentro da AW onde configuramos os recursos.**

## Route Table

É uma tabela lógica que possui um conjunto de regras, chamadas de rotas, que são utilizadas para direcionar onde seu tráfego de rede, de subnet, ou gateway deve chegar.

Pontos importantes:

 - Uma route table pode estar associada a vária subnets, já uma subnet só poderá estar associada a uma route table.
 - Uma VPC pode ter várias route tables.

Normalmente as route table são utilizadas para configurar rotas, como por exemplo:

- Internet Gateway
- Virtual private gateway
- NAT Gateway
- VPC Peering

Os conceitos principais das tabelas de rotas são os seguintes:

**Tabela de rotas principal** — a tabela de rotas que vem automaticamente com a VPC. Ela controla o roteamento de todas as sub-redes que não estejam explicitamente associadas com outra tabela de rotas.

 **Tabela de rotas personalizada** — uma tabela de rotas que você cria para a VPC.

 **Associação de borda** — uma tabela de rotas que é usada para encaminhar o tráfego de entrada da VPC para um equipamento. Associe uma tabela de rotas ao gateway da Internet ou ao gateway privado virtual e especifique a interface de rede do seu equipamento como destino do tráfego da VPC.

**Associação de tabela de rotas** — a associação entre uma tabela de rotas e uma sub-rede, gateway da Internet ou gateway privado virtual.

 **Tabela de rotas de sub-rede** — uma tabela de rotas associada a uma sub-rede.

 **Tabela de rotas de gateway** — uma tabela de rotas associada a um gateway da Internet ou gateway privado virtual.

 **Tabela de rotas de gateway local** — uma tabela de rotas associada a um gateway local do Outposts. Para obter informações sobre gateways locais, consulte Gateways locais no Guia do usuário do AWS Outposts.

**Destination (Destino)** – o intervalo de endereços IP para onde você deseja que o tráfego vá (CIDR de destino). Por exemplo, uma rede corporativa externa com um CIDR  [172.16.0.0/12](http://172.16.0.0/12).

**Propagação**— a propagação das rotas permite que um gateway privado virtual propague automaticamente rotas para as tabelas de rotas. Isso significa que você não precisa inserir manualmente rotas VPN para suas tabelas de rotas. Para obter mais informações sobre as opções de roteamento da VPN, consulte Opções de roteamento do Site-to-Site VPN no Guia do usuário do Site-to-Site VPN.

**Target (Destino)** – o gateway, a interface de rede ou a conexão por meio da qual enviar o tráfego de destino; por exemplo, um gateway da Internet.

 **Rota local** — uma rota padrão para comunicação dentro da VPC.

Documentação: https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/VPC_Route_Tables.html#RouteTables

## Security Groups e Network ACLs

São recursos que liberam tráfego de entreda e saída.

**Diferenças entre security groups e Network ACLs:**

**Security Groups** (atual como um firewall para instâncias EC2):

- Escopo de intâncias

- Politica padrão é permitir

- Regras são stateful (qualquer alteração aplicada a uma regra de entreda será automaticamente aplicada para as regras de saída)

- Aplica-se a uma instância somente se alguém especificar o security group ao executar uma instância ou associa posteriormente o security group com a instância

- Avaliamos todas as regras antes de decidir se permitimos ou não o tráfego

Documentação: https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/VPC_SecurityGroups.html

Network ACLs (atuam como firewall das subnets):

- Escopo de subnet

- Suporta permisão e negação (podemos negar que endereços de IP estabeleção conexão com a minha instância)

- Regras são stateless (qualquer modificação aplicada na regra de entrada não será aplicada automaticamente para a regra de saída, é necessário que você faça manualmente a regra desejada para saída)

- Aplica-se automaticamente a todas as instâncias nas sub-redes com as quais está associada (portanto, fornece uma camada adicional de defesa, caso as regras do grupo de segurança sejam permissivas demais)

- Processamos regras em ordem, começando com a regra de número menor, ao decidir se deve permitir o tráfego

Documentação: https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/vpc-network-acls.html

Leia mais sobre privacidade do tráfego entre redes na VPC:  [https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison](https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison)

# Hands On - Criação de um ambiente on premise
