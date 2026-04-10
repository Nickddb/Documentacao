# INTRODUÇÃO AO LINUX
![Linux](https://img.shields.io/badge/Linux-000000.svg?style=for-the-badge&logo=linux&logoColor=white)

## Tópicos
- 1. [História](#1-historia)
- 2. [Distros](#2-distros)
- # 3. [Interface gráfica](3#-interface-grafica)
    - 3.1 Aplicações na Internet
- 4. [Linhas de Comando](4#-linhas-comando)
    - 4.1 Documentação Linux
    - 4.2 Processos
- 5. [Operações com Arquivos](5#-operar-arquivos)
- 6. [Editores de Texto](6#-editores-texto)
    - 6.1 Ambiente User
    - 6.2 Manipulaçao de texto
- 7. [Operações com Conexões de Rede](7#-conexoes-rede)
- 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- 9. [Segurança](9#-seguranca)

# 3. INTERFACE GRÁFICA


**GUI (Interface Gráfica):** Ideal para tarefas ocasionais, navegação intuitiva e para quem não conhece todos os comandos. No curso, foca-se no ambiente GNOME.

**CLI (Linha de Comando):** Muito mais eficiente para tarefas repetitivas. É praticamente idêntica em todas as distribuições Linux.

<br>
<br>

Para a interface gráfica ser aplicada, são necessários processos da camada de software funcionarem:

**Display Manager (Gerenciador de Exibição):** Controla a tela de login (Ex: gdm para GNOME, kdm para KDE).

**X Window System (X11):** O padrão clássico desde os anos 80.

**Wayland:** O sucessor moderno, mais seguro e eficiente, padrão nas versões recentes do Fedora e RHEL.

**Desktop Environment (Ambiente de Trabalho):** É o conjunto completo (ícones, janelas, menus). O GNOME é o padrão das grandes famílias (Red Hat, SUSE, Debian/Ubuntu).
***

<br>
<br>

O painel de Configurações (Settings) é o hub central para ajustes básicos, mas o Linux possui camadas específicas para hardware e tempo, como monitores e resolução (O sistema detecta a melhor resolução automaticamente. Caso mude e a tela fique preta, o Linux reverte a alteração após alguns segundos (timeout)); 

Drives proprietários (Placas NVIDIA ou AMD podem ter softwares próprios (mais complexos) que exigem acesso de root (administrador)); Data e hora (UTC) (Internamente, o software utiliza o UTC (Tempo Universal Coordenado)); NTP (Network Time Protocol) (Protocolo que sincroniza a hora do PC com servidores na internet de forma automática).
***
<br>
<br>

***DHCP vs. Estático:*** A maioria das redes usa DHCP (configuração automática de IP). Configurações estáticas (manuais) são feitas pelo painel de rede.

***Endereço MAC:*** É o identificador físico único da placa de rede. O Linux permite alterar (mascarar) esse endereço via software.

***VPN e Banda Larga:*** O Network Manager também centraliza conexões de segurança (VPN) e modems 4G/5G.

<br>
<br>

| Categoria | Comando / Ferramenta | Descrição |
| :--- | :--- | :--- |
| **Interface** | `gnome-extensions-app` | Configura extensões de terceiros no GNOME moderno. |
| **Gráficos** | `/etc/X11/xorg.conf` | Arquivo antigo de config. de vídeo (raro em sistemas modernos). |
| **Rede** | `Network Manager` | Serviço que controla Wi-Fi, Ethernet e VPNs. |
| **Software (Debian)** | `apt install [pacote]` | Instala programas em sistemas como Ubuntu. |
| **Software (Red Hat)** | `dnf install [pacote]` | Instala programas no Fedora e RHEL moderno. |
| **Software (SUSE)** | `zypper install [pacote]` | Instala programas no openSUSE. |
| **Administração** | `YaST` | Central de controle total exclusiva da família SUSE. |
***

<br>
<br>

### Gestão de Energia e Sessão:

**Bloquear (Lock):** Protege a sessão com senha, mas mantém todos os processos rodando.

**Suspender (Sleep):** Salva o estado atual na memória RAM e desliga o restante do hardware. Economiza energia e volta rápido.

**Desligar/Reiniciar:** O sistema encerra todos os aplicativos (geralmente com confirmação de 60 segundos).

### Gerenciamento de Arquivos

O **Nautilus** (chamado apenas de "Files" ou "Arquivos") é o explorador padrão do GNOME.

**Diretório Home (/home/usuario):** Onde ficam seus documentos, downloads e configurações pessoais. Nunca apague sua pasta Home, ou você perderá suas configurações de login.

**Arquivos Ocultos:** Começam com um ponto (ex: .bashrc).

**Lixeira:** Arquivos deletados vão para ~/.local/share/Trash/files/ antes de serem removidos permanentemente.
***
<br>
<br>

### Atalhos importantes

| Ação | Atalho |
| :--- | :--- |
| **Bloquear Tela** | `SUPER` + `L` (ou `SUPER` + `Esc`) |
| **Abrir Executador de Comandos** | `ALT` + `F2` |
| **Alternar para modo Ícones (Nautilus)** | `CTRL` + `1` |
| **Alternar para modo Lista (Nautilus)** | `CTRL` + `2` |
| **Mostrar/Ocultar Arquivos Ocultos** | `CTRL` + `H` |
| **Pesquisar Arquivos (Nautilus)** | `CTRL` + `F` |
| **Focar na barra de endereço (Caminho)** | `CTRL` + `L` |
| **Mover para a Lixeira** | `CTRL` + `Delete` |
| **Excluir Permanentemente** | `SHIFT` + `Delete` |
***

<br>
<br>

## 3.1 Aplicações na Internet

Para navegar e se comunicar, o Linux oferece opções que vão desde interfaces gráficas modernas até ferramentas puramente de texto (úteis para servidores ou conexões lentas). E por isso, é considerado o "paraíso dos desenvolvedores" porque as ferramentas que costumam ser pagas ou difíceis de instalar em outros sistemas já vêm integradas ou disponíveis nos repositórios gratuitos.

* *Navegadores:* Além dos conhecidos Firefox e Chrome, o Linux possui o Epiphany (GNOME Web) e navegadores de texto como lynx e w3m;

* *E-mail:* Utilizam protocolos como IMAP (moderno/sincronizado) ou POP (antigo);

* *Gráficos:* Thunderbird, Evolution;

* *Texto:* Mutt;

* *Editores Avançados:* vi (ou vim) e emacs;

* *Compiladores:* gcc e clang (C/C++), além de suporte nativo para linguagens modernas como Go e Rust;

* *Controle de Versão:* O Git é o padrão absoluto, integrado com GitHub e GitLab;

* *IDEs:* Visual Studio Code e Eclipse são amplamente utilizados para unir todas essas ferramentas em uma interface única.

O **GIMP (GNU Image Manipulation Program)** é a alternativa de código aberto mais poderosa ao Adobe Photoshop.

Formatos: Suporta **JPEG, PNG, GIF, TIFF e muitos outros.**

Recursos Profissionais: Trabalha com camadas (layers), canais, histogramas e possui uma vasta biblioteca de plugins e filtros para retoque avançado de imagens.

<br>
<br>

**[Seguir para a página anterior ←](2-Distros.md)**

<br>

**[Seguir para a próxima página →](4-Linhas_comando.md)**


## 🔗 Recursos Úteis

Links de recursos extras além do próprio material do curso.

- [Documentação Uuntu](https://help.ubuntu.com/);
- [Documentação CentOS](https://wiki.centos.org/Documentation);
- [Documentação OpenSUSE](https://doc.opensuse.org/);
- [Documentação Gentoo](https://www.gentoo.org/support/documentation/);
- [Documentação Fedora](https://docs.fedoraproject.org/);

<br>
<br>

- **Atividades:**
* [Try It Yourself 1 - mudando o background do desktop](https://www.youtube.com/watch?v=bxvEv7jp1x0)
* [Try It Yourself 2 - mudando de users no Ubuntu](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/switchuserubuntu/index.html)
* [Try It Yourself 3 - acessando diretórios](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingcd/index.html)
* [Try It Yourself 4 - trabalhando com arquivos e diretórios](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingfilesdirs/index.html)
* [Try It Yourself 5 - localizando arquivos](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingfilesdirs/index.html)
* [Try It Yourself 6 - utilizando ls](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usinglswildcards/index.html)
* [Try It Yourself 7 - comparando arquivos](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingdiff/index.html)
* [Try It Yourself 8 - usando file](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingfile/index.html)
* [Try It Yourself 9 - identificando user](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingwho/index.html)
* [Try It Yourself 10 - usando cat](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingcat/index.html)
* [Try It Yourself 11 - usando echo](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingecho/index.html)
* [Try It Yourself 12 - usando head e tail](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingecho/index.html)
* [Try It Yourself 13 - usando sort e uniq](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingsort/index.html)
* [Try It Yourself 14 - usando tr](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingsort/index.html)
* [Try It Yourself 15 - usando wc](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingwc/index.html)
* [Try It Yourself 16 - usando DNS](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usinghost/index.html)
* [Try It Yourself 17 - usando ping, route, and traceroute](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingping/index.html)
* [Try It Yourself 18 - usando ferramentas de network](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingethtool/index.html)
* [Try It Yourself 19 - usando wget e curl](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usingwgetcurl/index.html)
* [Try It Yourself 20 - imprimindo com lp](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usinglp/index.html)
* [Try It Yourself 21 - gerenciando impressões](http://linuxfoundation.s3-website-us-east-1.amazonaws.com/TIY/usinglp/index.html)

--- 