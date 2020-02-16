# Geracao de chave ssh
Apos a geracao da chave ssh, sera possivel a realizacao desse tipo de autenticacao com algum servico, como o github.

## Neste artigo veremos

Geracao de nova chave SSH
Adicionando no SSH Agent
Adicionando chave no GitHub

Caso voce nao deseje informar a senha de sua chave SSH, sera necessario adicionar a chave no SSH agent, onde este gerencia e lembra o SO de sua respectiva senha.

# Geracao de nova chave SSH

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

> Generating public/private rsa key pair.
When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

> Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]
At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.
Start the ssh-agent in the background.

$ eval "$(ssh-agent -s)"
> Agent pid 59566
Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

$ ssh-add ~/.ssh/id_rsa
Add the SSH key to your GitHub account.
