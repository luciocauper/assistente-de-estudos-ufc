# Assistente de Estudos — Concurso UFC

Um prompt para estudar para a prova escrita do concurso da UFC com qualquer LLM. Você escolhe um tema, escreve sua resposta, e a IA corrige usando os critérios de avaliação da banca. No fim da sessão, ela junta tudo num arquivo com as notas e sugestões do que estudar.

## Estrutura

```
.
├── instruction/
│   ├── instruction.md   # Instruções para a IA (em inglês)
│   └── contest.md       # Tabela de avaliação da prova escrita + conteúdo programático
├── estudos/             # Seus textos para a IA analisar (opcional)
└── saída de estudos/    # Sessões finalizadas e arquivo temporário
```

## Como usar

1. **Clone o repositório**
   ```bash
   git clone https://github.com/luciocauper/assistente-de-estudos-ufc.git
   cd .\assistente-de-estudos-ufc\
   ```

2. **Abra na sua IDE** (VS Code, Cursor, JetBrains etc.).

3. **Chame a LLM que preferir** (Claude, Copilot, Cursor, Gemini etc.). Ela precisa conseguir ler e escrever arquivos do projeto. Envie o conteúdo de `instruction/instruction.md` como primeira mensagem ou configure-o como instrução do projeto.

4. **Estude.**

## Como funciona uma sessão

**Preparação (primeira interação)**
- A IA verifica se o `instruction/contest.md` já tem o conteúdo programático.
- Se não tiver, ela pergunta qual é a sua vaga e quais assuntos caem na prova. Você pode colar a lista ou indicar o arquivo do edital.
- A IA preenche a tabela de conteúdos do `instruction/contest.md` sem mexer na ficha de avaliação e pede sua confirmação.
- Se houver uma sessão anterior não finalizada, ela pergunta se deve compilar ou apagar.

**Estudo**
1. Envie um tema pelo número ou pelo nome (ex.: `3` ou `Linguagens regulares`).
2. A IA confirma o tema e responde: `Escreva sobre o assunto escolhido ou diga qual arquivo devo analisar`.
3. Escreva a resposta no chat ou indique um arquivo da pasta `estudos/` (ex.: `estudos/linguagens-regulares.md`).
4. A IA avalia cada critério do `instruction/contest.md`, com nota, justificativa, erros e pontos que faltaram.
5. Repita com o mesmo tema ou com outro.

Cada resposta fica salva temporariamente em `saída de estudos/temp-session.md`.

**Finalização**

Envie `Terminar`. A IA vai:
- Gerar o arquivo final em `saída de estudos/`, com o nome `Assunto-DDMMAAAA.md` (ex.: `Linguagens-Regulares-27102026.md`), contendo:
  - Seus textos e as avaliações
  - Uma tabela de pontuação por critério
  - Pontos a melhorar
  - Assuntos sugeridos para estudar
- Conferir o arquivo final e então apagar o arquivo temporário.

## Trocando de vaga

O conteúdo programático muda de acordo com a vaga. Para trocar, apague a vaga e os assuntos da tabela **Conteúdos para o concurso e bibliografia base** no `instruction/contest.md`, deixando só os números (`1.`, `2.`...). Na próxima sessão, a IA vai pedir os novos assuntos.