# awesome-harness

Estrutura inicial de um marketplace de plugins para o GitHub Copilot CLI,
baseada no [awesome-harness-primitives](https://github.com/gbb-acelerators/awesome-harness-primitives).
Por enquanto, este repositório não contém agentes nem plugins.

## Estrutura

```text
.github/plugin/marketplace.json     # Catálogo do marketplace (vazio)
harness/github-copilot/plugins/     # Diretório reservado para futuros plugins
```

## Adicionar o marketplace

Com o GitHub Copilot CLI instalado, execute no terminal, a partir de qualquer
repositório:

```sh
copilot plugin marketplace add marcosoikawa/awesome-harness
copilot plugin marketplace browse awesome-harness
```

O marketplace pode ser registrado, mas o catálogo estará vazio até que plugins
sejam publicados.

## Instalar plugins futuramente

Depois que um plugin estiver disponível, em uma sessão interativa do Copilot:

```text
/plugin install <plugin-name>@awesome-harness
```

Substitua `<plugin-name>` pelo nome publicado no catálogo. O sufixo
`@awesome-harness` identifica o marketplace de origem.

## Publicar um plugin futuramente

1. Crie o plugin em `harness/github-copilot/plugins/<plugin-name>/`, com seu
   manifesto `plugin.json` e os componentes necessários.
2. Adicione uma entrada ao array `plugins` de `.github/plugin/marketplace.json`,
   com `name` e `source`. O caminho de `source` deve ser relativo à raiz do
   repositório: `./harness/github-copilot/plugins/<plugin-name>`.
3. Publique as alterações neste repositório. Quem já adicionou o marketplace
   poderá atualizar o catálogo com:

   ```sh
   copilot plugin marketplace update awesome-harness
   ```

Consulte a [referência oficial de plugins do Copilot CLI](https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-plugin-reference)
para os formatos dos manifestos e os comandos disponíveis.