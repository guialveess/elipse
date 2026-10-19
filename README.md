# Elipse — tema para IntelliJ

Tema escuro minimalista para IntelliJ (UI inteira: painéis, botões, abas, menus
+ cores do editor/código), construído a partir do esquema oficial do
[Catppuccin Mocha para JetBrains](https://github.com/catppuccin/jetbrains)
(mesma base usada pelo plugin com +2M de downloads), recolorido para um visual
mais minimalista estilo Vercel (fundo neutro em cinza, sem o tom azulado do
Catppuccin original), com poucos acentos pastel bem marcados.

O nome brinca com a figura de linguagem: elipse é a omissão do óbvio para dizer
mais com menos — o espírito do tema (e também o nome da forma geométrica oval).

v2: paleta de fundo um pouco mais escura, hover e seleção da sidebar com mais
contraste entre si (pra não parecerem um bloco só quando ficam lado a lado).

v2.1: linha do cursor (`CARET_ROW_COLOR`) estava com a mesma cor do fundo —
corrigido. Breadcrumbs (`pacote > classe > método` abaixo das abas) agora usam
o roxo de destaque no item atual/hover, e um cinza mais apagado no que não é
o escopo ativo, em vez de tudo na mesma cor.

## Screenshots

![Classe de configuração Spring](screenshots/bean-configuration.png)
![Controller REST](screenshots/author-controller.png)

## Instalar (recomendado: plugin com UI + editor)

1. Abra o IntelliJ → `Settings/Preferences` → `Plugins`.
2. Clique na engrenagem ⚙️ no topo da lista → `Install Plugin from Disk...`.
3. Selecione o arquivo `elipse.jar` desta pasta.
4. Reinicie o IntelliJ quando ele pedir.
5. Vá em `Settings` → `Appearance & Behavior` → `Appearance` → dropdown `Theme`
   → escolha **"Elipse"**.
6. Confira também `Settings` → `Editor` → `Color Scheme`: esse dropdown é
   **separado** do Theme e não troca sozinho — selecione "Elipse" ali também.

Se você já tinha instalado uma versão antiga (`breve` / `Minimal Cappuccino`),
desinstale-a primeiro (`Plugins` → busque o nome → `Uninstall`), já que o id
interno muda a cada renomeação.

### Se "Synced with OS" estiver travando alguma coisa

Em `Settings` → `Editor` → `Color Scheme`, se o dropdown não deixar trocar,
clique em `Configure...` ao lado de "Synced with OS" e desative a sincronização
automática com o tema do sistema.

## Alternativa: só as cores do editor (sem mexer na UI)

Se preferir manter a UI padrão (Darcula) e só trocar a sintaxe do código:

1. `Settings` → `Editor` → `Color Scheme` → engrenagem ⚙️ → `Import Scheme...`
   → `IntelliJ IDEA color scheme (.icls)` → selecione `elipse.icls`.
2. Se o diálogo não aceitar o arquivo, copie-o manualmente para a pasta de
   esquemas do IDE e reinicie:
   ```
   ~/Library/Application Support/JetBrains/<Produto+Versão>/colors/
   ```
   Exemplo: `~/Library/Application Support/JetBrains/IntelliJIdea2025.3/colors/`
   (já deixei uma cópia lá pra você).

## Paleta usada (v2)

| Papel | Cor |
|---|---|
| Fundo (background) | `#1e1e21` |
| Painéis / mantle | `#18181b` |
| Toolbar / crust | `#141416` |
| Hover (sidebar) | `#212124` |
| Seleção (sidebar) | `#2c2c33` |
| Números de linha / comentário | `#4e4e57` / `#787882` |
| Texto padrão | `#e6e6ea` |
| Palavras-chave | `#b9a6f5` (violeta pastel) |
| Funções / métodos / accent principal | `#5ea8f2` (azul) |
| Strings | `#7fd88f` (verde menta) |
| Números / constantes | `#e8a87c` (pêssego) |
| Avisos / accent secundário | `#e8c170` (dourado suave) |
| Erros | `#f2777a` (coral) |

## Como ajustar

- **UI** (botões, painéis, abas): edite `elipse.theme.json`. A maior parte das
  chaves em `"ui"` referencia nomes simbólicos definidos em `"colors"`
  (ex.: `"accentColor"`, `"panelBackground"`) — mude ali que o resto segue junto.
- **Editor/código**: edite `elipse.icls` (XML). Tem `parent_scheme="Darcula"`,
  ou seja, qualquer atributo não sobrescrito cai de volta no Darcula padrão — por
  isso não existe risco de elemento "sem cor".
- Depois de editar, reempacote em `.jar` (é só um zip de `META-INF/plugin.xml` +
  `themes/*.json` + `themes/*.xml`, com o `.xml` do editor salvo dentro do jar
  como `themes/elipse.xml`) ou peça pra eu regenerar.

## Arquivos nesta pasta

| Arquivo | Para quê |
|---|---|
| `elipse.jar` | Plugin completo (UI + editor) — instalar via "Install Plugin from Disk" |
| `elipse.icls` | Só o esquema do editor — instalar via "Import Scheme" |
| `elipse.theme.json` | Fonte do tema de UI, editável (também embutido no jar) |
| `_referencia-catppuccin-mocha.xml` / `_referencia-catppuccin-macchiato.xml` | Catppuccin original, sem alterações — só referência/comparação |
