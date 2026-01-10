# Section Numbering Strategy for the TMS/DMS/CMS Guide

This note summarises options and trade-offs for LaTeX section numbering depth in the guide, focusing on how to handle deeper levels such as CMS MAN/AUTO/SEMI and ECM variants.

The goal is to pick a strategy that:

- Stays compatible with the existing **Briefing v0.2.0.1** chapter breakdown.
- Respects LaTeX best practices for technical manuals.
- Optionally aligns with the **Falcon BMS Dash-34** style, which often uses deeper numeric hierarchies.

---

## 1. Current Situation

### 1.1 Logical structure from the Briefing

For Chapter 5 (CMS), the Briefing defines the following hierarchy:

- 5 CMS — Countermeasures Management Switch  
  - 5.1 Concept and interaction with CMDS / ECM  
    - 5.1.1 Concept  
    - 5.1.2 Interaction with CMDS / ECM  
  - 5.2 CMS Switch Actuation — main table in subsections using `hotastable`  
    - 5.2.1 CMS Actuation with CMDS  
    - 5.2.2 CMS Actuation with ECM  
    - 5.2.3 CMS Consent & Constraints  
    - 5.2.4 Important Operational Notes  
  - 5.3 CMS — Block and variant notes

This maps naturally to LaTeX levels in `article` class:

- 5.x → `\section`
- 5.x.y → `\subsection`
- 5.x.y.z → `\subsubsection`

The Briefing does **not** define any further depth under 5.2.x (no 5.2.1.1 etc. are mandated).

### 1.2 How C5-S2 is currently implemented (guide-v0.2.3.1)

In `guide-v0.2.3.1-20260110.tex`, Section 5.2 is implemented as:

- `\subsection{CMS Switch Actuation}` → 5.2
  - `\subsubsection{CMS Actuation with CMDS}` → 5.2.1
    - `\paragraph{Manual Mode}`
    - `\paragraph{Automatic Mode}`
    - `\paragraph{Semi-Automatic Mode}`
  - `\subsubsection{CMS Actuation with ECM}` → 5.2.2
    - `\paragraph{External ECM Pod (ALQ-131 / ALQ-184)}`
    - `\paragraph{Internal ECM (IDIAS)}`
  - `\subsubsection{CMS Consent and Constraints}` → 5.2.3
  - `\subsubsection{Important Operational Notes}` → 5.2.4
    - `\paragraph*{Consent State Tracking}` etc.

Given that the default `secnumdepth` for `article` is 3:

- `\section`, `\subsection`, `\subsubsection` are numbered (5, 5.2, 5.2.1, 5.2.2, ...).
- `\paragraph` / `\paragraph*` are **not** numbered and do not appear in the ToC.

So today:

- The document complies exactly with the Briefing’s required depth (up to 5.2.4).  
- Modes (MAN/AUTO/SEMI, ECM pod/IDIAS) are clearly visible titles, but **not** numbered items.

---

## 2. What Happens If We "Promote" Modes to Subsubsections?

A naive idea is to turn modes into additional `\subsubsection`s, for example:

```latex
\subsection{CMS Switch Actuation} % 5.2
  \subsubsection{CMS Actuation with CMDS} % 5.2.1
  \subsubsection{Manual Mode}           % 5.2.2 (not 5.2.1.1!)
  \subsubsection{Automatic Mode}        % 5.2.3
  \subsubsection{Semi-Automatic Mode}   % 5.2.4
```

This is **not** what we want:

- LaTeX does not nest `\subsubsection` under `\subsubsection` numerically; each `\subsubsection` is just the next 5.2.x in sequence.
- "Manual Mode" passaria a ser 5.2.2, roubando o lugar de "CMS Actuation with ECM".
- A numeração deixaria de refletir a estrutura lógica do Briefing (5.2.1 como grupo CMDS e 5.2.1.1 como modo MAN), e sim apenas uma lista linear de `\subsubsection`s.

Por isso, **promover modos a `\subsubsection` não é adequado**: quebra a hierarquia planejada e gera numeração "bagunçada".

---

## 3. Opção A — Manter `secnumdepth = 3` e usar `\paragraph` não numerado (estado atual)

### 3.1 Descrição

- Nivéis usados:
  - `\section` (1) → capítulos (2, 3, 4, 5).  
  - `\subsection` (2) → 5.1, 5.2, 5.3.  
  - `\subsubsection` (3) → 5.2.1, 5.2.2, 5.2.3, 5.2.4.  
  - `\paragraph` (4) → títulos locais (MAN/AUTO/SEMI, ECM Pod/IDIAS, notas).  
- `secnumdepth` fica no padrão (=3).
- Modos e notas aparecem como texto em negrito no início do parágrafo, mas sem número próprio.

### 3.2 Vantagens

- **Totalmente consistente com o Briefing**, que só exige até 5.2.4.
- Estrutura simples de manter; nenhuma alteração global no preâmbulo.
- Visual limpo: numeração não fica "profunda demais" para leitores casuais.

### 3.3 Desvantagens

- Não é possível dizer, no estilo Dash-34, "see Section 5.2.1.3" para se referir especificamente a SEMI mode; tem que usar texto ou label (`\ref{...}`).
- Para quem está acostumado com manuais muito hierárquicos (Dash-34, Dash-1), pode parecer "raso" demais.

---

## 4. Opção B — Aumentar `secnumdepth` para 4 e numerar `\paragraph`

### 4.1 Descrição

- Adicionar no preâmbulo do guia (e documentar no Briefing):

```latex
\setcounter{secnumdepth}{4}
```

