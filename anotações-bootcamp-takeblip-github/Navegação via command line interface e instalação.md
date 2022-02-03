# Navegação via command line interface e instalação do Git

O Git é uma plataforma CLI, ou seja, todos os comandos são feitos através de uma linha de comando.

##### Diferenças entre plataformas GUI e CLI 

GUI (Graphic User Interface): tem uma interface gráfica que serve para guiar o usuário - gráfico e responsivo 

CLI (Command Line interface): não tem interface gráfica (Git), atua por linhas de comando. 

##### Instalação do Git

Link para download: https://git-scm.com/

Passo-a-passo da instalação:

1. Faça o download normalmente e execute o aplicativo;

2. Na aba "Select Components" deixe marcadas as opções:

   * Windows Explorer integration

   * Git Bash Here
   * Git GUI Here
   * Git LFS (Large File Support)
   * Associate .git* configuration files with default text editor
   * Associate .sh files to be run with Bash
   * Add a Git Bash Profile to Windows Terminal

3. Na aba Choosing the default editor used by Git escolha: use Vim (the ubiquitous text editor) as Git's default editor

4. Na aba Adjusting the name of the initial branch in new repositories escolha "Let Git decide"

5. Na aba Adjusting your PATH environment escolha "Git from command line and also from 3rd-party-software"

6. Na aba Choosing the SSH executable escolha "Use bundled OpenSSH"

7. Na aba Configuring the line ending conversions escolha "Checkout Windows-style, commit Unix-style line endings"

8. Na aba Configuring the terminal emulator to use with Git Bash escolha "Use MinTTY (the default terminal of MSYS2)"

9. Na aba Choose the default behavior of 'git pull' escolha "Default (fast-forward or merge)"

10. Na aba Choose a credential helper escolha "Git Credential Manager"

11. Na aba Configuring extra options escolha "Enable file system caching"

12. Na aba Configuring experimental options deixe ambas as opções em branco

13. Instale

14. Busque nos aplicativos do computador "Git Bash" e execute

15. No console do Git Bash execute o comando: git --version

16. Verifique a versão disponível no seu computador e valide a instalação do Git

##### Configurando o Git

Antes de qualquer coisa devemos configurar o básico do Git, então execute as seguintes linhas de comando:

1. git config --global user.name "Seu Nome"

​	Escolha o mesmo nickname usado no seu registro no GitHub, é importante que o nickname registrado no Git e no GitHub sejam iguais para não haver divergências entre as plataformas.

1. git config --global user.email "seuemail@exemplo.com"

​	Cadastre o e-mail registrado no GitHub para não haver divergências entre versões.