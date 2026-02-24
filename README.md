# VibeFinanças

**VibeFinanças** é um protótipo de app de organização de finanças pessoais baseado em conversas em linguagem natural. O usuário registra gastos digitando ou falando; o Agente sugere classificação e pede confirmação antes de salvar. Foco em simplicidade, acessibilidade e experiência conversacional.

---

## Visão geral

**Problema:** muitos apps de finanças exigem entrada manual e desmotivam iniciantes.  
**Solução:** interface conversacional que reduz fricção: registre gastos por texto/voz, confirme via cartão, acompanhe metas e visualize relatórios simples.  
**Público‑alvo:** iniciantes que querem controlar gastos sem planilhas.  
**Nome do projeto:** **VibeFinanças**

---

## Funcionalidades principais

- **Onboarding**: coleta de nome, objetivo financeiro e idioma.  
- **Chat em linguagem natural**: registrar gastos com parsing automático (valor, categoria, data).  
- **Modal de confirmação**: Confirmar / Editar / Reclassificar antes de salvar.  
- **Persistência**: integração com Google Sheets (via Webhook) para prototipagem sem backend.  
- **Metas**: criar metas e acompanhar progresso.  
- **Relatórios**: exportação de dados para gerar gráficos (pizza por categoria; linha por mês).  
- **Tutorial interativo e FAQ**: 6 perguntas frequentes + opção “Não encontrei” para falar com o Agente.  
- **i18n**: Português Brasileiro por padrão; suporte a Inglês, Espanhol e Francês.  
- **Paleta visual**: variações de verde — **#0B6B3A**, **#2EA86A**, **#BFF3D6**.

---

## Prompt final (PRD) usado com a IA

Você é o Agente Financeiro Vibe. Responda em Português Brasileiro por padrão e no idioma do usuário quando solicitado (pt/en/es/fr). Tom: educativo, direto e empático. Comece recomendações com "Sugestão:". Funcionalidades essenciais:

Onboarding (nome, objetivo, idioma).

Chat em linguagem natural para registrar gastos (texto e opcionalmente voz).

Parsing automático de valor, categoria e data; sempre abrir modal de confirmação com opções Confirmar / Editar / Reclassificar antes de salvar.

Persistência das transações (Google Sheets ou DB).

Metas financeiras com progresso.

Relatórios simples (pizza por categoria; linha por mês).

Tutorial interativo com FAQ (6 perguntas) e opção "Não encontrei" que abre chat com o Agente.

i18n: PT/EN/ES/FR.

Paleta de verdes: #0B6B3A,#2EA86A,#BFF3D6.

Evitar pedir dados sensíveis; confirmar exclusões; aplicar regras de privacidade (cada usuário só vê seus dados).
Responda com exemplos de microcopy e mensagens de confirmação. Use linguagem acessível e curta.


---

## Como executar o protótipo (Landbot)

1. **Criar bot no Landbot** com nome **VibeFinanças**.  
2. **Blocos essenciais**:
   - Start → Perguntar nome (`@name`) → Perguntar objetivo (`@objective`) → Perguntar idioma (`@lang`) → Mensagem de boas‑vindas.
   - Input livre → bloco de processamento (mock ou regex) → modal ConfirmTransaction (Confirmar / Editar / Reclassificar).
   - FAQ/Tutorial com botão “Não encontrei” que abre chat livre.
3. **Persistência**: conectar Webhook do Landbot ao Google Sheets (colunas: timestamp, user_name, amount, category, date, note, source).  
4. **Testes**: simular 10 conversas; validar gravação no Google Sheets.  
5. **Evidências**: capturar 3 prints (onboarding, modal confirm, Google Sheets) e opcionalmente um vídeo curto (30–60s).

---

## Estrutura do repositório sugerida

/ (root)
├─ README.md
├─ assets/
│  ├─ screenshots/
│  │  ├─ onboarding.png
│  │  ├─ confirm_transaction.png
│  │  └─ google_sheets.png
│  └─ video/
│     └─ demo.mp4 (opcional)
├─ landbot_flow_export.json (se disponível)
├─ flow_description.md
└─ sheet_sample.csv


**sheet_sample.csv** (exemplo)

timestamp,user_name,amount,category,date,note,source
2026-02-24 13:00,José,50,Alimentação,2026-02-24,"Mercado",landbot
2026-02-24 13:05,José,30,Transporte,2026-02-24,"Uber",landbot
2026-02-24 13:10,José,200,Poupança,2026-02-24,"Transferência",landbot


---

## Evidências e entrega para a DIO

- **README.md** atualizado com o PRD e instruções.  
- **assets/screenshots/** com pelo menos 3 imagens: onboarding, modal confirm, Google Sheets.  
- **landbot_flow_export.json** ou **flow_description.md** descrevendo o fluxo (se export não for possível).  
- **sheet_sample.csv** com 3 transações de exemplo.  
- **Commit message sugerido:** `feat: add VibeFinanças prototype and README with PRD and evidence`  
- **Link público do fork**: copie o URL do seu fork e submeta na plataforma DIO.

---

## Reflexão modelo (adicione suas impressões)

**O que aprendi:** prototipar conversas reduz atrito e melhora a taxa de registro de gastos; usar mocks economiza cotas de LLM durante validação.  
**Desafios:** parsing robusto de linguagem natural; balancear automação e confirmação para evitar erros.  
**Próximos passos:** integrar OpenAI/LLM com controle de histórico (últimas 6 mensagens), melhorar NLU com exemplos reais e adicionar gráficos in‑app.

---

## Licença

Este repositório segue a mesma licença do repositório-base da DIO. Adapte conforme necessário.

---