- Manter a hierarquia de comandos exata que existe hoje:
  - `\subsection` → 5.2.  
  - `\subsubsection` → 5.2.1 / 5.2.2 / 5.2.3 / 5.2.4.  
  - `\paragraph` → modos internos de cada `\subsubsection` (MAN/AUTO/SEMI, ECM Pod/IDIAS, etc.).

- Com `secnumdepth = 4`, LaTeX passa a numerar também `\paragraph`:
  - Em 5.2.1, os `\paragraph{Manual Mode/Automatic/Semi}` se tornam algo como **5.2.1.1 / 5.2.1.2 / 5.2.1.3**.  
  - Em 5.2.2, os `\paragraph{External ECM / IDIAS}` viram **5.2.2.1 / 5.2.2.2**.

### 4.2 Vantagens

- Mantém **100% a hierarquia lógica do Briefing** (até 5.2.4) **e** adiciona um nível extra de granularidade que se comporta exatamente como você espera intuitivamente.
- Fica muito parecido com o estilo dos manuais BMS (Dash-34, etc.), que usam 2.7.2.1.3, 2.7.4.2.5, etc.
- Referências cruzadas ficam naturais: "see Section 5.2.1.3 (CMS SEMI mode)".

### 4.3 Desvantagens

- A numeração torna-se mais "profunda"; pode intimidar leitores menos técnicos.
- Se o `tocdepth` também for aumentado para 4, o sumário pode ficar mais cheio (embora isso seja opcional; é possível numerar `\paragraph` sem colocá-los no ToC).

### 4.4 Combinação recomendada

- `\setcounter{secnumdepth}{4}` — para numerar `\paragraph`.  
- Manter `tocdepth` em 2 ou 3:

```latex
\setcounter{tocdepth}{3}
```

Assim:

- Capítulos, seções e subsubseções (até 5.2.4) aparecem no sumário.
- Modos individuais (5.2.1.1 etc.) têm número e podem ser citados, mas **não** poluem o ToC.

---

## 5. Opção C — Numeração profunda apenas em capítulos específicos

É tecnicamente possível aumentar `secnumdepth` localmente, por exemplo só em Capítulo 5, usando:

```latex
{\setcounter{secnumdepth}{4}
  % Chapter 5 here
}
```

ou redefinindo `secnumdepth` logo antes do Capítulo 5 e restaurando depois.

No entanto, isso tende a complicar o modelo mental (e a manutenção) sem grande ganho:

- Leitores podem estranhar que apenas CMS tenha 5.2.1.1, enquanto TMS/DMS ficam em 3 níveis.
- No futuro, TMS (Cap. 3) e DMS (Cap. 4) também podem ganhar "modos" equivalentes (FCR CRM subcases, IAM profiles etc.).

Por consistência de projeto, se for decidido usar numeração de `\paragraph`, é mais simples e previsível aplicá-la **globalmente** ao documento.

---

## 6. Impacto em WIP Files e no Briefing

### 6.1 WIP Files (template V1.0)

- O template atual já usa até `\subsubsection` e deixa `\paragraph` livre para detalhes finos.
- Adicionar `\setcounter{secnumdepth}{4}` no preâmbulo do guia **não quebra nenhum WIP**; apenas passa a numerar níveis que antes eram não numerados.
- WIPs futuros que queiram tirar proveito disso podem estruturar submodos sempre como `\paragraph{...}` sob uma `\subsubsection`.

### 6.2 Briefing

Se a decisão for adotar o estilo "Dash-34-like" (Opção B), convém atualizar o Briefing em dois pontos:

1. **Seção 3.3 — LaTeX Preamble (Assumed)**  
   - Documentar explicitamente:

   ```latex
   % Section numbering depth
   \setcounter{secnumdepth}{4} % Number sections, subsections, subsubsections and paragraphs
   \setcounter{tocdepth}{3}    % ToC shows up to subsubsections
   ```

2. **Seção 11 — Template / Integration**  
   - Explicar que:
     - Níveis até 3 (capítulo → seção → subseção) são mandatórios conforme estrutura do Briefing.
     - `\paragraph` é o nível recomendado para subdivisões internas (modos, submodos, notas importantes).  
     - Com `secnumdepth = 4`, esses `\paragraph` terão numeração (5.2.1.1 etc.), mas não aparecem no ToC por padrão.

Com isso, o comportamento passa a ser parte do "contrato" do projeto, evitando ambiguidades futuras.

---

## 7. Recomendação de Linha Mestra

- **Curto prazo (estado atual do projeto):**  
  A estrutura de C5-S2 em `guide-v0.2.3.1` já está funcional. Não há urgência para mexer no preâmbulo ou no Briefing só por causa de numeração; pode ser decidido com calma após revisar o capítulo compilado.

- **Quando decidir alinhar mais com o Dash-34:**  
  A opção mais equilibrada é a **Opção B**:

  - Adicionar globalmente em `guide.tex`:

    ```latex
    \setcounter{secnumdepth}{4}
    \setcounter{tocdepth}{3}
    ```

  - Manter a hierarquia lógica prevista pelo Briefing (até 5.2.4 em `\subsubsection`).
  - Continuar usando `\paragraph{...}` para modos internos (MAN/AUTO/SEMI, ECM Pod/IDIAS, etc.), agora com numeração 5.2.1.1, 5.2.1.2, 5.2.1.3, 5.2.2.1, 5.2.2.2.

Isso oferece o melhor dos dois mundos:

- Coerência com a estrutura definida no Briefing.  
- Profundidade de numeração compatível com o estilo dos manuais BMS.  
- Controle sobre o quão "carregado" fica o sumário via `tocdepth`.
