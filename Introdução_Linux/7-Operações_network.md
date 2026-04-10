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
- # 7. [Operações com Conexões de Rede](7#-conexoes-rede)
- 8. [Bash e scripting](#8-bash)
    - 8.1 Shell Script
- 9. [Segurança](9#-seguranca)


# 7. OPERAÇÕES COM CONEXÕES DE REDES

Uma rede é um conjunto de dispositivos conectados para compartilhar informações e recursos (impressoras, servidores, etc.). O Internet Protocol (IP) é o identificador único necessário para rotear pacotes de dados, que contêm o conteúdo da informação e cabeçalhos com origem, destino e sequência.

### IPv4 vs. IPv6

**IPv4:** Mais antigo e comum. Usa 32 bits (4,3 bilhões de endereços) e está se tornando insuficiente;

**IPv6:** Novo padrão. Usa 128 bits ($3,4 \times 10^{38}$ endereços). Oferece quase infinitas combinações, mas a migração é complexa.
***

**Network Manager**

Ferramenta moderna que padroniza a configuração via interface gráfica ou terminal (nmtui, nmcli).
***
**Interfaces**

São os canais de conexão (físicos como placas NIC ou virtuais via software). Podem ser ativadas ou desativadas conforme necessário.
***

**ip / ifconfig**

Mostram endereços IP e detalhes das interfaces. O ip é mais moderno e potente.
***

**ping**

Verifica se um host remoto está online e respondendo.
***

**traceroute**

Mostra o caminho (saltos/hops) que um pacote percorre até o destino. Útil para identificar onde há lentidão.
***

**route**

Exibe ou modifica a tabela de roteamento do sistema.
***

<br>
<br>

| Classe | Primeiro Octeto | Redes Possíveis | Hosts por Rede |
| :--- | :--- | :--- | :--- |
| **A** | 1 - 126 | 126 | 16.7 milhões |
| **B** | 128 - 191 | 16.384 | 65.536 |
| **C** | 192 - 223 | ~2.1 milhões | 256 |
***

<br>
<br>

| Ação | Comando `route` | Comando `ip` |
| :--- | :--- | :--- |
| **Mostrar tabela** | `route -n` | `ip route` |
| **Adicionar rota** | `route add -net [addr]` | `ip route add [addr]` |
| **Deletar rota** | `route del -net [addr]` | `ip route del [addr]` |
***

<br>
<br>

| Utilitário | Descrição / Função |
| :--- | :--- |
| `ethtool` | Consulta interfaces e define parâmetros como velocidade. |
| `netstat` | Exibe conexões ativas e tabelas de roteamento. |
| `nmap` | Escaneia portas abertas (segurança). |
| `tcpdump` | Captura tráfego de rede para análise. |
| `iptraf` | Monitora tráfego em modo texto. |
| `mtr` | Combina ping e traceroute em tempo real. |
| `dig` | Testa DNS (substituto do nslookup). |
***

<br>
<br>

**[Seguir para a página anterior ←](6-Editores_texto.md)**

<br>

**[Seguir para a próxima página →](8-Bash_scripting.md)**

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