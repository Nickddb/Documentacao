# INTRODUÇÃO AO LINUX
![Linux](https://img.shields.io/badge/Linux-000000.svg?style=for-the-badge&logo=linux&logoColor=white)

## Tópicos
- 1. [História](#1-historia)
- 2. [Distros](#2-distros)
- 3. [Interface gráfica](3#-interface-grafica)
    - 3.1 Aplicações na Internet
- 4. [Linhas de Comando](4#-linhas-comando)
    - 4.1 Documentação Linux
    - 4.2 Processos
- 5. [Operações com Arquivos](5#-operar-arquivos)
- 6. [Editores de Texto](6#-editores-texto)
    - 6.1 Ambiente User
    - 6.2 Manipulaçao de texto
- 7. [Operações com Conexões de Rede](7#-conexoes-rede)
- # 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- 9. [Segurança](9#-seguranca)

# 8. BASH E SCRIPTING

Os usuários de Linux utilizam dois tipos principais de navegadores, dependendo da disponibilidade de uma interface gráfica, sendo eles os **navegadores gráficos**, Firefox, Google Chrome, Chromium, Konqueror e Opera.

Há também os navegadores de texto, essenciais quando não há interface GUI ou para economia de recursos, como o lynx, elinks (versão baseada no lynx que suporta tabelas e quadros), w3m, etc.

<br>
<br>

Para automação ou downloads complexos, ferramentas de linha de comando são superiores aos navegadores convencionais:

* **wget:** Ideal para baixar arquivos grandes, realizar downloads recursivos e lidar com downloads que exigem senha;

        Uso: wget <URL>

* **curl:** Focado em visualizar o código-fonte de uma URL ou transferir dados, ele permite salvar o conteúdo de uma página em um arquivo específico.

        Uso: curl -o arquivo.html <URL>
***
<br>
<br>

O **FTP** (File Transfer Protocol) é um dos métodos mais antigos de transferência (anos 70), baseado no modelo cliente-servidor.

* **Insegurança:** O FTP tradicional é considerado inadequado hoje, pois transmite credenciais sem criptografia. Muitas organizações (como a kernel.org) o abandonaram;

* **Clientes:** Existem opções gráficas como o Filezilla e de linha de comando como ftp, ncftp e yafc;

* **SFTP:** Uma alternativa segura que utiliza o protocolo SSH para criptografar os dados. Diferente do FTP comum, o SFTP não suporta acessos anônimos (guest).
***
<br>

O **SSH** (Acesso Remoto) permite fazer login em máquinas distantes de forma segura.

* **Login simples:** ssh sistema_remoto

* **Login com usuário específico:** ssh usuario@sistema_remoto

* **Execução direta:** É possível rodar um comando remoto sem abrir um shell interativo: ssh sistema_remoto comando.
***
<br>

O **SCP** (Cópia Segura) utiliza o protocolo SSH para mover arquivos entre hosts de rede com total criptografia.

    Exemplo: scp arquivo_local usuario@remoto:/caminho/destino/
<br>
<br>

## 8.1 Shell Script

Um script é um arquivo de texto contendo uma sequência de comandos que o interpretador executa automaticamente, evitando erros de digitação, economizando tempo e permitindo a automação de tarefas complexas.

A primeira linha de um script deve começar com ***#!*** seguido pelo caminho do interpretador disponível no sistema, listados em /etc/shells.. Isso informa ao sistema qual programa deve ler as linhas seguintes.

    Exemplos: #!/bin/bash, #!/usr/bin/python, #!/usr/bin/perl.
<br>


**Escrever:** Cria o arquivo com o shebang e os comandos;

**Permissão:** Torna-o executável com chmod +x hello.sh;

**Executar:** Execute com ./hello.sh (ou bash hello.sh caso não queira alterar permissões);

**Read:** Pausa a execução para que o usuário digite algo;

**Variáveis:** Para definir, use nome="Valor". Para acessar o conteúdo, use o prefixo $ (ex: echo $nome).
***
<br>
<br>

**Todo comando ou script gera um valor de saída ao finalizar.**

* **0 (Zero):** Sucesso absoluto;

* **Não-zero (1-255):** Falha ou erro (ex: ls em arquivo inexistente retorna 2).

        Verificar o resultado do último comando- $?


**Saída (>):** Grava o resultado de um comando em um arquivo (sobrescreve o conteúdo existente).

**Anexar (>>):** Adiciona o resultado ao final de um arquivo sem apagar o que já existe.

**Entrada (<):** Faz um comando ler dados de um arquivo em vez do teclado.

**Pipe (|):** Conecta a saída de um comando diretamente à entrada de outro (fluxo de dados em tempo real).
***
<br>

| Operador | Nome | Comportamento | Exemplo |
| :--- | :--- | :--- | :--- |
| `;` | Semicolon | Executa sequencialmente, independente do resultado anterior. | `cmd1 ; cmd2` |
| `&&` | AND | Executa o próximo apenas se o anterior tiver sucesso. | `cmd1 && cmd2` |
| `||` | OR | Executa o próximo apenas se o anterior falhar. | `cmd1 || cmd2` |
| `\` | Backslash | Continua o comando na linha de baixo. | `command \ line2` |

<br>
<br>

Um **script** pode executar três tipos de instruções, como:

- **Aplicações Compiladas:** Binários no sistema;
        
        ex: /usr/bin/ls, vi, gzip

- **Comandos Internos:** Comandos que fazem parte do próprio código do bash;
    
        ex: cd, echo, pwd, read

- **Outros Scripts:** Chamadas para scripts em Python, Perl ou outros shells.
***
<br>

* **$0** - O nome do próprio script.
* **$1, $2...** - O primeiro, segundo parâmetro, e assim por diante.
* **$*** - Representa todos os parâmetros passados.
* **$#** - Indica o número total de argumentos fornecidos.
***
<br>

### Funções

    nome_da_funcao () {
        comando1
        comando2
    }

**Chamada**

Basta digitar o nome da função em qualquer lugar do script após ela ter sido declarada.

<br>

**Argumentos em funções**

Assim como os scripts, as funções podem receber parâmetros próprios, acessados via $1, $2, etc., dentro do escopo da função.
***

### Condicionais e comparações

- eq: Igual a (Equal);

- ne: Diferente de (Not equal);

- gt: Maior que (Greater than);

- lt: Menor que (Less than);

- ge: Maior ou igual a;

- le: Menor ou igual a;
***
<br>

| Condição | Significado |
| :--- | :--- |
| `-e` | Arquivo existe |
| `-d` | É um diretório |
| `-f` | É um arquivo regular |
| `-s` | Possui tamanho > 0 |
| `-r` | Tem permissão de leitura |
| `-w` | Tem permissão de escrita |
| `-x` | É executável |
***
<br>
<br>

É possível comparar a ordem de classificação de strings com ***[[ string1 > string2 ]]*** ou verificar a igualdade de caracteres e também medir o comprimento de uma variável usando ***${#string}*** e extrair partes específicas. 

Para decisões complexas que envolvem múltiplos caminhos, a estrutura **case** é a muito usada em blocos if-then-else aninhados, pois compara uma variável contra vários padrões simultaneamente, executando o primeiro que coincidir e saindo imediatamente.

Para a automação de tarefas repetitivas, o shell disponibiliza três tipos de loops: o ***for*** - que itera sobre uma lista pré-definida de itens; o **while** - que repete um bloco de comandos enquanto uma condição for verdadeira; e o **until** - que funciona de forma oposta, repetindo as instruções até que uma condição se torne verdadeira.
***
<br>
<br>

***stdin*** (Standard Input):

    ID: 0

    Função: Entrada de dados, geralmente via teclado ou terminal.

***stdout*** (Standard Output):

    ID: 1

    Função: Saída de dados padrão, geralmente exibida na tela do usuário.

***stderr*** (Standard Error):

    ID: 2

    Função: Canal exclusivo para mensagens de erro e diagnósticos, separado da saída comum.
***
<br>
<br>

### Gestão de arquivos temporários
***
* **Funcionamento:** Cria arquivos ou diretórios com nomes aleatórios e imprevisíveis;

* **O uso de "Xs":** O nome é gerado com base em um modelo (ex: arquivo.XXXXXX), onde os "Xs" são substituídos por caracteres aleatórios;

* **Segurança:** Esta prática previne ataques de links simbólicos, onde um invasor poderia criar um link apontando um arquivo temporário conhecido para um arquivo crítico;

* **Prevenção de Danos:** Evita que scripts sobrescrevam acidentalmente arquivos vitais, como o **/etc/passwd**, garantindo que o arquivo criado seja único e exclusivo do processo.
***

O **/dev/null** serve para descartar saídas indesejadas de comandos. Para a geração de dados aleatórios, essenciais em segurança e testes, o shell oferece a variável **$RANDOM** e os dispositivos **/dev/random** e **/dev/urandom**, em que o primeiro fornece aleatoriedade de alta qualidade, mas pode travar se o "pool de entropia" do sistema estiver vazio. Já o segundo é mais rápido e não bloqueia, sendo suficiente para a maioria das necessidades criptográficas ao reutilizar o pool de bits aleatórios existente.

<br>
<br>

**[Seguir para a página anterior ←](7-Operações_network.md)**

<br>

**[Seguir para a próxima página →](9-Segurança.md)**

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