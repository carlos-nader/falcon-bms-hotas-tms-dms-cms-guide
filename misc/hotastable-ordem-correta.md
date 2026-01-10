# Configuração Correta do Ambiente hotastable — ORDEM A

## PADRÃO OFICIAL (Numeração Sequencial Correta)

Use esta configuração em **template-wip-V1.0.tex** e **guide.tex**:

---

## Código Exato para template-wip-V1.0.tex

```latex
% HOTAS table environment (Briefing v0.2.0.1, Section 6)
% ORDEM CORRETA: \endfirsthead APÓS header primeira página

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
  \endfirsthead
  %
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endhead
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

## Código Exato para guide.tex

```latex
% HOTAS table environment
% CORRECTED: ORDEM A — \endfirsthead APÓS header primeira página
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
  \endfirsthead
  %
  \rowcolor{headerblue}
  \textbf{\color{white}State} &
  \textbf{\color{white}Dir} &
  \textbf{\color{white}Act} &
  \textbf{\color{white}Function} &
  \textbf{\color{white}Effect / Nuance} &
  \textbf{\color{white}Dash34} &
  \textbf{\color{white}Train} \\
  \endhead
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

## Status de Conformidade Após Atualização

| Arquivo | Antes | Depois |
|---------|-------|--------|
| template-wip-V1.0.tex | 🔴 Ordem B (errada) | ✅ Ordem A (correta) |
| guide.tex | 🔴 Ordem B (errada) | ✅ Ordem A (correta) |
| c5-s2*.tex | ✅ Ordem A (correto) | ✅ Mantém Ordem A |

---

## Verificação Pós-Atualização

Após atualizar, compile cada arquivo:

```bash
# Template (standalone)
pdflatex template-wip-V1.0.tex

# Guide (master)
pdflatex guide.tex

# WIP (standalone, sem mudança)
pdflatex section-C5-S2-cms-actuation-hotas-table-final-2026-01-10.tex
```

Confirme:
- ✅ Numeração de tabelas: Table 1, Table 2, ... (sequencial)
- ✅ Headers repetem corretamente em page breaks
- ✅ "Continued on next page" aparece em tabelas multi-página

---

## Por Que Esta Ordem?

**ORDEM A:**
```
header (página 1)
\endfirsthead    ← Marca FIM do header página 1
header (páginas 2+)
\endhead         ← Marca FIM do header páginas 2+
```

- ✅ Padrão oficial da documentação `longtable`
- ✅ Semanticamente lógico (primeira → depois)
- ✅ Menor risco de bugs em edge cases

---

## Checklist Final

- [ ] Copiei código exato para template-wip-V1.0.tex?
- [ ] Copiei código exato para guide.tex?
- [ ] c5-s2*.tex permanece inalterado?
- [ ] Compilei cada arquivo para validar?
- [ ] Numeração de tabelas é sequencial?
- [ ] Pronto para integração amanhã?
