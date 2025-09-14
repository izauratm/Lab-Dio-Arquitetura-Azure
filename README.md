# ☁️ Resumo do Lab: Construindo Arquiteturas no Microsoft Azure
Este repositório reúne os principais aprendizados adquiridos durante o laboratório de **Construindo Arquiteturas no Azure** da plataforma [DIO.me](https://web.dio.me), Módulo 2, do qual estou atualmente participando.
O foco está nos benefícios e aplicações práticas da plataforma Microsoft Azure, explorando seus recursos e funcionalidades.
O Bootcamp oferece uma base sólida em tecnologias de nuvem, abordando desde os conceitos fundamentais até os componentes essenciais da arquitetura Azure. Entre os temas estudados estão: criação e gerenciamento de máquinas virtuais, configuração de bancos de dados e soluções de armazenamento, além de tópicos avançados como arquitetura em nuvem, governança, monitoramento e segurança de ambientes cloud. 

---

## 📘 Tópicos Abordados
Este repositório contém anotações e resumos sobre os principais componentes de arquitetura da plataforma Microsoft Azure. 
Este material serve como referência para estudos e para a criação de ambientes em nuvem de forma organizada e escalável.

### 🏗️ Componentes de Arquitetura do Azure
A arquitetura do Azure é hierárquica e organizada, projetada para permitir a gestão eficiente de recursos em grande escala. O modelo hierárquico, de cima para baixo, é:
- Grupos de Gerenciamento → Assinaturas → Grupos de Recursos → Recursos

Essa estrutura garante que possamos aplicar políticas e permissões em níveis diferentes, facilitando a governança e o controle de custos.

### 🗺️ Regiões e Pares de Regiões
Uma região do Azure é um conjunto de datacenters fisicamente isolados dentro de uma localização geográfica. Ao implantar um recurso, como uma máquina virtual ou um banco de dados, o criamos em uma região específica.

O Azure oferece mais regiões globais do que qualquer outro provedor de nuvem, com mais de 60 regiões representando mais de 140 países.

Um par de regiões é um conjunto de duas regiões na mesma área geográfica que estão emparelhadas por motivos de recuperação de desastres. Por exemplo, "Leste dos EUA" e "Oeste dos EUA" formam um par de regiões.
Se houver uma interrupção em uma das regiões, a Azure pode priorizar a recuperação da outra região no par, garantindo a alta disponibilidade dos seus serviços.

### 📌Zonas de Disponibilidade (Availability Zones)
As Zonas de Disponibilidade no Azure são uma das principais formas de garantir a alta disponibilidade e a resiliência das aplicações na nuvem. Uma Zona de Disponibilidade é um datacenter fisicamente separado e isolado dentro de uma região do Azure. Cada região habilitada para Zonas de Disponibilidade tem pelo menos três dessas zonas, que são independentes uma da outra.

Cada zona tem sua própria:
- Fonte de energia: Um datacenter não compartilha a mesma rede de energia elétrica que os outros.
- Rede: As zonas são interligadas por uma rede de alta velocidade, mas são fisicamente separadas. Conectadas por meio de redes privadas de fibra óptica.
- Refrigeração: O sistema de resfriamento é independente.

O objetivo dessa separação é proteger os seus serviços contra falhas de hardware, interrupções de energia e até mesmo desastres naturais (como inundações ou incêndios) que poderiam afetar um datacenter inteiro.

Quando implantamos uma aplicação em uma região que suporta Zonas de Disponibilidade, podemos distribuir nossos recursos (como máquinas virtuais, bancos de dados e armazenamento) entre as zonas. Exemplo: criar uma VM na Zona 1, outra na Zona 2 e uma terceira na Zona 3. Se a Zona 1 tiver um problema, as outras VMs continuarão funcionando nas Zonas 2 e 3, garantindo que a aplicação permaneça online. O tráfego de rede é automaticamente direcionado para as zonas que estão operacionais.

Essa é uma abordagem mais robusta do que simplesmente usar um único datacenter (mesmo que com recursos redundantes dentro dele).

Portanto, as Zonas de Disponibilidade são a base para construir soluções robustas e tolerantes a falhas no Azure, garantindo que as aplicações permaneçam acessíveis mesmo diante de problemas em larga escala em um dos datacenters.
<img width="400" height="350" alt="7 zonas disponibilidade" src="https://github.com/user-attachments/assets/3169f967-77e6-4162-8520-e4e61c4cb87b" />


### 📦 Grupo de Recursos
- Um grupo de recursos é um contêiner lógico que agrupa recursos relacionados para um projeto ou aplicação. Ele atua como um diretório onde armazenamos e gerenciamos nossos recursos.
* **Principais características:**
  * **Ciclo de Vida:** podemos gerenciar todos os recursos em um grupo de recursos juntos. Por exemplo, para deletar uma aplicação completa, basta deletar o grupo de recursos.
  * **Permissões:** podemos aplicar permissões de acesso em nível de grupo de recursos, controlando quem pode criar, modificar ou excluir recursos nesse grupo.
- Alguns passos para criar um grupo de recursos:
<img width="400" height="300" alt="3 criar grupo de recursos" src="https://github.com/user-attachments/assets/e25c1943-b6e2-4eaf-8f1b-56fd4c9a0a84" />
<img width="400" height="300" alt="4 criar grupo recursos" src="https://github.com/user-attachments/assets/a083a597-7c9c-4fc4-8763-ead654a6fe81" />
<img width="400" height="300" alt="4 criar grupo recursos" src="https://github.com/user-attachments/assets/2d40fd6f-1695-4a96-bea4-9c18cb4bb29e" />
<img width="400" height="300" alt="5 criado grupo recursos" src="https://github.com/user-attachments/assets/8d8e5784-4cbb-4120-80d4-6429cb12e5e6" /> 
    

### 🔐 Assinaturas do Azure
Uma assinatura é um contêiner lógico que agrupa recursos e serviços do Azure. Ela é o nível de faturamento e de cobrança.
- Faturamento: cada assinatura é vinculada a um método de pagamento e tem um limite de gastos.
- Limites de Recursos: existe um limite máximo de recursos que podemos criar dentro de uma única assinatura.
- Gerenciamento de Acesso: as assinaturas servem para isolar ambientes, como produção, desenvolvimento e testes podendo ter uma assinatura para cada equipe ou projeto, controlando quem tem acesso a quais recursos.
<img width="500" height="626" alt="1 assinaturas do azure" src="https://github.com/user-attachments/assets/28e78667-b4b2-458c-a82e-cebe9b40bd5c" />

### 👥 Grupos de Gerenciamento
Os grupos de gerenciamento são o nível mais alto na hierarquia de recursos do Azure. Eles permitem organizar as assinaturas em grupos e aplicar políticas de governança e permissões de forma centralizada.
- Finalidade: ideal para grandes empresas que precisam gerenciar múltiplas assinaturas de maneira consistente.
- Benefício: quando aplicamos uma política em um grupo de gerenciamento, todos os recursos dentro das assinaturas filhas (e seus respectivos grupos de recursos e recursos) herdarão essa política automaticamente. Isso economiza tempo e garante a conformidade.
<img width="500" height="658" alt="2 grupos de gerenciamento" src="https://github.com/user-attachments/assets/9f83db7b-279f-4d89-8708-f832d6b29e60" />


---
## ✅ Conclusão
A compreensão dos principais componentes da arquitetura do Azure — como regiões e pares de região, zona de disponibilidade, grupos de recursos, assinaturas e grupos de gerenciamento — é essencial para estruturar ambientes de nuvem seguros, escaláveis e organizados. Esses elementos formam a base da governança e do controle de recursos dentro da plataforma, permitindo que profissionais de tecnologia planejem, implementem e mantenham soluções eficientes no Azure.

Este material serve como apoio para quem está iniciando na jornada de computação em nuvem com Azure, oferecendo uma base sólida para futuras aplicações, certificações ou projetos profissionais.
> Este conteúdo faz parte do projeto **Construindo Arquiteturas no Azure - Laboratório** da plataforma DIO.me.

---
 
### 📚 Recursos Complementares
- [Tutorial oficial para criar e gerenciar VMs Windows](https://learn.microsoft.com/pt-br/azure/virtual-machines/windows/tutorial-manage-vm)
- [SQL do Azure para Iniciantes](https://learn.microsoft.com/pt-br/shows/azure-sql-for-beginners/)
- [Portal Microsoft Azure](https://portal.azure.com/#allservices)
- [Azure Global Infrastructure](https://azure.microsoft.com/en-us/explore/global-infrastructure)
- [Explore Global Datacenters](https://datacenters.microsoft.com/globe/explore)
- [O que são as regiões do Azure?](https://learn.microsoft.com/pt-br/azure/reliability/regions-overview)
- [Grupos de Gerenciamento do Azure](https://learn.microsoft.com/pt-br/azure/governance/management-groups/overview)
- [Calculadora de Preços Azure](https://azure.microsoft.com/pt-br/pricing/calculator/?ef_id=_k_EAIaIQobChMI14z7o_fWjwMVc0FIAB3PYQApEAAYASACEgLE-fD_BwE_k_&OCID=AIDcmmzmnb0182_SEM__k_EAIaIQobChMI14z7o_fWjwMVc0FIAB3PYQApEAAYASACEgLE-fD_BwE_k_&gad_source=1&gad_campaignid=1635078708&gbraid=0AAAAADcJh_s0nlhmSLvv4COb6oAkGNm0s&gclid=EAIaIQobChMI14z7o_fWjwMVc0FIAB3PYQApEAAYASACEgLE-fD_BwE)
- [Assinatura do Azure](https://learn.microsoft.com/pt-br/azure/azure-resource-manager/management/azure-subscription-service-limits)
  
📎 Link do curso: [Microsoft Azure AZ-900 - DIO.me](https://web.dio.me/lab/computacao-da-nuvem-laboratorio/learning/6d6083cf-0291-428d-a5f2-c93166e6874d)

🖼️ Imagens: Fonte Dio.me
  
