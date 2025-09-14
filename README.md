# ☁️ Resumo do Lab: Configurando uma instância de Banco de Dados com Microsoft Azure
Este repositório reúne os principais aprendizados adquiridos durante o laboratório de **Construindo Arquiteturas no Azure** da plataforma [DIO.me](https://web.dio.me), Módulo 2 do qual estou atualmente participando.
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
Se houver uma interrupção em uma das regiões, a Azure pode priorizar a recuperação da outra região no par, garantindo a alta disponibilidade dos seus serviços
