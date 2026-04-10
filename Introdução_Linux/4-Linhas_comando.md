# INTRODUÇÃO AO LINUX
![Linux](https://img.shields.io/badge/Linux-000000.svg?style=for-the-badge&logo=linux&logoColor=white)

## Tópicos
- 1. [História](#1-historia)
- 2. [Distros](#2-distros)
- 3. [Interface gráfica](3#-interface-grafica)
    - 3.1 Aplicações na Internet
- # 4. [Linhas de Comando](4#-linhas-comando)
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

# 4. LINHAS DE COMANDO

### Estrutura de um Comando
Quase todo comando segue o padrão: 

    comando -opções argumentos.
    
As opções modificam o comportamento, e os argumentos dizem sobre o que o comando deve operar.

<br>
<br>

* **Permissões (Sudo):** O comando sudo permite que um usuário comum execute tarefas com privilégios de "root" (superusuário);

* **A Filosofia do Pipeline:** Com os Pipes (**|**) e Redirecionamentos (**>, <**), é possível conectar esses programas para criar soluções complexas, enviando o resultado de um para a entrada de outro;

* **Navegação e Caminhos:**
    * **Caminho Absoluto:** Começa na raiz (/);
    * **Caminho Relativo:** Começa onde o user está no momento (. atual, .. pai, ~ home);

* **Links:** *Hard links* são nomes diferentes para o mesmo arquivo físico; *Soft links* (Symlinks) são como atalhos que apontam para o caminho de outro arquivo;

* **Busca:** O comando find é utilizado para localizar arquivos por nome, tamanho, data de modificação ou tipo;

* **Gerenciamento de Pacotes:** Ocorre em dois níveis. Ferramentas de alto nível (**apt, dnf, zypper**) resolvem dependências automaticamente baixando da internet, enquanto as de baixo nível (**dpkg, rpm**) lidam com os arquivos locais.

<br>
<br>

### Comandos de Navegação

| Comando | Descrição | Exemplo |
| :--- | :--- | :--- |
| **`pwd`** | Mostra o diretório atual (Print Working Directory) | `pwd` |
| **`cd`** | Muda de diretório | `cd /usr/bin` ou `cd ..` |
| **`ls`** | Lista arquivos e pastas (`-a` mostra ocultos, `-l` detalhes) | `ls -la` |
| **`tree`** | Exibe a estrutura de pastas em formato de árvore | `tree -d` |
| **`which`** | Localiza o caminho de um comando executável | `which python` |
| **`man`** | Abre o manual de instruções de qualquer comando | `man ls` |
***
<br>

As "man pages" são divididas em capítulos (1 a 9) para separar comandos de usuário, chamadas de sistema, arquivos de configuração, etc.
O sistema info funciona como uma "web primitiva" dentro do terminal, com links entre seções. Geralmente, as páginas info são muito mais extensas e detalhadas do que as man pages.

Opção **--help:** Quase todo comando aceita esse parâmetro para mostrar uma "cola" rápida de opções;

Comando **help:** Exclusivo para comandos internos do Shell (Bash), como o cd ou echo.

### Comandos de Adminstração

| Comando / Símbolo | Função | Exemplo |
| :--- | :--- | :--- |
| **`sudo`** | Executa comandos com privilégios de superusuário (root) | `sudo apt update` |
| **`find`** | Busca arquivos por critérios (nome, tamanho, data) | `find / -name "*.log"` |
| **`grep`** | Filtra linhas que contêm uma palavra específica | `cat file.txt \| grep "Erro"` |
| **`locate`** | Busca rápida baseada em um banco de dados indexado | `locate config.php` |
| **`>`** | Redireciona a saída para um arquivo (sobrescreve) | `ls > lista.txt` |
| **`>>`** | Redireciona a saída anexando ao final do arquivo | `echo "fim" >> log.txt` |
| **`|` (Pipe)** | Conecta a saída de um comando à entrada do próximo | `history \| grep sudo` |
| **`shutdown`** | Desliga ou reinicia o sistema | `sudo shutdown -h now` |
***

<br>
<br>

### Atalhos importantes

| Ação | Tecla |
| :--- | :--- |
| **Sair (Quit)** | `q` |
| **Pesquisar termo (para frente)** | `/` |
| **Pesquisar termo (para trás)** | `?` |
| **Ir para próxima ocorrência** | `n` |
| **Descer uma página** | `Espaço` ou `Page Down` |
| **Subir uma página** | `b` ou `Page Up` |
***

<br>
<br>

## PROCESSOS

Um processo é uma instância de tarefas relacionadas (threads) em execução. Ele difere de um "programa" ou "comando", pois um único comando pode gerar múltiplos processos. O kernel do sistema operacional gerencia a alocação de recursos (CPU, memória, periféricos) para cada um.

Os tipos de Processos são nomeados como interativos, que são iniciados por usuários via CLI ou GUI (ex: Firefox, Bash), batch (Lote), que são agendados e desconectados do terminal, seguindo a ordem FIFO (ex: updatedb), daemons, serviços de sistema que rodam continuamente em segundo plano (ex: httpd, sshd), threads, os chamados "Processos leves", que rodam sob um processo principal, compartilhando memória, e por fim Kernel threads, que engloba as tarefas do núcleo que o usuário não controla (ex: kthreadd).

**Running:** O processo está usando a CPU ou esperando sua fatia de tempo (time slice) na fila de execução (run queue);

**Sleep:** O processo espera por um recurso ou evento;

**Zombie:** Processo filho que terminou, mas o pai ainda não leu seu estado. Ele aparece na lista, mas não está "vivo".
***
<br>

### ***Identificadores importantes:***

**PID:** ID único do processo;

**PPID:** ID do processo pai. Se o pai morre, o processo é "adotado" (geralmente pelo PID 2, kthreadd);

**TID:** ID da Thread (igual ao PID em processos simples);

**UID/GID:** Identificadores de Usuário e Grupo (Real e Efetivo) que determinam permissões de acesso.

### Prioridades

* Nice Value: Vai de **-20** (maior prioridade) a **+19** (menor prioridade). Quanto mais "gentil" (nice) o processo, mais ele cede lugar aos outros.

* Real-time Priority: Usado para tarefas extremamente sensíveis ao tempo.

O Load Average indica a utilização do sistema em **1**, **5** e **15** minutos. No Linux, inclui processos em execução, esperando na fila e em "espera ininterrupta" (I/O).
Um valor de 1.00 por CPU significa 100% de utilização. Acima disso, há sobrecarga.
***
<br>

| Comando | Função Principal | Exemplo de Uso |
| :--- | :--- | :--- |
| **`ps`** | Exibe o status atual dos processos (visão estática) | `ps aux` ou `ps -ef` |
| **`top`** | Monitoramento em tempo real (CPU, RAM, Swap) | `top` |
| **`htop`** | Versão interativa e visual do `top` (se instalado) | `htop` |
| **`pstree`** | Exibe a hierarquia de processos em árvore | `pstree -p` |
| **`kill`** | Envia sinais a um processo (padrão: terminar) | `kill -9 1234` |
| **`jobs`** | Lista tarefas em segundo plano no shell atual | `jobs -l` |
| **`bg`** | Retoma um processo suspenso em segundo plano | `bg %1` |
| **`fg`** | Traz um processo de segundo plano para o primeiro | `fg %1` |
| **`at`** | Agenda um comando para uma única execução futura | `at 10:00 PM` |
| **`crontab`** | Edita agendamentos de tarefas repetitivas | `crontab -e` |
| **`sleep`** | Atrasa a execução por um tempo determinado | `sleep 5m` |
| **`uptime`** | Mostra o tempo de atividade e a média de carga | `uptime` |
***
<br>
<bt>

### Agendamento de tarefas

* **at -** Executa um comando uma única vez em um horário específico no futuro.

* **cron -** Agendador de tarefas rotineiras baseado no arquivo crontab. Possui 6 campos: Minutos, Horas, Dia do Mês, Mês, Dia da Semana e Comando.

* **anacron -** Garante que tarefas agendadas pelo cron sejam executadas mesmo que o computador tenha ficado desligado no horário previsto.

* **sleep -** Apenas atrasa a execução de um comando por um período determinado (segundos, minutos, horas ou dias).
***
<br>
<br>

**[Seguir para a página anterior ←](3-Interface_grafica.md)**

<br>

**[Seguir para a próxima página →](5-Operações_arquivos.md)**

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