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
- # 6. [Editores de Texto](6#-editores-texto)
    - 6.1 Ambiente User
    - 6.2 Manipulaçao de texto
- 7. [Operações com Conexões de Rede](7#-conexoes-rede)
- 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- 9. [Segurança](9#-seguranca)

# 6. EDITORES DE TEXTO

Dominar a edição de arquivos de texto é uma habilidade indispensável no Linux, já que quase todas as configurações e scripts do sistema dependem de texto puro. Diferente de processadores de texto como o Word, que inserem formatações invisíveis capazes de corromper arquivos de sistema, os editores de texto garantem a integridade dos dados. 

A escolha da ferramenta depende da necessidade e do ambiente: você pode usar editores gráficos como **gedit** ou **Visual Studio Code** para uma experiência intuitiva similar ao Windows, ou editores de terminal como o }**nano**, que é ideal para edições rápidas e exibe seus comandos principais diretamente na tela.

Para tarefas ainda mais simples, como criar arquivos curtos ou automatizar scripts, nem sempre é necessário abrir um editor completo. É possível alimentar arquivos diretamente pelo terminal usando o comando **echo** ou através do comando **cat** com um delimitador de fim de texto (como EOF). 

Essa flexibilidade permite que tanto iniciantes quanto administradores veteranos escolham a ferramenta que melhor se adapta ao contexto, seja uma interface visual rica ou a agilidade da linha de comando.

<br>
<br>

***nano***
    
    Interface: Terminal;

    Complexidade: Baixa;

    Uso Principal: Ideal para edições rápidas diretamente no terminal ou via conexões remotas (SSH);

***gedit***

    Interface: Gráfica (GUI);

    Complexidade: Baixa;

    Uso Principal: Editor padrão para usuários de desktop no ambiente GNOME; oferece uma experiência familiar e intuitiva;

***code (Visual Studio Code)***

    Interface: Gráfica (GUI);

    Complexidade: Alta;

    Uso Principal: Focado em desenvolvimento de software e gerenciamento de grandes projetos; possui uma vasta biblioteca de extensões e ferramentas de depuração.

***vi / vim***

    Interface: Terminal;

    Complexidade: Alta;

    Uso Principal: Ferramenta onipresente em quase todos os servidores Linux; extremamente poderoso e eficiente para quem domina seus atalhos de teclado.

Os Três Modos do vi:

* *Modo de Comando (Padrão):* Onde inicia. Cada tecla é um comando para mover o cursor, copiar ou deletar texto;

* *Modo de Inserção:* Ativado ao digitar i. Aqui escreve-se o texto. Pressione Esc para sair;

* *Modo de Linha (Ex):* Ativado ao digitar :. Usado para salvar, sair e comandos externos.

<br>

***emacs***

    Interface: Híbrida (Terminal e Gráfica);

    Complexidade: Altíssima;

    Uso Principal: Altamente extensível e customizável; é tão completo que muitos usuários o consideram quase um sistema operacional à parte.

Diferente do vi, o emacs não possui modos. Ele se comporta mais como um editor moderno, onde digita-se texto diretamente, mas usa combinações complexas de teclas (CTRL e Meta/Alt) para executar funções poderosas, como ler e-mails ou debugar código.

    Convenção: C- significa CTRL e M- significa Meta (Alt ou Esc).

<br>
<br>

## 6.1 Ambiente User

O Linux é um sistema multiusuário onde o gerenciamento de identidade e ambiente é fundamental para a segurança e produtividade. Para saber quem está operando o sistema, comandos como **whoami** e **who** identificam o usuário atual e quem mais está conectado. 

Cada conta possui um UID (User ID) único e pertence a grupos (identificados pelo GID), que servem para organizar permissões de acesso a arquivos e dispositivos de forma coletiva. O controle dessas contas e grupos é feito pelo usuário root através de comandos (useradd, groupadd e usermod) cujas informações são armazenadas em arquivos críticos como o ***/etc/passwd*** e ***/etc/group***.

A interação com o sistema ocorre através do ***shell***, que é personalizado por arquivos de inicialização. Configurações globais residem no ***/etc***, enquanto preferências pessoais ficam na pasta home do usuário (~/). 

O arquivo ~/.bash_profile é lido no login inicial, mas o **~/.bashrc** é o mais utilizado na prática, pois é executado toda vez que um novo terminal é aberto. Nesses arquivos, os usuários definem aliases (atalhos para comandos) e manipulam variáveis de ambiente, que são strings de informação lidas pelos programas.

***variáveis de ambiente mais importantes estão:***

* PATH: Uma lista de diretórios onde o sistema busca os programas executáveis;

* HOME: O caminho para o diretório pessoal do usuário;

* PS1: A variável que define a aparência do prompt de comando, permitindo exibir informações como nome de usuário (\u), máquina (\h) e diretório atual (\w).

Quanto à segurança, o acesso às funções de administrador deve ser feito com cautela. Embora o comando **su** permita trocar de usuário totalmente, a prática recomendada é o uso do **sudo**. 

Ele permite executar comandos específicos com privilégios de root de forma temporária e controlada, evitando que o usuário permaneça logado como superusuário desnecessariamente, o que reduz drasticamente os riscos de erros acidentais ou brechas de segurança.

<br>
<br>

O Bash mantém um registro dos comandos executados para que você não precise digitá-los novamente. Esse histórico é salvo no arquivo ~/.bash_history.

* Busca Inteligente (CTRL + R): Permite fazer uma busca reversa. Basta pressionar a combinação e começar a digitar parte do comando desejado; o Bash encontrará a última ocorrência.

* Comando history: Lista todos os comandos numerados que ainda estão no buffer.

<br>

### Atalhos de **Substituição** de Histórico (Bash)

| Comando | Função | Exemplo de Uso |
| :--- | :--- | :--- |
| **`!!`** | Executa o último comando exatamente como foi digitado | `sudo !!` (roda o último comando como root) |
| **`!$`** | Refere-se ao último argumento do comando anterior | `mkdir pasta; cd !$` (cria e entra na pasta) |
| **`!n`** | Executa o comando de número **n** da lista do `history` | `!42` (roda o comando 42 do seu histórico) |
| **`!-n`** | Executa o comando de **n** posições atrás no histórico | `!-2` (roda o penúltimo comando) |
| **`!string`** | Executa o comando mais recente que comece com a **string** | `!ssh` (roda o último comando ssh que você usou) |
| **`!?string?`** | Executa o comando mais recente que contenha a **string** | `!?config?` (roda o último comando que tinha "config") |
| **`^old^new`** | Substitui "old" por "new" no último comando e o executa | `cat arquivo.txt` -> `^txt^log` (vira `cat arquivo.log`) |

<br>

## 6.2 Manipulacão de texto

O comando **cat** (concatenate) é um dos mais versáteis, pois serve para ler ou criar arquivos, além de combinar vários em um só rapidamente.

<br>

| Comando | Ação / Função |
| :--- | :--- |
| **`cat file1 file2`** | Concatena e exibe o conteúdo de vários arquivos em sequência |
| **`cat f1 f2 > novo`** | Combina arquivos e salva o resultado em um **novo** arquivo |
| **`cat f1 >> exist`** | Anexa o conteúdo de um arquivo ao **final** de outro já existente |
| **`cat > arquivo`** | Cria um arquivo e grava o que você digitar (saia com `CTRL+D`) |
| **`cat >> arquivo`** | Adiciona o texto digitado ao final do arquivo (saia com `CTRL+D`) |
| **`tac arquivo`** | Exibe o conteúdo do arquivo em **ordem inversa** (linha por linha) |
***


O **echo** é usado principalmente para exibir strings no terminal ou alimentar variáveis e arquivos. É uma peça fundamental em scripts para fornecer feedback ao usuário.

    echo $USER exibe o nome do usuário logado.

    Usando a opção -e, você pode inserir quebras de linha (\n) ou tabulações (\t).

<br>
<br>

| Comando | Função | Exemplo |
| :--- | :--- | :--- |
| **`echo string > file`** | Coloca o texto em um novo arquivo (sobrescreve) | `echo "Oi" > ola.txt` |
| **`echo string >> file`**| Anexa o texto ao final de um arquivo existente | `echo "Tchau" >> ola.txt` |
| **`echo $VAR`** | Exibe o conteúdo de uma variável de ambiente | `echo $USER` |
| **`echo -e`** | Habilita caracteres especiais como `\n` (linha) e `\t` (tab) | `echo -e "A\nB"` |
***
<br>
<br>

Abrir um arquivo de **log** de vários gigabytes em um editor de texto comum pode travar o sistema, pois eles tentam carregar tudo na RAM. No Linux, usa-se ferramentas que leem o arquivo em "pedaços".

O visualizador **less** permite navegar por arquivos gigantes de forma fluida, subindo e descendo páginas sem sobrecarregar a memória.

<br>
<br>

| Comando | Função | Diferencial |
| :--- | :--- | :--- |
| **`less arquivo`** | Visualiza arquivos grandes sem carregar tudo na RAM | Permite scroll e busca interna |
| **`head -n X`** | Exibe as **X primeiras** linhas de um arquivo | Padrão é 10 linhas |
| **`tail -n X`** | Exibe as **X últimas** linhas de um arquivo | Padrão é 10 linhas |
| **`tail -f`** | Monitora um arquivo em **tempo real** | Ideal para logs de erro e acesso |
***
<br>
<br>

No Linux, o acesso aos arquivos é controlado por um sistema de permissões dividido em três categorias: ***Usuário/Dono (u), Grupo (g) e Outros (o)***.

Tipos de Permissão

    Read (r): Leitura.

    Write (w): Escrita/Alteração.

    Execute (x): Execução (necessário para scripts e programas).

***O comando chmod (Modo Numérico)***

A forma mais comum de alterar permissões é através da soma de valores octais:

    4: Leitura (r)

    2: Escrita (w)

    1: Execução (x)

Soma-se os valores para cada categoria (Dono, Grupo, Outros). Por exemplo:

    7 (4+2+1): Permissão total (rwx).

    5 (4+0+1): Leitura e execução (r-x).

    6 (4+2+0): Leitura e escrita (rw-).
***
<br>
<br>

***SED (Stream Editor)***

Utilizado para filtrar e transformar fluxos de texto. Ele trabalha em um "espaço de trabalho" temporário antes de enviar o resultado para a saída padrão.

Comandos comuns:

    sed s/padrão/substituição/ arquivo: Substitui a primeira ocorrência em cada linha.

    sed s/padrão/substituição/g arquivo: Substitui todas as ocorrências (global).

- Opção -i: Salva as alterações diretamente no arquivo original.

***AWK***

Uma linguagem de programação interpretada focada no processamento de campos (colunas) e registros (linhas), ideal para geração de relatórios.

Lê-se o arquivo linha por linha e executa ações baseadas em padrões.

Exemplos:

    awk '{ print $0 }': Imprime o arquivo inteiro.

    awk -F: '{ print $1 }': Usa o : como separador (útil para arquivos como /etc/passwd) e imprime a primeira coluna.


***SORT***

Reorganiza linhas em ordem ascendente (padrão ASCII) ou descendente.

    -r: Ordem reversa.

    -k 3: Ordena com base na terceira coluna.

    -u: Remove duplicatas após ordenar.

***UNIQ***

Remove linhas duplicadas consecutivas. Usa-se *sort arquivo | uniq* para garantir que todas as duplicatas sejam removidas.

    -c: Conta o número de ocorrências de cada linha.


***PASTE***

Une arquivos horizontalmente (coluna ao lado de coluna).

    -d: Define um delimitador personalizado (ex: vírgula).

***JOIN***

Une dois arquivos baseando-se em um campo comum (ex: um ID ou número de telefone presente em ambos).

***SPLIT***

Divide arquivos grandes em partes menores (padrão de 1000 linhas). Cria novos arquivos com prefixos (ex: xaa, xab).

<br>
<br>

**Caracteres especiais para buscas avançadas**

| Símbolo | Significado | Exemplo | Resultado do Exemplo |
| :--- | :--- | :--- | :--- |
| `.` | Corresponde a qualquer caractere único | `a..` | Encontra "azy" |
| `a\|z` | Corresponde a "a" ou "z" | `b.\|j.` | Encontra "br" e "ju" |
| `$` | Corresponde ao final de uma linha | `..$` | Encontra "og" em "dog" |
| `^` | Corresponde ao início de uma linha | `^the` | Encontra "the" no início da frase |
| `*` | Corresponde ao item anterior 0 ou mais vezes | `l.*` | Encontra "lazy dog" |
***
<br>
<br>

***GREP E STRINGS***

O utilitário grep é a ferramenta fundamental para localizar padrões dentro de arquivos de texto. Sua versatilidade permite não apenas encontrar linhas que correspondam a um **padrão específico**, mas também realizar buscas inversas com a opção **-v** (que exibe apenas as linhas que não contêm o padrão) ou localizar sequências numéricas específicas, como o intervalo de **[0-9]**. Há também a opção -C, que fornece o "contexto" da busca ao exibir um número determinado de linhas acima e abaixo da ocorrência encontrada.

Quando o alvo da busca não é um arquivo de texto simples, mas sim um arquivo binário (como uma planilha .xls ou um executável), utiliza-se o comando **strings**. Esta ferramenta varre o arquivo em busca de sequências de caracteres que sejam humanamente legíveis, possibilitando a localização de licenças, nomes de variáveis ou mensagens de erro embutidas em arquivos complexos.

<br>

***TR (Translate)***

Usado para substituir ou deletar caracteres específicos, o TR lê da entrada padrão (geralmente via pipe |), e realiza substituições, remoções e complementa e compactar arquivos.

* **Substituição**: cat arquivo | tr 'a-z' 'A-Z' (converte para maiúsculas);

* **Remoção (-d)**: tr -d 't' (deleta todos os 't');

* **Squeeze (-s)**: Compacta repetições de caracteres (ex: transformar múltiplos espaços em um só);

* **Complemento (-c)**: Trabalha com o inverso do set definido (ex: -cd [:digit:] remove tudo que não for número).

***TEE***

Ele recebe a saída de um comando e a envia para dois lugares ao mesmo tempo: a **tela** (saída padrão) e um **arquivo**.

    Exemplo: ls -l | tee lista_arquivos.txt


***WC (Word Count)***

Exibe estatísticas de contagem do arquivo, e por padrão mostra os três valores abaixo:

    -l: Conta o número de linhas;

    -w: Conta o número de palavras;

    -c: Conta o número de bytes.

***CUT***

Extrai colunas (campos) específicas de arquivos baseados em um delimitador (TAB).

    -d" ": Define um delimitador personalizado (ex: espaço);

    -f3: Seleciona o campo (coluna) número 3.

<br>
<br>
<br>

**[Seguir para a página anterior ←](5-Operações_arquivos.md)**

<br>

**[Seguir para a próxima página →](7-Operações_network.md)**


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