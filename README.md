# mac-bootstrap

Bootstrap simples para configurar um Mac com `Homebrew Bundle`.

## O que este projeto faz

Este repositório usa um [`Brewfile`](./Brewfile) para listar apps, ferramentas e utilitários que podem ser instalados de uma vez no macOS.

Hoje o arquivo está organizado em categorias como:

- Apps principais
- Ferramentas de desenvolvimento
- Banco de dados
- Extras úteis

Os itens estão comentados, então você pode ativar apenas o que fizer sentido para o seu setup.

## Pré-requisitos

Antes de usar este projeto, instale o Homebrew:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Depois, garanta que o `brew bundle` esteja disponível:

```bash
brew tap homebrew/bundle
```

## Como usar

1. Clone este repositório:

```bash
git clone <url-do-repositorio>
cd mac-bootstrap
```

2. Edite o [`Brewfile`](./Brewfile) e descomente os pacotes que quiser instalar.

Exemplo:

```ruby
cask "google-chrome"
brew "git"
brew "node"
```

3. Execute a instalação:

```bash
brew bundle --file=Brewfile
```

## Estrutura atual

Exemplos de itens já previstos no `Brewfile`:

- Navegadores: `google-chrome`, `microsoft-edge`
- Editores e produtividade: `visual-studio-code`, `iterm2`, `slack`, `zoom`, `rectangle`
- Ferramentas: `git`, `wget`, `node`, `python`
- Banco de dados: `mysql`
- Extras: `docker`, `postman`, `macs-fan-control`

## Dicas

- Use `brew bundle check --file=Brewfile` para verificar o que já está instalado.
- Use `brew bundle cleanup --file=Brewfile` para remover itens que não estão mais listados.
- Mantenha o `Brewfile` como a fonte da verdade do seu ambiente.

## Próximos passos

Se quiser evoluir este repositório, uma boa sequência é:

1. Descomentar os pacotes realmente usados no seu dia a dia.
2. Adicionar novas categorias, como `fonts`, `devops` ou `mobile`.
3. Versionar mudanças no `Brewfile` para reaproveitar o setup em outros Macs.
