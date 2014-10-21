Linux shell 101
===============

![454](assets/linux.jpg)

##<center>Francisco Pina Martins</center>
###<center>21/10/2014</center>

---

A shell e "porque é que eu preciso disto" ?
==========================================

##O que é:

* Uma interface com o computador via "linha de comandos"
* *bash* (ksh zsh fish dash etc...)
* Acede-se através de um "terminal"
* Apesar de tudo o rato também é útil na shell

</br>

##Para que é que preciso dela?

* Servidores HPC
* Acesso remoto
* Interface **simples**
* Automatização e reprodutibilidade de processos

##Não acreditam? Vejam.

---

O *prompt*
==========

``user@machine:~$``

``bash-4.1$``

![Prompt image](assets/shell_prompt.gif)

---

Navegação e orientação
======================

##Pensem na vossa shell como um gestor de ficheiros

1. Onde é que eu estou?
2. O que é que há aqui?
3. Como é que me movimento?

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ pwd``

``$ ls``

``$ cd``

##Significado:

1. <font color="red">p</font>rint <font color="red">w</font>orking <font color="red">d</font>irectory
2. <font color="red">l</font>i<font color="red">s</font>t
3. <font color="red">c</font>all <font color="red">d</font>irectory

---

O vossos novos melhores amigos
==============================

``man nome_do_programa``

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

* **TODOS** os programas *builtin* na shell (coreutils) têm um
* Alguns outros também

``$ man ls``

``$ whatis ls``

<div style="float: right"><img src="assets/Tab-Key.png" /></div>
##Tecla "Tab"

* Completa o que estão a escrever
* Com uma ou duas "*keypress*"

##Teclas ↓ e ↑

* Navegam pela lista de comandos anteriores

---

Caminhos (path) e convenções
============================

##Os caminhos podem ser absolutos ou relativos

##Ex. de caminhos absolutos
``/etc/fstab``

``~/Downloads/ficheiro.txt``

##Ex. de caminhos relativos
``Downloads/ficheiro.txt``

``./ficheiro.txt``

##Convenções comuns

* <font color="red">~</font> -> *home dir*, por ex. ``/home/francisco``
* <font color="red">./</font> -> "Aqui"
* <font color="red">../</font> -> Um diretório abaixo
* <font color="red">../../</font> -> Dois diretórios abaixo
* <font color="red">.ficheiro</font> -> Ficheiro "escondido"

---

Navegação II
============

1. Como é que eu crio um novo diretório (pasta)?
2. Como é que eu apago um novo diretório?
3. Como é que eu crio um novo ficheiro?
4. Como é que eu copio um ficheiro?
5. Como é que eu movo um ficheiro?
6. Como é que eu apago um ficheiro

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ mkdir dir_name``

``$ rmdir dir_name``

``$ touch file_name``

``$ cp origem destino``

``$ mv origem destino``

``$ rm file_name``

---

#<center>Intervalo!</center>

---

Permissões
==========

##Todos os ficheiros têm uma série de atributos.

``drwxr-xr-x  5 francisco francisco 4096 Oct 22 00:24 Desktop``

``drwxr-xr-x  3 francisco cobig2    4096 2013-05-20 13:55 Databases``

``-rw-r--r-- 1 francisco francisco 4256 Sep 15  2011 Zkill.py``

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

* user
* group
* others

##Valores

* <font color="red">r</font>ead (4)
* <font color="red">w</font>rite (2)
* e<font color="red">x</font>ecute (1)

``$ groups``

---

Permissões II
=============

##Ok, e como é que eu mudo isto?

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ chown user:group ficheiro``

``$ chmod mode ficheiro``

##Usamos as somas dos valores...

5 - read&execute (4+1)

6 - read&write (4+2)

7 - read,write&execute (4+2+1)

##... em trios de UGO (<font color="red">U</font>ser<font color="red">G</font>roup<font color="red">O</font>thers):

``777 ou 755 ou 640``

##Ou um valor "verbal"

``$ chmod +x ficheiro``

``$ chmod o-w ficheiro``

---

Variáveis de ambiente e  outros *goodies*
=========================================

##``env vars``

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

	!bash
	i="ola"
	echo $i
	echo $USER
	echo $HOME

##Aliases

	!bash
	alias ll=ls -l
	ll

##Para tornar permanente basta adicionar a ``~/.bashrc``

##Unix pipe ``|``

##Podemos "pipar" o resultado de um comando para outro

	!bash
	du -sm *
	du -sm *| sort -rk 2
	du -sm *| sort -n

##As possibilidades são ilimitadas!

---

$PATH
=====

##Correr programas

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

* É boa prática colocar os programas num localização no $PATH

``$ echo $PATH``

* /bin
* /usr/bin
* /usr/local/bin
* ~/bin

## E se o programa não estiver no $PATH?

``$ ~/cool_stuff/o_meu_programa``

##ou

``$ cd ~/cool_stuff``

``$ ./o_meu_programa``

---

$PATH II
========

##Como é que eu mudo isto?

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

