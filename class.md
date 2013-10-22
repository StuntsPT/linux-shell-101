Linux shell 101
===============

![454](assets/linux.jpg)

##<center>Francisco Pina Martins</center>
###<center>24/10/2013</center>

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
* Acesso remoto simples
* Interface **simples**
* Pode parecer que não, mas facilita imenso

##Não acreditam? Vejam.

---

#O *prompt*

``user@machine:~$``

![Prompt image](assets/shell_prompt.gif)

---

#Navegação e orientação

##Pensem na vossa shell como um gestor de ficheiros

1. Onde é que eu estou?
2. O que é que há aqui?
3. Como é que me movimento?

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``pwd``

``ls``

``cd``

##Significado:

1. <font color="red">p</font>rint <font color="red">w</font>orking <font color="red">d</font>irectory
2. <font color="red">l</font>i<font color="red">s</font>t
3. <font color="red">c</font>all <font color="red">d</font>irectory

---

#O vossos novos melhores amigos

``man nome_do_programa``

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

* **TODOS** os programas *builtin* na shell (coreutils) têm um
* Alguns outros também

``man ls``

``whatis``

<div style="float: right"><img src="assets/Tab-Key.png" /></div>
##Tecla "Tab"

* Completa o que estão a escrever
* Com uma ou duas "*keypress*"

##Teclas ↓ e ↑

* Navegam pela lista de comandos anteriores

---

#Caminhos (path) e convenções

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

#Navegação II

1. Como é que eu crio um novo diretório (pasta)?
2. Como é que eu apago um novo diretório?
3. Como é que eu crio um novo ficheiro?
4. Como é que eu copio um ficheiro?
5. Como é que eu movo um ficheiro?
6. Como é que eu apago um ficheiro

<div style="float: right"><img src="assets/shell_prompt_small.gif" /></div>

``mkdir dir_name``

``rmdir dir_name``

``touch file_name``

``cp origem destino``

``mv origem destino``

``rm file_name``

---

#<center>Intervalo!</center>

---

#Permissões