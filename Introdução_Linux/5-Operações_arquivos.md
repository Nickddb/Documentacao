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
- # 5. [Operações com Arquivos](5#-operar-arquivos)
- 6. [Editores de Texto](6#-editores-texto)
    - 6.1 Ambiente User
    - 6.2 Manipulaçao de texto
- 7. [Operações com Conexões de Rede](7#-conexoes-rede)
- 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- 9. [Segurança](9#-seguranca)

# 5. OPERAÇÕES COM ARQUIVOS

No Linux, quase tudo (documentos, discos rígidos, placas de som, impressoras) é tratado como um arquivo. Isso permite que você use as mesmas operações de entrada e saída (I/O) para interagir com dispositivos e dados comuns.

    /bin e /sbin: Binários essenciais do sistema (muitas vezes links para /usr/bin e /usr/sbin);

    /proc e /sys: Pseudo-sistemas de arquivos virtuais que residem na memória e mostram informações do hardware e processos em tempo real;

    /dev: Nós de dispositivos (ex: /dev/sda para o disco);

    /var: Dados variáveis (logs, filas de impressão, bancos de dados);

    /etc: Arquivos de configuração do sistema;

    /boot: Arquivos necessários para iniciar o PC (Kernel, Grub);

    /lib e /lib64: Bibliotecas compartilhadas essenciais;

    /mnt e /media: Pontos de montagem para discos temporários ou removíveis.
***

**Journaling:** Sistemas como ext4, xfs e btrfs possuem "jornal", o que evita a corrupção de dados em caso de desligamento repentino;

**NFS (Network File System):** Permite montar pastas de outros computadores via rede como se fossem locais.

<br>
<br>
<br>

| Comando | Função | Exemplo de Uso |
| :--- | :--- | :--- |
| **`mount`** | Monta um sistema de arquivos em um diretório | `sudo mount /dev/sdb1 /mnt/dados` |
| **`umount`** | Desmonta um sistema de arquivos (note que não tem o 'n') | `sudo umount /mnt/dados` |
| **`df -h`** | Exibe o espaço livre/usado em disco (human-readable) | `df -h` |
| **`du -sh`** | Resume o espaço ocupado por um diretório específico | `du -sh /var/log` |
| **`lsblk`** | Lista informações sobre todos os dispositivos de bloco | `lsblk` |
| **`file`** | Determina o tipo de arquivo (texto, binário, imagem, etc) | `file /bin/ls` |
***
<br>
<br>

Para garantir a integridade e a disponibilidade dos dados em um sistema Linux, é essencial dominar as ferramentas de sincronização e cópia. Enquanto o scp e o rsync são os pilares da movimentação de arquivos via rede — com o rsync destacando-se pela eficiência ao transferir apenas as diferenças entre pastas —, o dd atua em um nível muito mais profundo, realizando cópias bit-a-bit ideais para clonagem de discos inteiros.

Por fim, para validar se essas transferências ou alterações foram precisas, o diff surge como o utilitário de comparação textual definitivo, revelando cada divergência entre arquivos ou diretórios.

| Ferramenta | Comando para Criar/Comprimir | Comando para Extrair |
| :--- | :--- | :--- |
| **`tar`** (Geral) | `tar -cvf arq.tar /pasta` | `tar -xvf arq.tar` |
| **`gzip`** | `gzip arquivo` | `gunzip arquivo.gz` |
| **`bzip2`** | `bzip2 arquivo` | `bunzip2 arquivo.bz2` |
| **`xz`** | `xz arquivo` | `unxz arquivo.xz` |
| **`zip`** | `zip -r backup.zip /pasta` | `unzip backup.zip` |

| Formato | Comando de Criação | Comando de Extração |
| :--- | :--- | :--- |
| **.tar.gz** | `tar -zcvf arquivo.tar.gz /origem` | `tar -zxvf arquivo.tar.gz` |
| **.tar.bz2**| `tar -jcvf arquivo.tar.bz2 /origem`| `tar -jxvf arquivo.tar.bz2`|
| **.tar.xz** | `tar -Jcvf arquivo.tar.xz /origem` | `tar -Jxvf arquivo.tar.xz` |

<br>
<br>
<br>

**[Seguir para a página anterior ←](4-Linhas_comando.md)**

<br>

**[Seguir para a próxima página →](6-Editores_texto.md)**

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