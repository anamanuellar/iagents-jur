# 🤖 ARGOS IA - Agente Inteligente para Análise de Notas Fiscais

> Agente de IA capaz de responder perguntas em linguagem natural sobre dados de notas fiscais (CSV), otimizando a análise e tomada de decisão no setor financeiro.

## 🎯 Demo & Equipe

Experimente o chat ao vivo: **[Chat Demo](https://manurs.app.n8n.cloud/webhook/4972343f-ebd6-47bf-8cb9-1b71b618045b/chat)**

**Desenvolvido por:**
- 👤 **Ana Manuella da S. Ribeiro** [![GitHub](https://img.shields.io/badge/GitHub-anamanuellar-181717?style=flat&logo=github)](https://github.com/anamanuellar)  [![Email](https://img.shields.io/badge/Email-ribeiro.anamanuella@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:ribeiro.anamanuella@gmail.com) 
- 👤 **Enos Luiz da Silva Correa** [![Email](https://img.shields.io/badge/Email-enosluiz@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:enosluiz@gmail.com)  
- 👤 **Jader Augusto Maciel Fonseca** [![Email](https://img.shields.io/badge/Email-jader.augusto@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:jader.augusto@gmail.com)
- 👤 **Letivan Gonçalves de Mendonça Filho** [![GitHub](https://img.shields.io/badge/GitHub-Letivan--filho-181717?style=flat&logo=github)](https://github.com/Letivan-filho) [![Email](https://img.shields.io/badge/Email-letivan@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:letivan@gmail.com) 
- 👤 **Rodrigo Arantes** [![Email](https://img.shields.io/badge/Email-arantes.rodrigo@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:arantes.rodrigo@gmail.com)
- 👤 **Sergio Guerrero Naves de Souza** [![Email](https://img.shields.io/badge/Email-senaguerrero@hotmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:senaguerrero@hotmail.com)

## 📋 Sobre o Projeto

O **ARGOS IA** é uma solução desenvolvida em n8n que utiliza inteligência artificial para análise automatizada de notas fiscais. O sistema permite que profissionais façam perguntas em linguagem natural sobre dados fiscais e recebam respostas precisas e contextualizadas.

### 🎯 Público-Alvo
- Profissionais de contas a pagar
- Controladoria
- Auditoria interna
- Contadores
- Analistas fiscais de órgãos públicos e empresas privadas

## 🏗️ Arquitetura do Sistema

### Workflows Inclusos:

#### 1. **ARGOS_IA.json** - Workflow Principal
- **Função**: Interface de chat com IA para consultas
- **Componentes**:
  - `Chat Trigger`: Recebe mensagens do usuário
  - `Question and Answer Chain`: Processa perguntas usando RAG
  - `Google Gemini Chat Model`: Modelo de IA (Gemini 1.5 Flash)
  - `Workflow Retriever`: Busca dados relevantes

#### 2. **Notas_Fiscais.json** - Processamento de Dados
- **Função**: Extração e preparação de dados das NFs
- **Componentes**:
  - `HTTP Request`: Download de arquivos CSV do Google Drive
  - `Compression`: Descompactação de arquivos ZIP
  - `Code`: Transformação e organização dos dados
  - `Extract from File`: Extração de dados dos CSVs
  - `Merge`: Combinação de datasets

## 🚀 Como Implementar

### Pré-requisitos
- Conta no n8n Cloud
- Google Gemini API Key
- Arquivos CSV de notas fiscais

### Passo 1: Configurar Credenciais
1. No n8n Cloud, vá em **Credentials**
2. Adicione nova credencial do tipo **Google Gemini(PaLM) API**
3. Insira sua API Key do Google AI Studio

### Passo 2: Importar Workflows
1. No n8n Cloud, vá em **Settings** > **Import/Export**
2. Importe primeiro o `Notas_Fiscais.json`
3. Depois importe o `ARGOS_IA.json`

### Passo 3: Configurar Fonte de Dados
1. No workflow "Notas Fiscais", atualize a URL do Google Drive
2. Certifique-se que os arquivos CSV estão no formato esperado
3. Teste a execução do workflow de dados

### Passo 4: Ativar o Sistema
1. Ative o workflow "Notas Fiscais"
2. Ative o workflow "ARGOS IA"
3. Use o webhook do chat para interagir com o sistema

## 💬 Exemplos de Uso

### Perguntas Eficientes (Baixo consumo de tokens):
```
✅ "Qual o valor da NF 12345?"
✅ "Quantas NFs foram emitidas em janeiro?"
✅ "Qual a NF de menor valor?"
✅ "Total das NFs do cliente João?"
✅ "Resumo das NFs vencidas"
```

### Perguntas a Evitar (Alto consumo de tokens):
```
❌ "Analise detalhadamente todas as notas fiscais"
❌ "Descreva cada transação em detalhes"
❌ "Liste todos os itens de todas as NFs"
```

## 📊 Estrutura dos Dados

O sistema espera arquivos CSV com as seguintes estruturas:

### Cabeçalho das NFs (202401_NFs_Cabecalho.csv):
- Número da NF
- Data de emissão
- Cliente/Fornecedor
- Valor total
- Status
- Data de vencimento

### Itens das NFs:
- Código do produto
- Descrição
- Quantidade
- Valor unitário
- Valor total

## 🔧 Configurações Técnicas

### Modelo de IA:
- **Modelo**: Google Gemini 1.5 Flash
- **Contexto**: 131.072 tokens
- **Otimizado para**: Consultas rápidas e precisas

### Processamento de Dados:
- **Formato**: CSV compactado (ZIP)
- **Fonte**: Google Drive (URL pública)
- **Método**: RAG (Retrieval-Augmented Generation)

## 🛠️ Troubleshooting

### Erro: "Maximum context length exceeded"
- **Causa**: Muitos dados sendo enviados para a IA
- **Solução**: Use perguntas mais específicas ou implemente chunking

### Dados não encontrados:
- **Causa**: URL do Google Drive incorreta ou arquivo não acessível
- **Solução**: Verifique se o link está público e correto

### Respostas imprecisas:
- **Causa**: Dados mal estruturados ou pergunta ambígua
- **Solução**: Padronize os CSVs e seja específico nas perguntas

## 📈 Roadmap

- [ ] Suporte a múltiplos formatos (Excel, XML)
- [ ] Dashboard de métricas
- [ ] Integração com ERPs
- [ ] Relatórios automatizados
- [ ] Alertas inteligentes

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para suas modificações
3. Faça commit das mudanças
4. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 📞 Suporte

Para dúvidas e suporte:
- Abra uma [Issue](../../issues)

---

**ARGOS IA** - Transformando dados fiscais em insights inteligentes! 🚀

