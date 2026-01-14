## **Bot Discord — Sistema de Whitelist Automatizado**

### **Descrição:**

Um bot Discord avançado que automatiza o processo de whitelist/inscrição em servidores, permitindo que usuários respondam a formulários interativos pelo Discord. O bot coleta respostas através de perguntas em DM (texto, múltipla escolha e arquivo), envia os formulários para um canal de staff, que pode avaliar e responder através de botões persistentes. Resolve o problema de gerenciar inscrições manualmente, eliminando verificações manuais e oferecendo uma experiência automática e escalável para servidores Discord de qualquer tamanho.

**Funcionalidades principais:**

- Sistema de painel interativo para iniciar whitelists
- Formulários com até 10 perguntas customizáveis (texto, select, arquivo)
- Timeouts inteligentes e validações avançadas
- Sistema de cargos temporários com expiração automática
- Resposta automática aos usuários pelos botões de moderação
- Cooldown entre formulários
- Recuperação automática após restart
- Gerenciamento de permissões por cargo
- Threads automáticas para discussão
- Limpeza automática de dados (24h)

---

### **Tecnologias Utilizadas:**

| Tecnologia    | Versão | Uso                                                              |
| ----------------- | ------ | ------------------------------------------------------------ |
| **Python**        | 3.8+   | Linguagem base                                               |
| **discord.py**    | ≥2.3.0 | Framework para integração com Discord                        |
| **aiohttp**       | ≥3.8.0 | HTTP assíncrono para requisições                             |
| **python-dotenv** | ≥1.0.0 | Gerenciamento de variáveis de ambiente                       |
| **JSON**          | Nativo | Persistência de dados (sessões, cooldowns, roles, moderação) |
| **asyncio**       | Nativo | Programação assíncrona                                       |

**Stack técnico:**

- Arquitetura modular com 6 módulos especializados
- Sistema de banco de dados JSON (sem SQL)
- Padrão MVC com separação em config + modules + data
- Async/await para operações não-bloqueantes
- Views persistentes para botões interativos
- Sistema de task scheduling com @tasks.loop()

---

### **Resultados e Impacto:**

**Métricas:**

- 📊 Até **50 formulários simultâneos** em processamento
- 📊 **30 minutos** de timeout customizável
- 📊 Limpeza automática a cada **24 horas**
- 📊 Suporte a **até 5 imagens** por formulário
- 📊 **12 comandos slash** implementados
- 📊 **15 melhorias avançadas** documentadas no arquivo de ideias

**Aprendizados técnicos:**

1. **Padrão de Views Persistentes**: Implementação de botões que funcionam mesmo após restart do bot
2. **Sistema de Timeouts Inteligente**: Avisos antes da expiração com recovery automático
3. **Gestão de Estado com JSON**: Serialização eficiente sem dependência de BD externo
4. **Concorrência em Async**: Múltiplas sessões ativas com proper cleanup de tasks
5. **Validação em Camadas**: Validação de tipo → tamanho → conteúdo para segurança
6. **Autorização Granular**: Sistema de permissões baseado em cargos do Discord
7. **File Handling**: Upload/validação de arquivos em DM com limites configuráveis

**Arquitetura:**

```
modules/
  ├─ database_manager.py     (4 JSONs: sessions, roles, cooldowns, moderation)
  ├─ whitelist_handler.py    (Core do fluxo de formulário)
  ├─ role_manager.py          (Gerenciamento de cargos + temporários)
  ├─ moderation_manager.py    (Respostas de staff + persistência)
  ├─ panel_manager.py         (Painel interativo)
  └─ embed_builder.py         (Formatação visual)
```
