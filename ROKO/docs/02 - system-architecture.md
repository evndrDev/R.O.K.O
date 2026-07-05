# Arquitetura do Sistema

## Objetivo

Definir a arquitetura da R.O.K.O. para garantir que o sistema seja modular, escalável, de fácil manutenção e preparado para evoluir ao longo do tempo.

---

# Filosofia da Arquitetura

A R.O.K.O. não é apenas um chatbot.

Ela é uma plataforma de assistência inteligente composta por módulos especializados, coordenados por um núcleo central responsável por organizar o fluxo de informações e tomar decisões sobre qual serviço deve ser utilizado.

Essa abordagem garante baixo acoplamento entre os componentes e facilita futuras expansões.

---

# Arquitetura Geral

```
                    Usuário
                       │
             ┌─────────▼─────────┐
             │     Frontend      │
             │ React / Electron  │
             └─────────┬─────────┘
                       │
                   REST API
                       │
             ┌─────────▼─────────┐
             │     Backend       │
             │   Spring Boot     │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │    R.O.K.O Core   │
             └─────────┬─────────┘
                       │
     ┌─────────────────┼──────────────────┐
     │                 │                  │
     ▼                 ▼                  ▼
 Banco de Dados    AI Gateway      Serviços Externos
 PostgreSQL       Modelos de IA     APIs diversas
```

---

# Componentes

## Frontend

Responsável pela interface com o usuário.

### Responsabilidades

- Exibir informações
- Receber comandos
- Enviar requisições ao Backend

Tecnologias previstas:

- React
- Vite
- Electron (futuro)

---

## Backend

Responsável pela lógica de negócio.

### Responsabilidades

- Receber requisições
- Processar informações
- Controlar módulos
- Gerenciar autenticação
- Persistir dados

Tecnologias previstas:

- Java 21
- Spring Boot

---

## R.O.K.O. Core

É o cérebro da aplicação.

Todo fluxo passa pelo Core.

### Responsabilidades

- Coordenar módulos
- Decidir qual módulo utilizar
- Compartilhar contexto
- Orquestrar chamadas ao AI Gateway
- Gerenciar regras de negócio

---

## Banco de Dados

Responsável pelo armazenamento permanente.

Tecnologia:

- PostgreSQL

Armazenará:

- usuários
- metas
- tarefas
- histórico
- memória
- configurações

---

## AI Gateway

Camada responsável pela comunicação com modelos de Inteligência Artificial.

Inicialmente:

- OpenAI

Futuramente:

- Modelos locais
- Outros provedores

O restante do sistema nunca acessará diretamente um modelo de IA.

Toda comunicação será feita através do AI Gateway.

---

## Serviços Externos

Integrações com APIs e plataformas.

Exemplos:

- Google Calendar
- GitHub
- Spotify
- APIs financeiras
- APIs meteorológicas

---

# Fluxo de Comunicação

```
Usuário

↓

Frontend

↓

Backend

↓

R.O.K.O. Core

↓

Módulo responsável

↓

Banco de Dados (se necessário)

↓

AI Gateway (se necessário)

↓

Resposta

↓

Frontend

↓

Usuário
```

---

# Módulos do Sistema

A R.O.K.O. será composta por módulos independentes.

## Chat

Responsável pela comunicação com o usuário.

---

## Memória

Gerencia informações importantes do usuário.

---

## Planejamento

Cria estratégias e planos de ação.

---

## Agenda

Gerencia compromissos e lembretes.

---

## Estudos

Organiza cronogramas de estudo e progresso.

---

## Finanças

Controla orçamento, despesas e metas financeiras.

---

## Voz

Reconhecimento e síntese de voz.

---

## AI Gateway

Responsável pela comunicação com modelos de IA.

---

# Estrutura Inicial do Backend

```
backend/

├── api/
├── core/
├── chat/
├── memory/
├── planning/
├── study/
├── finance/
├── voice/
├── ai/
├── database/
├── security/
├── config/
└── shared/
```

---

# Princípios Arquiteturais

- Modularidade
- Baixo acoplamento
- Alta coesão
- Escalabilidade
- Separação de responsabilidades
- Fácil manutenção
- Evolução contínua

---

# Decisões Arquiteturais

- O Core será responsável por coordenar todos os módulos.
- O AI Gateway abstrairá qualquer modelo de Inteligência Artificial utilizado.
- Os módulos serão independentes e reutilizáveis.
- O Backend será responsável por toda a lógica de negócio.
- O Frontend será responsável apenas pela apresentação.
- O banco de dados armazenará somente informações persistentes.

---

# Próximos Passos

Após a definição da arquitetura, as próximas etapas serão:

- Criar o README do projeto.
- Estruturar os módulos do Backend.
- Configurar o ambiente de desenvolvimento.
- Iniciar a implementação do MVP.
