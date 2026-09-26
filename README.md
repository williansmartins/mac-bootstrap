# Configurar GitHub via SSH no macOS

Este guia configura o GitHub via SSH no Mac para que comandos como git clone, git pull e git push não fiquem pedindo usuário, senha ou token.

## 1. Verificar se já existe uma chave SSH

Abra o Terminal e execute:

    ls -al ~/.ssh

Procure por arquivos como:

    id_ed25519
    id_ed25519.pub

Se eles existirem, provavelmente você já possui uma chave SSH.

---

## 2. Criar uma nova chave SSH

Se você ainda não tiver uma chave:

    ssh-keygen -t ed25519 -C "seu-email-do-github"

Quando aparecer:

    Enter file in which to save the key:

pressione Enter para usar o local padrão:

    ~/.ssh/id_ed25519

Quando pedir uma passphrase, é recomendado definir uma senha para proteger a chave.

---

## 3. Iniciar o SSH Agent

Execute:

    eval "$(ssh-agent -s)"

Depois adicione sua chave ao Keychain do macOS:

    ssh-add --apple-use-keychain ~/.ssh/id_ed25519

Isso permite que o macOS armazene a passphrase no Keychain, evitando que você precise digitá-la repetidamente.

---

## 4. Configurar o SSH para o GitHub

Crie ou edite:

    nano ~/.ssh/config

Adicione:

    Host github.com
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_ed25519

Salve com:

    Ctrl + O

Pressione Enter.

Depois saia com:

    Ctrl + X

---

## 5. Copiar a chave pública

Execute:

    pbcopy < ~/.ssh/id_ed25519.pub

A chave pública agora está copiada para o clipboard.

IMPORTANTE: nunca compartilhe o conteúdo de ~/.ssh/id_ed25519.

A chave privada deve permanecer somente no seu Mac.

A chave que termina em .pub é a que deve ser adicionada ao GitHub.

---

## 6. Adicionar a chave ao GitHub

No GitHub:

1. Abra Settings
2. Vá para SSH and GPG keys
3. Clique em New SSH key
4. Em Title, coloque algo como:

    MacBook

5. Cole a chave copiada no campo Key
6. Confirme

---

## 7. Testar a conexão

No Terminal:

    ssh -T git@github.com

Na primeira conexão, pode aparecer:

    Are you sure you want to continue connecting (yes/no/[fingerprint])?

Digite:

    yes

Se estiver funcionando, o GitHub deverá responder informando que a autenticação foi realizada.

---

