# VIRTUALIZAÇÃO
![VMware](https://img.shields.io/badge/VMware-606060.svg?style=for-the-badge&logo=vmware&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-214294.svg?style=for-the-badge&logo=virtualbox&logoColor=white)

## Tópicos
-  1. [Computação](#1-computacao)
# 2. [Virtualização](#2-virtualizacao)

<br>
<br>

# 2. VIRTUALIZAÇÃO


**Virtualização** é a tecnologia que cria uma camada de software sobre o hardware físico, permitindo que os recursos (CPU, RAM, Disco) sejam distribuídos de forma lógica. Um sistema (Hypervisor) gerencia o hardware real para "fingir" a existência de múltiplos hardwares independentes. A VM é o produto final da virtualização - um computador completo em formato de software.

**Vantagens -** Proporciona escalabilidade e flexibilidade, permitindo que um único servidor físico hospede diversos sistemas diferentes.

* **Isolamento -** Cada VM roda seu próprio Sistema Operacional e aplicações em um espaço isolado, garantindo que uma falha em uma máquina não afete as outras.

* **Eficiência -** É a maneira mais inteligente de usar o hardware, pois evita que recursos fiquem ociosos (como um servidor potente rodando apenas um serviço leve).

* **Confiabilidade -** Facilita o backup, a migração entre servidores e a recuperação de desastres.

<br>

***Desktop vs. Servidor***

A principal diferença entre essas arquiteturas reside na finalidade e resiliência. Enquanto o **Desktop** é projetado para o uso de rotina e interações humanas pontuais, o **Servidor** é construído para priorizar estabilidade e disponibilidade constante de dados na rede.


## Armazenamento

A CPU é responsável por realizar cálculos e processar as tarefas determinadas pelo usuário. Ela opera fundamentalmente através do padrão binário ($0$ e $1$), que representa estados elétricos (desligado e ligado).

A **RAM** é o componente de alta velocidade que armazena temporariamente os programas em execução;

* *Volatilidade* - É uma memória volátil que requer energia para manter os dados. Ao desligar o computador, as informações são apagadas;

* *Tipos e Tecnologias* - Pode variar entre **UDIMM** (sem registro) e **RDIMM** (com registro/circuito intermediário), além de possuir versões com ECC, que detectam e corrigem erros de dados, sendo comuns em servidores.

<br>
<br>

**HDD** (Hard Disk Drive) é uma tecnologia mecânica composta por "pratos" magnéticos e um cabeçote móvel, sendo mais econômico e durável para grandes volumes de dados (filmes, fotos), porém mais lento e frágil a impactos;

**SSD** (Solid State Drive): Baseado em chips de memória Flash. É muito mais rápido, resistente a quedas e silencioso, sendo ideal para instalar o sistema operacional e jogos.

**ROM:** Armazena o Bootloader e softwares de diagnóstico (POST);

**Flash:** Guarda a imagem comprimida do sistema operacional (IOS);

**NVRAM:** Memória não volátil que armazena as configurações de inicialização (startup-config);

**Gestão de Periféricos:** Controla as interfaces de Entrada/Saída (E/S), como mouse, teclado e monitor;

**Conectividade:** Abriga as conexões de rede e slots de expansão para garantir que todo o ecossistema eletrônico funcione de forma integrada.
***
<br>
<br>

**[Seguir para a página anterior ←](1-História.md)**

<br>
<br>

## 🔗 Recursos Úteis

Links de recursos extras além do próprio material do curso.

- [PDF de apoio](virtualizacao.pdf)
---