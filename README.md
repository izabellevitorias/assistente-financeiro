# Assistente Financeiro

## Sobre o Projeto

**Projeto:** Assistente Financeiro

**Problema que resolve:** Ajuda usuários a registrar, organizar e entender seus gastos pessoais de forma simples.

## Integrantes

| Nome | GitHub |
|------|--------|
| Izabelle Vitoria | @izabellevitorias |
| Julia Baxega dos Reis | @juliabxreis |
| Guilherme Paulino dos Santos Alves | @guipaulino0202 |

## Como funciona

O usuário informa dados sobre seus gastos, como valor, categoria, descrição ou data da despesa. O fluxo criado no N8N recebe essas informações, organiza os dados e pode consultar APIs externas para complementar o processamento. Em seguida, as informações são enviadas para o Gemini, que interpreta os dados e ajuda a gerar uma resposta mais clara para o usuário. Como saída, o usuário recebe uma resposta organizada, podendo visualizar o registro do gasto, alertas, classificações ou um resumo financeiro simples.

## Arquitetura

```mermaid
flowchart TD
    A[Usuário preenche formulário<br>Valor, moeda, categoria, descrição, data]
    B[N8N recebe os dados<br>Organiza campos do formulário]
    C[Frankfurter API - Cotação em tempo real<br>GET api.frankfurter.dev/v2/latest?from=USD&to=BRL<br>Gratuita - sem chave - dados reais]
    D[Processar e calcular dados<br>Converte moeda para BRL com taxa real<br>Calcula projeção mensal e anual]
    E[Gemini - Análise financeira<br>Avalia razoabilidade, alertas e dicas<br>Nota 1 a 10 e impacto anual]
    F[N8N formata o relatório<br>Monta resumo com câmbio e análise]
    G[Usuário recebe o resultado]

    A -->|Form Trigger| B
    B --> C
    C --> D
    D -->|Prompt com contexto| E
    E --> F
    F --> G
```
