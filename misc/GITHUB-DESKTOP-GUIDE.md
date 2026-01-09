# GitHub Desktop Guide — Falcon BMS TMS/DMS/CMS Guide Repository

**Purpose:** Provide a simple, repeatable workflow for using **GitHub Desktop** with the Falcon BMS TMS/DMS/CMS HOTAS Usage Guide repository, focusing on governance documents (`docs/`), WIP files (`WIP/`), and the main guide source (`guide.tex` + versioned snapshots in `WIP/GUIDE/`).

---

## 1. Prerequisites

- A GitHub account with access to the repository.
- **GitHub Desktop** installed (latest stable version).
- Local LaTeX toolchain (for compiling the guide).
- Word or compatible editor (for `.docx` governance documents if needed).

Repository root structure (simplified):

```text
project-root/
├── guide.tex                        # Canonical main LaTeX source (tracked by Git)
├── WIP/
│   └── GUIDE/
│       ├── guide-v0.2.2.0-20260108.tex   # Current snapshot (example)
│       └── ...                           # Older snapshots and history
├── docs/                            # Governance and tracking documents (.md as source)
├── ARCHIVE/                         # Approved or deprecated WIP files and old guide versions
├── README.md                        # Project overview
└── md-to-docx-v2.9.6.bat            # Markdown → DOCX batch converter
```

**Key idea:**

- `guide.tex` (na raiz) é o arquivo **canônico** que o Git/GitHub acompanham ao longo do tempo.
- `WIP/GUIDE/guide-v...tex` são **snapshots versionados** (por número de versão + data) e servem como cópias de segurança e marco editorial.

---

## 2. Clonando e Atualizando o Repositório

### 2.1 Primeiro clone

1. Abra o **GitHub Desktop**.
2. Clique em **File → Clone Repository...**.
3. Selecione o repositório `carlos-nader/falcon-bms-hotas-tms-dms-cms-guide` na sua conta.
4. Escolha um caminho local (por exemplo `C:\Projects\falcon-bms-hotas-tms-dms-cms-guide`).
5. Clique em **Clone**.

### 2.2 Atualizações regulares (antes de trabalhar)

Antes de qualquer sessão de edição:

1. Abra o repositório no GitHub Desktop.
2. Confirme que a **branch atual** é `main` (ou outra branch de trabalho que você criou).
3. Clique em **Fetch origin**.
4. Se houver mudanças remotas, clique em **Pull origin**.

Isso garante que seus arquivos locais estão alinhados com o que está no GitHub.

---

## 3. Documentos de Governança (Markdown + DOCX)

Documentos de governança ficam em `docs/` e são mantidos principalmente como **Markdown** (`.md`). As versões `.docx` são geradas a partir dos `.md`.

### 3.1 Arquivos típicos em `docs/`

- `BRIEFING-v0-1-4-1.md` / `.docx`
- `version-system-v4-2.md` / `.docx`
- `WIP-FILE-NAMING-v1-3.md` / `.docx`
- `PROJECT-TRACKING-v4-1-2.md` / `.docx`
- `GITHUB-DESKTOP-GUIDE.md` / `.docx` (opcional)
- `PHASE-3-TECHNICAL-PLAN.md` / `.docx`
- `SESSION-8-PHASE-2-SUMMARY.md` / `.docx`

### 3.2 Fluxo de edição (governança)

1. **Pull origin** no GitHub Desktop.
2. Abra o `.md` relevante no seu editor preferido (por exemplo VS Code).
3. Edite o conteúdo (sempre em **inglês**, seguindo o BRIEFING).
4. Salve o `.md`.
5. Execute `md-to-docx-v2.9.6.bat` a partir da raiz do projeto.
   - O script gera/regera os `.docx` correspondentes em `docs/`.
6. Abra o `.docx` se quiser verificar rapidamente a formatação.

### 3.3 Commit de mudanças de governança

No GitHub Desktop:

1. Confirme que em **Changes** aparecem:
   - Os `.md` alterados em `docs/`.
   - Os `.docx` regenerados em `docs/`.
2. Revise o diff dos `.md` (são a fonte de verdade).
3. Escreva uma mensagem de commit descritiva, por exemplo:
   - `docs: update version-system to v4.2 (EN)`
   - `docs: add session 8 phase 2 summary`
4. Clique em **Commit to main** (ou na branch de trabalho).
5. Clique em **Push origin** para enviar ao GitHub.

---

## 4. Arquivos WIP (`WIP/`)

WIP files seguem as regras de **WIP-FILE-NAMING v1.3**, usando status no nome (`dev`, `review`, `final`, `approved`, `deprecated`).

### 4.1 Localização e tipos

- `WIP/section-*.tex` — conteúdo de seções em desenvolvimento.
- `WIP/table-*.tex` — tabelas HOTAS em desenvolvimento.
- `WIP/notes-*.md` — notas e rascunhos.
- `WIP/visual-*.*` — diagramas e figuras.
- `WIP/GUIDE/guide-v*.tex` — snapshots versionados do guia principal.

### 4.2 Fluxo básico com GitHub Desktop (WIP comum)

1. **Pull origin** antes de editar.
2. Edite os arquivos WIP necessários no seu editor (LaTeX, Markdown, etc.).
3. Se o status mudou (por exemplo `dev` → `review`), renomeie o arquivo seguindo WIP-FILE-NAMING.
4. De volta ao GitHub Desktop, confira os arquivos listados em **Changes**.
5. Faça commit com uma mensagem clara, por exemplo:
   - `wip: refine cms 5.2 tables (review)`
   - `wip: promote cms 5.1 section to final`
6. **Push origin**.

Importante: mudanças em WIP **não** mudam a versão do guia até serem integradas no snapshot e propagadas para `guide.tex`.

---

## 5. Editando o Guia Principal (`guide.tex` + snapshots em `WIP/GUIDE/`)

### 5.1 Conceito de snapshot vs arquivo canônico

- **Snapshots versionados**: `WIP/GUIDE/guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex`.
  - Contêm macros `\docversion` e `\docbuild` com a versão completa.
  - Servem como marcos editoriais e ponto de referência.

- **Arquivo canônico**: `guide.tex` (raiz do repositório).
  - Sempre deve ser byte-idêntico ao snapshot ativo.
  - É o arquivo que o Git/GitHub usam para diffs entre commits.

### 5.2 Fluxo seguro de edição do guia

1. **Pull origin**.
2. Localize o snapshot ativo em `WIP/GUIDE/`, por exemplo:

   ```text
   WIP/GUIDE/guide-v0.2.2.0-20260108.tex
   ```

3. Edite **apenas o snapshot** em `WIP/GUIDE/` (não edite `guide.tex` diretamente).
4. Atualize `\docversion` e `\docbuild` **somente se** a mudança exigir bump de versão, conforme `version-system-v4-2.md`.
5. Compile o snapshot com LaTeX para garantir que gera PDF sem erros.
6. Quando estiver satisfeito:
   - Copie o snapshot por cima de `guide.tex` na raiz, garantindo que fiquem idênticos.

   Por exemplo:

   - Abrir os dois arquivos no editor.
   - Substituir o conteúdo de `guide.tex` pelo do `guide-v...tex`.

7. Atualize `PROJECT-TRACKING` com a nova versão e breve descrição.

### 5.3 Commit de mudanças do guia

Depois de compilar e sincronizar snapshot → `guide.tex`:

1. No GitHub Desktop, revise **Changes**:
   - `guide.tex` modificado.
   - Snapshot novo/atualizado em `WIP/GUIDE/` (se houve mudança de versão ou data).
   - `PROJECT-TRACKING` atualizado.
2. Escreva uma mensagem de commit, por exemplo:
   - `guide: bump to v0.2.3.0 (cms 5.2 integration)`
3. **Commit** e depois **Push origin**.

Esse fluxo garante que o GitHub mostre diffs limpos em `guide.tex` ao longo da história.

---

## 6. Branches, Pull Requests e Reversão Simples

Se a branch `main` estiver protegida, o fluxo recomendado é:

### 6.1 Criar uma branch de trabalho (no GitHub Desktop)

1. No topo da janela, clique na lista de branches.
2. Selecione **New Branch...**.
3. Dê um nome descritivo, por exemplo: `feature/cms-5-2-tables`.
4. Confirme que ela será criada a partir de `main` e clique em **Create branch**.
5. Certifique-se de que a branch nova está selecionada.

### 6.2 Trabalhar normalmente nessa branch

- Siga os fluxos anteriores para:
  - editar WIP;
  - atualizar snapshot em `WIP/GUIDE/`;
  - copiar para `guide.tex`;
  - atualizar docs.
- Faça commits pequenos e descritivos.
- Quando terminar um conjunto de mudanças coerente, clique em **Push origin**.

### 6.3 Abrir Pull Request no GitHub (interface web)

1. Após dar **Push** da branch nova, abra o repositório no navegador.
2. O GitHub geralmente mostra um banner: “Compare & pull request”. Clique nele.
3. Confira que o PR é **de** `feature/...` **para** `main`.
4. Escreva um título e descrição breves.
5. Crie o Pull Request.

Na aba **Files changed**, você verá os diffs (linhas vermelhas/verde) em `guide.tex`, docs, etc.

Se algo estiver errado, basta **voltar para a branch no GitHub Desktop**, corrigir, commitar e dar outro **Push**: o PR é atualizado automaticamente.

### 6.4 Revisar e fazer merge do PR

Quando tudo estiver ok:

1. Na página do PR, clique em **Merge pull request**.
2. Confirme o merge.
3. Opcionalmente, apague a branch `feature/...` depois de mesclar.

Agora a `main` passa a conter aquelas mudanças.

### 6.5 Reverter um commit (GitHub Desktop, forma simples)

Se você perceber que **um commit específico** em `main` trouxe um problema:

1. No GitHub Desktop, vá em **History**.
2. Localize o commit problemático.
3. Clique com o botão direito nele e escolha **Revert this commit**.
4. O GitHub Desktop cria um **novo commit** que desfaz as mudanças daquele commit.
5. Clique em **Push origin**.

Isso não apaga o commit antigo (histórico continua intacto), mas volta o conteúdo ao estado anterior de forma segura.

---

## 7. Checklists de Sessão

### 7.1 Sessão só de governança (docs)

1. **Pull origin**.
2. Editar `.md` em `docs/`.
3. Rodar `md-to-docx-v2.9.6.bat`.
4. Conferir `.docx` se necessário.
5. Commit (`.md` + `.docx`) com mensagem clara.
6. **Push origin**.

### 7.2 Sessão de WIP (sem mexer no guia)

1. **Pull origin**.
2. Editar `WIP/section-*`, `WIP/table-*`, `WIP/notes-*`.
3. Ajustar nomes dos arquivos se o status mudar.
4. Commit WIP com mensagem clara.
5. **Push origin**.

### 7.3 Sessão de integração (nova versão do guia)

1. **Pull origin**.
2. Integrar conteúdo de `WIP/` no snapshot em `WIP/GUIDE/guide-v...tex`.
3. Decidir se há bump de versão (MINOR/PATCH/SUBPATCH) segundo `version-system-v4-2.md`.
4. Atualizar `\docversion`, `\docbuild` e, se necessário, o nome do snapshot.
5. Compilar o snapshot e confirmar que o PDF está ok.
6. Copiar o snapshot atualizado por cima de `guide.tex`.
7. Atualizar `PROJECT-TRACKING`.
8. Commit (`guide.tex` + snapshot + tracking) e **Push origin**.

Se estiver usando branch + PR:

9. Abrir PR para `main` e fazer merge quando estiver satisfeito.

---

## 8. Resolução de Problemas no GitHub Desktop

### 8.1 Merge conflicts

Se o GitHub Desktop reportar conflito:

1. Clique em **View conflicts**.
2. Abra os arquivos em conflito (por exemplo `.md` ou `.tex`) no seu editor.
3. Resolva manualmente os blocos `<<<<<<<`, `=======`, `>>>>>>>`.
4. Salve os arquivos.
5. Volte ao GitHub Desktop, marque os conflitos como resolvidos.
6. Commit de resolução e **Push origin**.

### 8.2 Commits acidentais com arquivos indesejados

Se um commit incluiu artefatos de build (por exemplo `.aux`, `.log`, `.synctex.gz`, `.pdf`):

1. Adicione esses padrões a `.gitignore`, por exemplo:

   ```text
   *.aux
   *.log
   *.synctex.gz
   *.pdf
   ```

2. Remova os arquivos já rastreados pelo Git, se necessário.
3. Faça um commit de limpeza.

---

## 9. Convenções e Boas Práticas

- Trate sempre `docs/*.md` como **fonte de verdade**; `.docx` é somente saída.
- Nunca edite `.docx` manualmente; sempre regenere a partir do `.md`.
- Mantenha commits **pequenos e descritivos**, especialmente quando mexer em `guide.tex`.
- Sempre faça **Pull** antes de começar a trabalhar e **Push** ao concluir um bloco lógico de trabalho.
- Para mudanças grandes no guia, prefira usar **branch de feature + Pull Request**, mesmo sendo single-author. Isso dá um lugar próprio para revisar diffs antes de afetar a `main`.
- Sincronize sempre três coisas quando houver nova versão do guia:
  - `\docversion` / `\docbuild` no LaTeX.
  - Nome do snapshot em `WIP/GUIDE/`.
  - Entrada correspondente em `PROJECT-TRACKING`.

Seguindo este guia, o repositório fica limpo, rastreável e alinhado com a governança definida, usando o GitHub Desktop como interface principal.
