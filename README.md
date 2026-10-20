# 📈 Assistente de Investimentos com RPA e n8n

Projeto desenvolvido como parte do desafio prático da **DIO (Digital Innovation One)**, focado no uso de Automação de Processos Robóticos (RPA), fluxos de trabalho no n8n e manipulação de dados em Python para auxílio e tomada de decisão em investimentos.

---

## 🎯 Objetivo do Projeto

O objetivo principal desta aplicação é automatizar a ingestão de dados de clientes a partir de um script Python (executado no Google Colab), relacionar esses dados com opções de investimento previamente cadastradas (via arquivo CSV público) e gerar análises e recomendações personalizadas com base no perfil de cada cliente.

---

## 🛠️ Tecnologias Utilizadas

* **Python 3**: Extração, manipulação e envio dos dados via requisição HTTP POST.
* **Google Colab**: Ambiente de desenvolvimento e execução do script Python.
* **n8n (Cloud)**: Plataforma de automação e orquestração de workflows.
* **JavaScript / Node.js**: Lógica de processamento e cruzamento de dados nos nós do n8n.
* **GitHub**: Versionamento do código e armazenamento dos dados de investimento (CSV) e do fluxo (`n8n/workflow.json`).

---

## 📐 Arquitetura do Workflow

[ Script Python ] ---> ( Webhook ) ---> [ HTTP Request (CSV) ]
                            |                     |
                            v                     v
                 ( Respond to Webhook )   [ Code JavaScript ]
                            |                     |
                            +-------> ( Merge ) <-+
                                        |
                                        v
                            [ Code JavaScript (Final) ]

### Descrição das Etapas:

1. **Gatilho (Webhook)**: Recebe os dados dos clientes enviados via POST pelo script Python.
2. **Resposta Direta (Respond to Webhook)**: Confirma o recebimento dos dados para o cliente HTTP (Python) de forma imediata.
3. **Ingestão de Dados Externos (HTTP Request)**: Busca a tabela CSV atualizada com as opções de investimento hospedada no GitHub.
4. **Tratamento de Dados (Code in JavaScript)**: Processa e formata os dados do CSV para cruzamento.
5. **Correlação (Merge)**: Une os dados dos clientes recebidos via Webhook com a lista de investimentos tratada.
6. **Geração de Recomendação (Code in JavaScript1)**: Aplica a regra de negócio para indicar os melhores investimentos de acordo com o saldo e perfil de cada cliente.

---

## 📁 Estrutura do Repositório

.
├── n8n/
│   └── workflow.json          # Arquivo exportado do fluxo do n8n
├── extrair_clientes.ipynb     # Notebook Python de automação/extração
└── README.md                  # Documentação do projeto

---

## 👩‍💻 Autora

Desenvolvido por **Carolina Cavallaro**  
[LinkedIn](https://www.linkedin.com/in/carolcavallaro/) | [GitHub](https://github.com/carolcavallaro)
