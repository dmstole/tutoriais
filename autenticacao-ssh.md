# Geracao de chave ssh
Apos a geracao da chave ssh, sera possivel a realizacao desse tipo de autenticacao com algum servico, como o github.

## Neste artigo veremos

Geracao de nova chave SSH
Adicionando no SSH Agent
Adicionando chave no GitHub

Caso voce nao deseje informar a senha de sua chave SSH, sera necessario adicionar a chave no SSH agent, onde este gerencia e lembra o SO de sua respectiva senha.

## Geracao de nova chave SSH

Abra um terminal

Acesse sua pasta principal
```
$ cd ~/.
```

Verifique se existe a pasta *.ssh*. Caso nao, crie essa pasta.
```
$ ls -l
$ mkdir .ssh
```

Cole o comando abaixo e substitua o email pelo utilizado no GitHub
```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Esta comando vai criar uma nova chave utilizando o email como nome da chave.

Informe um nome da chave caso necessite a geracao de novas chaves. Por padrao nao iremos informar um tipo de  secure passphrase.
> Enter a file in which to save the key (/home/you/.ssh/id_rsa): <nome_chave> [Pressione o Enter]

> Enter passphrase (empty for no passphrase): [Pressione o Enter]

> Enter same passphrase again: [Pressione o Enter]

## Adicionando sua chave SSH no ssh-agent

Inicie o ssh-agent.
```
$ eval "$(ssh-agent -s)"
```
> Agent pid 59566

Adicione a chave privada no ssh-agent.
```
$ ssh-add ~/.ssh/<nome_chave - exemplo: id_rsa_github>
```
