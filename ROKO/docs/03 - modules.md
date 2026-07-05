# Módulos da R.O.K.O.

## Objetivo

Este documento descreve todos os módulos que compõem a arquitetura da R.O.K.O., suas responsabilidades, dependências e possíveis evoluções.

Cada módulo possui uma responsabilidade única, seguindo o princípio de **Single Responsibility Principle (SRP)**, facilitando a manutenção, evolução e reutilização do sistema.

---

# Core

## Descrição

O Core é o coração da R.O.K.O.

Ele é responsável por coordenar todos os módulos do sistema, decidir qual serviço deve ser utilizado em cada situação e controlar o fluxo de informações.

## Responsabilidades

- Orquestrar os módulos
- Compartilhar contexto entre módulos
- Coordenar o fluxo da aplicação
- Gerenciar regras de negócio
- Encaminhar solicitações ao AI Gateway

## Dependências

- Todos os módulos da aplicação

---

# Chat

## Descrição

Responsável pela comunicação entre o usuário e a R.O.K.O.

Todo comando enviado pelo usuário passa inicialmente por este módulo.

## Responsabilidades

- Receber mensagens
- Enviar respostas
- Manter histórico da conversa
- Gerenciar sessões de chat

## Futuras melhorias

- Conversas em tempo real
- Múltiplas sessões
- Exportação do histórico

---

# Memory

## Descrição

Gerencia todas as informações persistentes relacionadas ao usuário.

É o módulo responsável por permitir que a R.O.K.O. "lembre" informações importantes ao longo do tempo.

## Responsabilidades

- Armazenar preferências
- Armazenar objetivos
- Manter contexto
- Gerenciar memória de longo prazo
- Recuperar informações relevantes

## Futuras melhorias

- Memória semântica
- Busca vetorial
- Priorização automática de informações

---

# Planning

## Descrição

Responsável por criar planos de ação e estratégias para atingir objetivos.

Este módulo transforma metas em tarefas organizadas.

## Responsabilidades

- Criar planos
- Definir prioridades
- Organizar cronogramas
- Dividir objetivos em etapas
- Gerenciar produtividade

## Futuras melhorias

- Planejamento automático
- Sugestão de prioridades
- Replanejamento inteligente

---

# Study

## Descrição

Gerencia todo o ambiente de estudos do usuário.

## Responsabilidades

- Organizar matérias
- Criar cronogramas
- Registrar progresso
- Controlar revisões
- Gerar estatísticas

## Futuras melhorias

- Revisão espaçada
- Flashcards
- Simulados
- Relatórios de desempenho

---

# Finance

## Descrição

Responsável pelo gerenciamento financeiro.

## Responsabilidades

- Registrar receitas
- Registrar despesas
- Controlar orçamento
- Acompanhar metas financeiras
- Gerar relatórios

## Futuras melhorias

- Gráficos
- Integração bancária
- Previsão financeira
- Alertas de gastos

---

# Calendar

## Descrição

Gerencia compromissos, eventos e lembretes.

## Responsabilidades

- Criar eventos
- Editar compromissos
- Enviar lembretes
- Organizar agenda

## Futuras melhorias

- Integração com Google Calendar
- Sincronização entre dispositivos
- Sugestão automática de horários

---

# Voice

## Descrição

Responsável pela interação por voz.

## Responsabilidades

- Reconhecimento de voz (Speech-to-Text)
- Síntese de voz (Text-to-Speech)
- Gerenciamento do microfone
- Reprodução de áudio

## Futuras melhorias

- Wake Word ("R.O.K.O.")
- Conversação contínua
- Múltiplas vozes
- Ajuste de velocidade da fala

---

# AI Gateway

## Descrição

Camada responsável pela comunicação entre a aplicação e modelos de Inteligência Artificial.

Nenhum outro módulo deve acessar diretamente um modelo de IA.

## Responsabilidades

- Enviar prompts
- Receber respostas
- Selecionar o provedor de IA
- Gerenciar custos
- Centralizar integrações

## Modelos previstos

- OpenAI
- Ollama
- Outros provedores

---

# Notification

## Descrição

Responsável por todas as notificações do sistema.

## Responsabilidades

- Lembretes
- Alertas
- Avisos importantes
- Notificações de metas

## Futuras melhorias

- Notificações push
- E-mail
- Discord
- Telegram

---

# Integration

## Descrição

Gerencia integrações com serviços externos.

## Responsabilidades

- Conectar APIs
- Sincronizar informações
- Gerenciar autenticação de terceiros

## Integrações previstas

- GitHub
- Google Calendar
- Spotify
- Gmail
- APIs financeiras

---

# Security

## Descrição

Responsável pela segurança da aplicação.

## Responsabilidades

- Autenticação
- Autorização
- Criptografia
- Proteção de dados
- Controle de acesso

---

# Shared

## Descrição

Contém componentes compartilhados entre todos os módulos.

## Responsabilidades

- Classes utilitárias
- Objetos compartilhados
- Exceções
- Constantes
- Helpers

---

# Relacionamento entre os módulos

```
Usuário
    │
    ▼
Chat
    │
    ▼
Core
    │
    ├───────────────┐
    │               │
    ▼               ▼
Memory         Planning
    │               │
    ▼               ▼
Study        Finance
    │               │
    └───────┬───────┘
            ▼
        AI Gateway
            │
            ▼
      Modelos de IA
```

---

# Evolução dos módulos

Cada módulo foi projetado para evoluir de forma independente.

Essa abordagem permite adicionar novas funcionalidades sem impactar o restante do sistema, garantindo maior escalabilidade, organização e facilidade de manutenção ao longo do desenvolvimento da R.O.K.O.
