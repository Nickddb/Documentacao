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
- 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- # 9. [Segurança](9#-seguranca)

# 9. SEGURANÇA

O **Common UNIX Printing System** é o padrão que permite ao Linux processar e enviar documentos para impressoras, convertendo arquivos das aplicações em linguagens que o hardware compreenda.

### Arquitetura e Funcionamento
* *Servidor de Impressão:* Atua tanto para impressoras locais (USB) quanto de rede;

* *Filtros e Drivers:* Usa filtros para converter formatos de arquivos e drivers para descrever as capacidades da impressora;

* *Fila de Impressão:* Os trabalhos são armazenados em */var/spool/cups*. Arquivos com prefixo d são dados; prefixo c são arquivos de controle;

* *Logs:* Registros de atividades e erros ficam em /var/log/cups.
***
<br>
<br>

A maioria das configurações é feita automaticamente, mas existem arquivos cruciais em /etc/cups/:

* **cupsd.conf:** Configurações globais e de segurança da rede.

* **printers.conf:** Detalhes específicos de cada impressora instalada (não deve ser editado manualmente).

* **systemctl status cups:** Verifica se o serviço está rodando.

* **systemctl start/stop/restart cups:** Inicia, para ou reinicia o serviço.

* **Interface Web:** Interface de gerenciamento que pode adicionar impressoras e gerenciar filas de trabalhos.
<br>
<br>
<br>

| Comando | Função |
| :--- | :--- |
| `lp <arquivo>` | Imprime o arquivo no destino padrão. |
| `lp -d <impressora> <arq>` | Imprime em uma impressora específica. |
| `lp -n <número> <arq>` | Imprime múltiplas cópias. |
| `lpstat -p -d` | Lista impressoras disponíveis e o padrão. |
| `lpq -a` | Mostra o status da fila de impressão. |
| `lpoptions -d <imp>` | Define a impressora padrão do sistema. |
| `cancel <ID_job>` | Cancela um trabalho de impressão específico. |
| `lpmove <ID> <nova_imp>` | Move um trabalho de uma impressora para outra. |

<br>
<br>

**PostScript:** Uma linguagem de descrição de página em texto puro. Embora poderosa, foi amplamente substituída pelo PDF por ser um formato mais pesado.

**PDF:** Formato comprimido e padrão atual para documentos finais.
<bR>
<br>

### Conversão de Formatos
Ferramentas como **enscript** e **convert** facilitam a mudança entre texto, PS e PDF:

**enscript -2 -r arquivo.txt:** Converte texto para PostScript em 2 colunas e modo paisagem;

**ps2pdf arquivo.ps:** Converte PostScript para PDF;

**pdf2ps arquivo.pdf:** Converte PDF para PostScript.

<br>

### Ferramentas Principais:
**qpdf:** Moderna e completa, ideal para criptografia e mesclagem;

**pdftk-java:** Excelente para "grampear" (mesclar) e rotacionar páginas;

**Ghostscript:** O motor de interpretação mais robusto, embora seus comandos sejam mais complexos;

    Mesclar PDFs: qpdf --empty --pages 1.pdf 2.pdf -- saida.pdf

**Rotacionar todas as páginas:** pdftk A=in.pdf cat A1-endright output out.pdf;

**Criptografar com senha:** pdftk public.pdf output private.pdf user_pw SENHA;

**Extrair informações (metadados):** pdfinfo arquivo.pdf;

**flpsed:** Adiciona dados ou comentários em documentos PostScript (ótimo para formulários);

**pdfmod:** Interface gráfica simples para remover ou reordenar páginas de PDFs arrastando e soltando;

**/dev/null:** Descartar a saída de um comando de impressão em um script.
***
<br>
<br>

***Identificação e Tipos de Conta***

O Linux identifica cada usuário através de um nome de login e um número único chamado **UID** (User ID), em que as contas são categorizadas para isolar processos: 
* *root* (UID 0) detém privilégios totais, contas de sistema gerenciam serviços;
* *Contas normais* (UID 1000+) são destinadas ao uso cotidiano com permissões limitadas.

A segurança baseia-se na separação rigorosa de processos, impedindo que uma aplicação acesse recursos de outra indevidamente. Tecnologias modernas como **cgroups, containers** e **virtualização** levam esse isolamento a níveis mais profundos. Além disso, o sistema trata dispositivos de hardware *(como discos em /dev/sd*)* como arquivos, aplicando as mesmas permissões rígidas de acesso.

Para evitar vulnerabilidades, senhas são criptografadas (SHA-512) e guardadas no arquivo */etc/shadow*, acessível apenas pelo root. O sistema também utiliza módulos como o PAM (garante que as senhas sejam fortes) e ferramentas como o chage (gerencia a expiração periódica das credenciais).
<br>
<br>

***Segurança do Boot e Atualizações***

A proteção do sistema começa antes mesmo do login, podendo incluir senhas no carregador de inicialização (GRUB 2) e na BIOS para evitar o uso de mídias externas maliciosas. 

Manter o sistema atualizado é a defesa mais eficaz contra vulnerabilidades conhecidas, já que a comunidade Linux costuma lançar correções de segurança rapidamente em seus repositórios oficiais.

Mesmo com proteções de software, o acesso físico ao hardware representa um risco crítico. Técnicas como **keylogging, sniffing de rede** ou o uso de **discos de resgate** podem comprometer dados se o computador não estiver em um local seguro. Por isso, políticas de segurança empresarial exigem o bloqueio de estações de trabalho e a proteção física de servidores e periféricos.

<br>
<br>

**[Seguir para a página anterior ←](8-Bash_scripting.md)**

<br>


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