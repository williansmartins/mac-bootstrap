# mac-bootstrap com MacPorts

Este repositório também inclui um [`Portfile.txt`](./Portfile.txt) para configurar um Mac usando MacPorts como alternativa ao Homebrew Bundle.

## O que este projeto faz

O [`Portfile.txt`](./Portfile.txt) lista pacotes que podem ser instalados via MacPorts. Atualmente, é um exemplo simples com a instalação do Node.js versão 22.

## Pré-requisitos

Antes de usar este arquivo, instale o MacPorts:

```bash
# Baixe e instale o MacPorts do site oficial: https://www.macports.org/install.php
# Ou via Homebrew (se já tiver):
brew install macports
```

Certifique-se de que o comando `port` esteja disponível:

```bash
port version
```

## Como usar

1. Clone este repositório (se ainda não fez):

```bash
git clone <url-do-repositorio>
cd mac-bootstrap
```

2. Edite o [`Portfile.txt`](./Portfile.txt) e adicione os pacotes que quiser instalar.

Exemplo de conteúdo:

```
install nodejs22
install git
install python311
```

3. Execute a instalação:

```bash
# Para instalar os pacotes listados:
sudo port -f < Portfile.txt
```

Ou manualmente:

```bash
port install nodejs22
```

## Estrutura atual

Exemplos de pacotes que podem ser adicionados:

- Desenvolvimento: `nodejs22`, `git`, `python311`, `ruby`
- Ferramentas: `wget`, `curl`, `vim`
- Banco de dados: `mysql8`, `postgresql14`

## Dicas

- Use `port installed` para ver o que já está instalado.
- Use `port uninstall <pacote>` para remover pacotes.
- Mantenha o `Portfile.txt` como referência para replicar o setup.

## Próximos passos

1. Adicione mais pacotes conforme necessário.
2. Organize em categorias comentadas, similar ao Brewfile.
3. Versione as mudanças para reaproveitar em outros Macs.