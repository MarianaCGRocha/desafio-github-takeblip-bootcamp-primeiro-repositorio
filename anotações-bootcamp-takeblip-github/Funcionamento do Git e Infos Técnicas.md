# Entendendo como o Git funciona por baixo dos panos

#### Tópicos fundamentais para entender o funcionamento do Git

##### O que é SHA1 e qual sua importância?

SHA1 (Secure Hash Algorithm) é um conjunto de funções hash criptográficas projetadas pela NSA (Agência de Segurança Nacional dos EUA). Esse sistema de encriptação gera um conjunto de 40 dígitos codificados único que é a identificação exclusiva da versão do seu código.

##### Objetos Fundamentais:

* Blobs: armazena metadados de um objeto (tipo de objeto, tamanho da String, etc.). Os Blobs tem o SHA1 igual ao do arquivo que é dono dos dados neles armazenados.
* Trees: armazenam Blobs e, também, os nomes dos arquivos. Monta a estrutura de onde estão localizados os arquivos. Também pode apontar para outras árvores (Trees), ou seja, organiza outras árvores. As árvores tem um SHA1 próprio.
* Commits: objeto que aponta para: uma Tree, Parente, Autor, Mensagem e tem TimeStamp. O SHA1 de um commité o hash de todas essas informações.

Isso significa que quando altera um dado dentro de um Blob que está dentro de uma árvore inserida em um commit, toda a cadeia de SHA1 será alterada. Ou seja, todas alterações são rastreadas, impedindo assim ações maliciosas ou incompatibilidade de versão de código.

##### Chaves SSH e Token

Quando você vai passar seu código pro GitHub é necessário que sua identidade esteja validada para evitar a ação de pessoas com intenções maliciosas e alterações indevidas. Para que essa autenticação seja feita usamos uma chave de acesso criptografada chamada chave SSH.

A chave SSH certifica que existe uma conexão segura e rastreável entre duas máquinas. Dessa forma quando você solicita a geração dessa chave para o Git, ele fornecerá duas versões:

* Chave Pública: que você deverá inserir na plataforma (GitHub) para validar sua chave de acesso ao servidor.

* Chave Privada: chave de acesso fornecida ao agent no Git para que ele criptografe as mensagens enviadas ao servidor e também traduza as recebidas.

##### Passo-a-Passo para geração, validação e inserção da chave SSH

###### Geração da Chave SSH

1. No Git Bash você deve inserir o código: ssh-keygen -t ed25519 -C "seuemail@exemplo.com"
2. O Git Bash retornará duas chaves, uma privada e uma pública (.pub) e o local onde as chaves estão salvas na máquina
3. Use o código para acessar sua chave: cat id_ed"insira o código de chave pública aqui".pub
4. Copiar o código exibido e inserir no GitHub no campo de Chave SSH

###### Ativação da Chave SSH

1. Use o código no Git Bash: eval$(ssh-agent -s)

   Esse código vai fornecer um agent pid, que é o projeto rodando em segundo plano e validando todas as versões do código, monitorando todas as alterações do mesmo.

2. Use o código: add id_ed"insira aqui o código de chave privado"

   Esse código fornece ao agent a chave para descriptografar as mensagens vindas do GitHub e, também, criptografar aquelas que são enviadas à plataforma.

##### Ciclo de Vida dos arquivos no Git

Os arquivos no Git podem, primeiramente, ser classificados em:

1. Untracked: Aqueles arquivos que não foram adicionados ao Git, então ele sequer sabe da existência deles.

2. Tracked: arquivos que estão sendo rastreados pelo Git e podem ser divididos em 3 fases:

   1. Unmodified: arquivos não alterados, ou seja, sua máquina e a plataforma tem a mesma versão desses arquivos. Esses arquivos estão esperando por modificações para que se tornem "modified".
   2. Modified: arquivos que foram modificados/editados, mas que ainda não foram salvos. Estão esperando o comando <git add *> para serem adicionados.
   3. Staged: Arquivos que já foram commitados e, após isso, retornam ao estágio de Unmodified.

   