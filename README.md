<h1 align="center">Rodrigo Mota</h1>

<p align="center">
  <strong>Arquiteto de Integrações &amp; Automação Corporativa</strong><br>
  SAP Business One · SQL Server · n8n · Power BI · FastAPI · Docker
</p>

<p align="center">
  <a href="https://motainteligencia.com.br">
    <img src="https://img.shields.io/badge/Mota_Intelig%C3%AAncia_de_Neg%C3%B3cio-00B4D8?style=for-the-badge&logoColor=white" alt="Mota Inteligência de Negócio">
  </a>
  <a href="https://www.linkedin.com/in/rodrigo-mota-2619b422/">
    <img src="https://img.shields.io/badge/LinkedIn-0D1B2A?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <a href="contato@motainteligencia.com.br">
    <img src="https://img.shields.io/badge/E--mail-1B263B?style=for-the-badge&logo=gmail&logoColor=white" alt="E-mail">
  </a>
</p>

---

## Sobre

Trabalho na camada onde o ERP encontra a operação real da empresa, o ponto em que o dado sai do SAP Business One e precisa chegar em quem decide, íntegro e no horário.

Atuo de ponta a ponta: modelagem de dados no SAP B1 → view SQL confiável → orquestração em n8n → entrega em Power BI, app ou Teams. Incluindo o contêiner que roda isso em produção e o alerta que dispara quando algo quebra.

Sou o responsável técnico interno de uma indústria: quando uma integração cai, o alerta chega em mim e a sustentação é minha, não existe "abrir chamado pra outra equipe". Isso moldou meu critério de projeto: prefiro a solução simples que sobrevive à solução elegante que quebra.

**Como eu penso arquitetura:**

```
Dado confiável (view SQL)  →  Automação (n8n / Power Automate)  →  Interface (Power BI / app / Teams)
                                      ↓
                          Validação operacional antes de escalar
```

---

## Stack 

| Camada | Tecnologias |
|---|---|
| **Dados & ERP** | SQL Server · T-SQL · SAP Business One (Service Layer, DI/DTW) · Crystal Reports · PostgreSQL |
| **Automação & Integração** | n8n self-hosted (queue mode) · Power Automate · Webhooks · REST APIs · Change Tracking |
| **Backend** | Python · FastAPI · Uvicorn · autenticação por API key |
| **BI & Visualização** | Power BI · DAX · modelagem dimensional · views materializadas |
| **Infraestrutura** | Linux (Ubuntu Server) · Docker · Docker Compose · Traefik · Nginx · Cloudflare · Windows Server |
| **Microsoft 365** | SharePoint Online · Power Apps · Microsoft Teams (Adaptive Cards) · Graph API |
| **Front & Protótipo** | Next.js · Tailwind CSS · Lovable · Typebot |

---

## O que eu construo

### 🔄 Integrações ERP ↔ Aplicações

Sincronização bidirecional entre SAP Business One e aplicações internas via n8n e Service Layer. Trabalho com estratégias distintas por criticidade: batch horário para volume, Change Tracking para tempo real e consulta sob demanda via webhook para operações sensíveis. Paginação de payload e controle de janela de execução para não competir com a carga transacional do ERP.

### 🗄️ Camada de dados sobre SAP B1

Views SQL como contrato entre o ERP e o consumo: nomenclatura padronizada, lógica de negócio centralizada, relatórios desacoplados da estrutura interna do SAP. Quando performance vira problema, substituí uma view crítica que dominava a CPU do SQL Server na janela de refresh por uma tabela materializada com índice columnstore, alimentada por stored procedure agendada, mantendo todas as conexões dos relatórios intactas, correção de uma solução feita por outra ADM.

### 📊 Inteligência de negócio

Power BI conectado direto ao SQL Server do SAP B1, com modelo semântico próprio não relatório sobre tabela crua. A regra de negócio mora na view; o Power BI consome contrato, não estrutura interna do ERP.

Construo indicador que muda comportamento, não painel que decora reunião: gestão de pedidos em aberto com sinalização de autorização, adiantamento e follow-up pendente; projeção de faturamento; e modelo de scoring consultivo que classifica oportunidade de venda em escala de 0 a 100, com faixas de prioridade e temperatura de cliente para direcionar o time comercial.

Carga sincronizada com a janela de refresh, log de execução e monitoramento de custo de consulta, dashboard que não atualiza no horário é dashboard que ninguém usa. O critério é sempre o mesmo: se o número aparece no painel e ninguém decide diferente por causa dele, o indicador está errado não a ferramenta.

### 🏭 Sistemas operacionais internos

MES para chão de fábrica com controle de lote, apontamento por operador e painel de liderança, migrado de SQLite para PostgreSQL em container. Central de Pedidos em Kanban espelhando o fluxo comercial e de faturamento, com máquina de estados para divergências de NF-e, regras de elegibilidade de CC-e ancoradas na legislação fiscal e SLA com semáforo.

### ⚙️ Automação de processos de negócio

Conciliação automatizada de repasses de marketplace contra o ERP. Distribuição de documentos por WhatsApp com origem no SharePoint. Alertas executivos em Microsoft Teams via Adaptive Cards: resumo, leitura contextual e impacto financeiro, não só o número cru.

### 🛡️ Governança de infraestrutura

Observabilidade e capacity planning em VPS compartilhada com múltiplos fornecedores externos. Limites de recurso por container, diagnóstico de contenção de I/O e memória, isolamento de ambientes e definição clara de fronteira de responsabilidade entre quem constrói workflow e quem responde pelo servidor.

---

## Como eu trabalho

- **MVP primeiro.** Solução mínima funcional em produção vale mais que arquitetura completa no slide.
- **Dado antes de interface.** Dashboard sobre dado ruim é mentira bem formatada.
- **Baixo custo por princípio.** Dependência paga só quando não existe caminho sustentável sem ela.
- **Reutilizável, não único.** Padrão de nomenclatura, padrão de card, padrão de view para que o próximo caso leve horas, não semanas.
- **Escrever o risco.** Quando uma decisão técnica tem risco operacional ou fiscal, ele vai documentado para a diretoria antes de virar incidente.

---

## Diagnóstico é parte do trabalho

Boa parte do que faço não é construir, é descobrir por que algo quebrou.

Já rastreei colisão de chave primária em rotina interna do SAP via Extended Events, identifiquei consumo desproporcional de banco causado por armazenamento indevido de histórico de conversas, isolei picos de CPU de antivírus em VM de Service Layer e mapeei crescimento silencioso de base em ambiente de staging que funcionava, na prática, como produção.

Diagnóstico com evidência, não com achismo. Depois a correção.

---

## Contato

Aberto a conversas sobre integração de ERP, arquitetura de automação e engenharia de dados em ambiente organizacional.

<p>
  <a href="https://motainteligencia.com.br">🌐 motainteligencia.com.br</a> ·
  <a href="https://www.linkedin.com/in/rodrigo-mota-2619b422/">💼 LinkedIn</a> ·
  <a href="contato@motainteligencia.com.br">✉️ E-mail</a>
</p>

<p align="center">
  <sub>Belo Horizonte/MG · Brasil</sub>
</p>
