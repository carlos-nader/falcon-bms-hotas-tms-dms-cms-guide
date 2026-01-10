# Correção do Ambiente hotastable — section-C5-S3-blocks-and-variants

## Arquivo: section-C5-S3-blocks-and-variants-review-2026-01-10.tex

### Status Atual: 🔴 ORDEM B (Errada)

```latex
% ANTES (INCORRETO):
\caption{#1}\\

\rowcolor{headerblue}
\textbf{\color{white}State} & ... \\

\endhead              % ← AQUI PRIMEIRO (ERRADO)

\rowcolor{headerblue}
\textbf{\color{white}State} & ... \\

\endfirsthead         % ← DEPOIS (ERRADO)

\multicolumn{7}{r}{\small\emph{Continued on next page}}\\

\endfoot

\endlastfoot
```

---

## Correção: Inverter para ORDEM A (Correta)

### Localize Este Texto no Arquivo (por volta da linha 85–120):

```latex
% HOTAS table environment (per BRIEFING v0.2.0.1, Section 6)
% CORRECTED: [1] instead of [1][] to force caption requirement

\newenvironment{hotastable}[1]{%
  \small
  \renewcommand{\arraystretch}{1.25}
  \begin{longtable}{L{1.6cm} L{1.0cm} L{1.0cm} L{3.4cm} L{5.8cm} L{1.4cm} L{1.4cm}}
  \caption{#1}\\
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endhead                    % ← AQUI PRIMEIRO (ORDEM B — ERRADA)
  
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endfirsthead               % ← DEPOIS (ORDEM B — ERRADA)
  
  \multicolumn{7}{r}{\small\emph{Continued on next page}}\\
  \endfoot
  
  \endlastfoot
}{%
  \end{longtable}
}
```

### Substitua por Este Código (ORDEM A — Correto):

```latex
% HOTAS table environment (per BRIEFING v0.2.0.1, Section 6)
% CORRECTED: [1] instead of [1][] to force caption requirement
% CORRECTED v2: Header order follows official longtable standard (ORDEM A)

\newenvironment{hotastable}[1]{%
  \small
  \renewcommand{\arraystretch}{1.25}
  \begin{longtable}{L{1.6cm} L{1.0cm} L{1.0cm} L{3.4cm} L{5.8cm} L{1.4cm} L{1.4cm}}
  \caption{#1}\\
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endfirsthead                % ← MOVER PARA AQUI (após header primeira página)
  %
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endhead                     % ← MOVER PARA AQUI (após header demais páginas)
  %
  \multicolumn{7}{r}{\small\emph{Continued on next page}}\\
  \endfoot
  %
  \endlastfoot
}{%
  \end{longtable}
}
```

---

## Mudanças Específicas

| O Quê | Antes | Depois |
|-------|-------|--------|
| Após header primeira página | `\endhead` | ✅ `\endfirsthead` |
| Após header demais páginas | `\endfirsthead` | ✅ `\endhead` |
| Comentário | Sem nota v2 | ✅ Adiciona "v2: Header order" |

---

## Validação Pós-Correção

```bash
pdflatex section-C5-S3-blocks-and-variants-review-2026-01-10.tex
```

Confirme:
- ✅ Nenhum erro LaTeX
- ✅ Numeração de tabelas: "Table 1", "Table 2" (sequencial)
- ✅ Headers repetem corretamente em page breaks (se houver tabelas multi-página)

---

## Status Final

| Arquivo | Antes | Depois |
|---------|-------|--------|
| **section-C5-S3** | 🔴 ORDEM B | ✅ ORDEM A |

---

## Checklist Integração (Amanhã)

```
☐ Corrigiu ORDEM em section-C5-S3?
☐ Compilou sem erros?
☐ Numeração sequencial (Table 1, 2, ...)?
☐ Pronto para integrar no guide.tex com c5-s2?
```

Após esta correção:
- ✅ c5-s2 (já correto) = ORDEM A
- ✅ c5-s3 (agora corrigido) = ORDEM A
- ✅ guide.tex (em sua lista de correções) = ORDEM A
- ✅ template (em sua lista de correções) = ORDEM A
- ✅ briefing (em sua lista de correções) = especificação ORDEM A

**Tudo sincronizado! 🎯**
