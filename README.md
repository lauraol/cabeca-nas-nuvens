# Cabeça nas nuvens - AWS para iniciantes ☁️☁️☁️

## Tópicos de estudo

Resumos organizados por tópicos:

 - O que é AWS?
 - Infraestrutura AWS
 - Regiões
 - Zonas de disponibilidade 
 - Pontos de presença
 - Entendendo alguns serviços
 - Escopo de serviço
 - Internet Gateway e Virtual Private Gateway
 - Route Table
 - Security Group and Network ACLs
 - Nat Instances and Nat Gateways
 - EC2
 
 ## O que é AWS?

Amazon Web Services ou simplesmente AWS é uma plataforma de nuvem, que possui mais de 175 serviços completos de datacenters espalhados pelo mundo. Clique aqui para saber mais: [https://aws.amazon.com/pt/what-is-aws/](https://aws.amazon.com/pt/what-is-aws/)

## Infraestrutura AWS

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

## Entendendo alguns serviços

**Amazon CloudFront**

É uma rede de entrega de conteúdo (CDN) rápida, altamente programável e segura.

> O Amazon CloudFront é um serviço rápido de rede de entrega de conteúdo (CDN) que entrega dados, vídeos, aplicativos e APIs a clientes em todo o mundo com segurança, baixa latência e altas velocidades de transferência em um ambiente de uso facilitado para desenvolvedores. O CloudFront é integrado com a AWS; ambos são locais físicos conectados diretamente à infraestrutura global da AWS, bem como a outros serviços da AWS. O CloudFront funciona de forma transparente com serviços como AWS Shield para mitigação de ataques DDoS; Amazon S3, Elastic Load Balancing ou Amazon EC2 como origens para os aplicativos; e Lambda@Edge para executar código personalizado mais perto dos usuários dos clientes e personalizar a experiência dos usuários. Por fim, se você usar origens na AWS, como Amazon S3, Amazon EC2 ou Elastic Load Balancing, a transferência de dados entre esses serviços e o CloudFront não será cobrada.
> https://aws.amazon.com/pt/cloudfront/

O CloudFront obtém seus conteúdos de um bucket (contêineres para objetos , tipo dados) do Amazon S3, uma instância do Amazon EC2, um load balancer do Amazon Elastic Load Balancing ou seu próprio servidor web, quando não está em um ponto de presença. Uma coisa legal do ClouFront é que ele pode ser usado para entregar um site ou app inteirinho incluindo conteúdo dinâmico, estático, interativo e de streaming.

É possível utilizar esse serviço na modalidade gratuita da AWS, só atentar-se à alguns detalhes:  o nível gratuito da AWS inclui 50 GB de transferência de dados para fora e 2.000.000 de solicitações HTTP e HTTPS com o Amazon CloudFront.

Como configurar um bucket S3 e distribuir o conteúdo usando um navegador web: https://aws.amazon.com/pt/getting-started/hands-on/deliver-content-faster/

Documentação para começara utilizar o CloudFront: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html

**Route 53**

**Amazon S3**

O Amazon Simple Storage Service (Serviço de Armazenamento Simples) é armazenamento para a Internet. Ele foi projetado para facilitar a computação de escala na web para os devs.

Vantagens de utilizar esse serviço:

 - Criação de buckets
 - Armazenamento de dados 
 - Dowload de dados
 - Gerenciamento de permissões 
 - Uso de interfaces padrão como por exemplo REST e SOAP
 
***obs: é recomendável utilizar o padrão API REST***

Documentação sobre o Amazon S3: https://docs.aws.amazon.com/pt_br/AmazonS3/latest/dev/Welcome.html


