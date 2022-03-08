---
title: "Criando chaves SSH ED25519"
author: "ramonrwx"
description: "As chaves SSH fornecem uma maneira fácil e segura de fazer login
no seu servidor e são recomendadas para todos os usuários."
date: "2022-02-18"
slug: criando-chaves-ssh-ed25519
cover: images/ssh.png
categories: [linux]
tags: [segurança, ssh, ed25519]
hideReadMore: true
output: html_document
---

### O que são chaves SSH?

O SSH (Secure Shell), também conhecido como Secure Socket Shell, é um protocolo
que permite a conexão com servidores remotos, de forma criptografada e mais
segura, usando um par de chaves.

### Criando uma chave SSH

1. Você deve ter instalado o `openssh` na sua máquina.

```sh
sudo apt install openssh
```

2. digite o seguinte comando para gerar uma chave SSH que usa o algoritmo
   Ed25519:

```sh
ssh-keygen -o -a 100 -t ed25519 -f ~/.ssh/id_ed25519 -C "ramon@example.com"
```

Será solicitado a inserir uma senha para esta chave, use uma senha forte.

- `-o` Salva a private-key usando o novo formato OpenSSH em vez do formato PEM.
- `-a` São os números das rodadas KDF (Key Derivation Function). Números mais
  altos resultam em verificação mais lenta da senha.
- `-t` Especifica o tipo de chave que será criar, no nosso caso o Ed25519.
- `-f` Especifique o nome do arquivo do arquivo gerado.
- `-C` Uma opção para especificar um comentário. É puramente informativo e pode
  ser qualquer coisa.

### Adicionando sua chave ao agente SSH
Você pode encontrar sua chave privada recém-gerada em `~/.ssh/id_ed25519` e sua
chave pública em `~/.ssh/id_ed25519.pub`.

Antes de adicionar sua chave privada ao agente SSH, certifique-se de que o
agente SSH esteja ativo com o comando:

```sh
eval "$(ssh-agent -s)"
```

Em seguida, execute o seguinte comando para adicionar sua nova chave Ed25519 ao
agente SSH:

```sh
ssh-add ~/.ssh/id_ed25519
```

É isso ai. :heart:
