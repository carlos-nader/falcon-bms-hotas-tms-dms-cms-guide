# Correções Necessárias no Brief v0.2.0.1

## Arquivo: briefing-v0.2.0.1.md

Localize e aplique as seguintes correções para sincronizar com ORDEM A (padrão oficial longtable).

---

## CORREÇÃO 1: Section 3.3 — Add Note About hotastable

### Localizar Este Texto (seção 3.3):

```
### 3.3 LaTeX Preamble (Assumed)

The LaTeX preamble already includes, among others:... - Fonts, geometry, microtype.
- Clickable TOC and PDF bookmarks.
- Headers/footers via `fancyhdr`.
- Custom `hotastable` environment with columns (updated v0.1.3):
  - State (1.6 cm), Direction (1.0 cm), Action (1.0 cm), Function (3.4 cm), Effect / Nuance (5.8 cm), Dash34 (1.4 cm), Train (1.4 cm).
- Helper macros: `\\dashref{}`, `\\dashone{}`, `\\trnref{}`, `\\trnman`, `\\bmsver`, `\\dashrefs{}`.
- `graphicx` with `fig/` as the figures folder.
```

### Substituir Por:

```
### 3.3 LaTeX Preamble (Assumed)

The LaTeX preamble already includes, among others:

- Fonts, geometry, microtype.
- Clickable TOC and PDF bookmarks.
- Headers/footers via `fancyhdr`.
- Custom `hotastable` environment with columns (updated v0.1.3):
  - State (1.6 cm), Direction (1.0 cm), Action (1.0 cm), Function (3.4 cm), Effect / Nuance (5.8 cm), Dash34 (1.4 cm), Train (1.4 cm).
  - Header structure: First-page header, then `\endfirsthead`; subsequent-pages header (identical), then `\endhead`. This order ensures correct table numbering across page breaks (see Section 11.5).
- Helper macros: `\\dashref{}`, `\\dashone{}`, `\\trnref{}`, `\\trnman`, `\\bmsver`, `\\dashrefs{}`.
- `graphicx` with `fig/` as the figures folder.
```

---

## CORREÇÃO 2: Section 11.5 — Add Subsection "Header Order (LOCKED)"

### Localizar Este Texto (Section 11.5):

```
### 11.5 hotastable Environment (Frozen Specification)

The `hotastable` environment is **architecture-locked**: column widths, font size, and row height are fixed and must not be modified without explicit brief revision.

**Column configuration (EXACT, locked):**

```latex
\newenvironment{hotastable}[1]{\
  ...
}
```

**Column semantics (locked, per Section 6):**
...
**Font and spacing (locked):**

```latex
{\\small
\\arraystretch=1.25
... table content ...
}
```

- `\\small` (10 pt) is the baseline for all HOTAS tables; deviation requires brief amendment.
- `\\arraystretch = 1.25` is locked; changes require brief amendment and validation against page economy.

**Why this is frozen:**
- Column widths are designed to fit exactly 15.6 cm within the 17.0 cm text width (see Section 4.1).
- Deviations would either break page layout or sacrifice content legibility.
- `\\small` + `\\arraystretch = 1.25` is optimised for dense technical tables; empirically validated.
```

### Após "**Why this is frozen:**", Adicionar Este Novo Subsection:

```
**Header Order (LOCKED):**

The `hotastable` environment MUST follow this exact sequence for header and footer management. This order is mandated by official `longtable` documentation and ensures correct table numbering and page break behavior.

The **correct sequence** is:

```latex
\begin{longtable}{L{1.6cm} L{1.0cm} L{1.0cm} L{3.4cm} L{5.8cm} L{1.4cm} L{1.4cm}}
\caption{#1}\\
%
\rowcolor{headerblue}
\textbf{\color{white}State} &
\textbf{\color{white}Dir} &
\textbf{\color{white}Act} &
\textbf{\color{white}Function} &
\textbf{\color{white}Effect / Nuance} &
\textbf{\color{white}Dash34} &
\textbf{\color{white}Train} \\
\endfirsthead              % Marks end of first-page header
%
\rowcolor{headerblue}
\textbf{\color{white}State} &
\textbf{\color{white}Dir} &
\textbf{\color{white}Act} &
\textbf{\color{white}Function} &
\textbf{\color{white}Effect / Nuance} &
\textbf{\color{white}Dash34} &
\textbf{\color{white}Train} \\
\endhead                   % Marks end of subsequent-pages header
%
\multicolumn{7}{r}{\small\emph{Continued on next page}}\\
\endfoot
%
\endlastfoot
\end{longtable}
```

**Critical ordering rules:**

1. `\caption{}\\` must come FIRST (inside `longtable`, not before)
2. First-page header content follows immediately after
3. `\endfirsthead` MUST mark the END of first-page header (not the beginning)
4. Subsequent-pages header content (identical to first-page) follows
5. `\endhead` MUST mark the END of subsequent-pages header
6. Footer material (`\multicolumn`, `\endfoot`, `\endlastfoot`) follows

**Rationale:**

- This order follows the official `longtable` documentation convention
- It ensures LaTeX correctly distinguishes first-page headers from subsequent-page headers
- It guarantees correct table numbering (Table 1, Table 2, etc.) across page breaks
- The semantic meaning is: "define first-page header, THEN mark it as finished, THEN define subsequent pages, THEN mark those as finished"
- Reversing the order (placing `\endhead` before `\endfirsthead`) is non-standard and may cause unpredictable behavior in edge cases

**Enforcement:**

All WIP files created from `template-wip-V1.0.tex` must inherit this exact order. Integration of WIP content into `guide.tex` must verify that this order is preserved. Deviations require explicit justification and amendment to this brief.
```

---

## CORREÇÃO 3: Section 11.6 — Update Template Example (if present)

### Localizar Esta Seção (11.6):

If Section 11.6 contains a code example showing hotastable, ensure it uses ORDEM A:

```latex
% BEFORE (WRONG):
\endhead
...
\endfirsthead

% AFTER (CORRECT):
\endfirsthead
...
\endhead
```

---

## CORREÇÃO 4: Update Section 11.8 (Optional But Recommended)

### Localizar Esta Seção (11.8 — Template Versioning and Maintenance):

Adicionar nota:

```
**Hot Fix Note (v0.2.0.1 → v0.2.0.2):**

Version v0.2.0.1 of this briefing contained an ambiguity in Section 11.5 regarding 
the correct order of \endfirsthead and \endhead in the hotastable environment. 

This has been clarified in Section 11.5 (new subsection "Header Order (LOCKED)") 
to specify the official order required by longtable documentation.

All WIP templates and the master guide (guide.tex) have been updated to conform 
to this specification as of 2026-01-10.
```

---

## SUMMARY: Onde Fazer As Mudanças

| Seção | Ação | Tipo |
|-------|------|------|
| 3.3 | Adicionar nota sobre header order | Clarificação |
| 11.5 | Adicionar subsection "Header Order (LOCKED)" | Nova seção |
| 11.6 | Verificar e corrigir exemplos (se existirem) | Validação |
| 11.8 | Adicionar nota sobre v0.2.0.1 → v0.2.0.2 | Versionamento |

---

## Versionamento do Brief

### Opção A: Patch Version (Recomendado)

```
Atual:  briefing-v0.2.0.1.md
Novo:   briefing-v0.2.0.2.md
Motivo: Clarificação de ambiguidade existente (não novo conteúdo)
```

### Opção B: Minor Version

```
Atual:  briefing-v0.2.0.1.md
Novo:   briefing-v0.2.1.0.md
Motivo: Adição de especificação completa (entidade nova: "Header Order LOCKED")
```

**Recomendação**: Use Opção A (v0.2.0.2) — é correção de ambiguidade, não nova funcionalidade.

---

## Procedimento de Atualização

1. ✅ Abra `briefing-v0.2.0.1.md`
2. ✅ Aplique CORREÇÃO 1 em Section 3.3
3. ✅ Aplique CORREÇÃO 2 em Section 11.5 (novo subsection)
4. ✅ Aplique CORREÇÃO 3 em Section 11.6 (se necessário)
5. ✅ Aplique CORREÇÃO 4 em Section 11.8 (opcional)
6. ✅ Salve como `briefing-v0.2.0.2.md` (ou v0.2.1.0.md)
7. ✅ Atualize referências em guide.tex e template-wip-V1.0.tex para referenciar v0.2.0.2

---

## Validação Pós-Atualização

Após atualizar o briefing:

```
☐ Section 3.3 menciona ordem de \endfirsthead/\endhead?
☐ Section 11.5 contém novo subsection "Header Order (LOCKED)"?
☐ Código de exemplo em 11.5 usa \endfirsthead → \endhead (ORDEM A)?
☐ Rationale explain por que esta ordem é correta?
☐ Nova versão documentada em 11.8?
☐ Briefing é agora fonte de verdade única para hotastable?
```

---

## Resultado Final

Após estas correções:

✅ Brief é source of truth único  
✅ template-wip-V1.0.tex pode referenciar briefing com confiança  
✅ guide.tex está sincronizado com brief  
✅ c5-s2*.tex segue brief  
✅ Próximos WIPs herdam ordem correta automaticamente  
✅ Ambiguidades eliminadas  
✅ Documentação architecture-locked e confiável