##Lembram-se das ``env vars``?

``$ echo $PATH``

``$ PATH=$PATH:~/bin``

``$ echo $PATH``

##E para o tornar permanente?

##Sim, acrescenta-se ao ``~/.bashrc`` !

---

Mais sobre programas
====================

##Correr programas com argumentos

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ ls -l``

##Cada argumento é separado por um espaço

##Normalmente dá-se mais que um argumento

``$ cp origem destino``

##Exemplo de um argumento comum e extremamente importante

``$ cp --help``

##<font color="red">Mensagem a reter:</font> <font color="blue"> Os argumentos são separados por espaços e os espaços separam sempre argumentos!</font>

##E espaços em nomes de ficheiros? Como em "``ficheiro com espacos.fasta``".

##Os caracteres especiais têm de ser "escapados":

``$ cat ficheiro\ com\ espacos.fasta``

##Ou

``$ cat "ficheiro com espacos.fasta"``

---

Se estão a conseguir acompanhar até aqui - parabéns. Estão aptos a navegar a shell básica
=========================================================================================

---

Awesome starts here
====================

#Ferramentas mais avançadas.

## ``grep sed cat less vim nano git``

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

##Exemplos:

``$ cat ficheiro.fasta``

``$ grep ">" ficheiro.fasta``

``$ sed 's/>/+/g' ficheiro.fasta``

``$ less ficheiro.fasta``

##Usem a tecla "q" para sair do ``less``

##O ``vim`` dava sozinho para mais que uma so aula.

``$ nano ficheiro.fasta``

##O ``git`` sozinho dava para uma cadeira.
---

*Wildcards*
===========

##São caracteres especias que têm um significado diferente do seu "literal"

* "*" - qualquer caractere, qualquer número de vezes
* "?" - qualquer caractere, uma vez

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ ls D*``

``$ cp *.fasta outro/diretorio/qualquer``

---

*Redirects*
===========

##É usado para redirecionar o *output* de um programa para um ficheiro.

##Pode ser feito de várias formas, mas as mais simples são estas:

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

* ``$ ls -l > ficheiro.txt`` - cria um fichiero novo e escreve lá
* ``$ ls -l >> ficheiro.txt`` - começa a escrever no final do ficheiro

##É claro que podemos combinar diversas ferramentas para obter resultados interessantes...

* ``$ cat ficheiro.fasta | grep ">"  > nomes_das_sequencias.txt``

##Ou melhor ainda:

* ``$ cat ficheiro.fasta |grep ">" | sed 's/>//g' > nomes_das_sequencias2.txt``

##O primeiro a descobrir o que isto faz ganha uma bolacha!

---

Acesso remoto
=============

##Meet ``ssh``

##Significa "<font color="red">s</font>ecure <font color="red">sh</font>ell"

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ ssh user@machine``

##Isto vai abrir um nova shell na máquina a que se ligaram

##O ssh é um programa enorme, com inúmeras aplicações. Vejam a página do manual para terem uma ideia

</br>

#Meet ``scp``

##É como uma fusão do *ssh* com o *cp*

##Significa "<font color="red">s</font>ecure <font color="red">c</font>o<font color="red">p</font>y"

``$ scp user@machine:caminho/para/ficheiro caminho/local``

##Para uma solução mais completa, mas mais complexa, vejam o *rsync*

---

wget
====

##O wget é uma ferramenta para efetuar downloads via linha de comandos

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

##É extremamente útil num servidor remoto sem acesso a um browser

``$ wget http://exemplo.com/ficheiro_fixe.txt``

##Pode ser usado para descarregar a internet inteira!

##Uma alternativa popular é o ``curl``:

``$ wget http://odin.fc.ul.pt/bcg/exemplos/sequencias.fasta``

``$ curl http://odin.fc.ul.pt/bcg/exemplos/sequencias.fasta > sequencias.fasta``

---

Descomprimir ficheiros
======================

##.zip

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``$ unzip ficheiro.zip``

##.tar.gz

``$ tar xvfz ficheiro.tar.gz``

##.tar.bz2

``$ tar xvfj ficheiro.tar.bz2``

##Para outros formatos - o google é vosso amigo.

---

A vossa vez!
============

1. Descarregem sequencias do NCBI (ou gerem as vossas, como queiram)
2. Façam um BLASTX local no servidor odin.fc.ul.pt contra uma base de dados de proteínas (/home/databases/nr/)
3. Gerem o output HTML e abram-no no vosso browser

##username: alunos

##password: nitUkDagwi

* Tudo o que necessitam está nestes slides
* Usem o programa "blast2" (está instalado e acessivel no $PATH)
* Usem também o "BLAST++" (têm de o instalar localmente! Está no site do NCBI)
* A plataforma é GNU/Linux x86_64 (64bit)
* Leiam a documentação dos programas!
* Se não tiverem sequencias podem encontrar um exemplo aqui: https://dl.dropboxusercontent.com/u/929646/linux-shell-101/exemplos/sequencias.fasta

---

Ladies and gentleman - start your terminals!
============================================
