# 🌍 Voyager AI - Agente de Viagens Inteligente

> Um assistente virtual baseado em IA generativa capaz de planejar roteiros de viagem personalizados, utilizando RAG (Retrieval-Augmented Generation) para sugerir hotéis, restaurantes e voos com base em dados reais.

## 📋 Sobre o Projeto

O **Voyager** é um agente de viagens construído com Python que atua como uma consultora especializada (Persona "Voyager"). O sistema interage com o usuário em linguagem natural para coletar preferências de viagem, orçamento e datas, retornando um roteiro detalhado e personalizado.

O diferencial deste projeto é o uso de **Busca Semântica** em uma base de dados vetorial, permitindo que a IA acesse informações específicas de um dataset curado (Hotéis, Restaurantes e Voos) antes de gerar a resposta, garantindo recomendações mais precisas e menos alucinações.

---

## 🛠️ Tecnologias e Ferramentas

* **Linguagem:** Python
* **Orquestração de LLM:** [LangChain](https://www.langchain.com/)
* **Modelo Generativo:** Google Gemini (gemini-2.5-flash)
* **Embeddings:** Cohere (embed-multilingual-v3.0)
* **Vector Store:** FAISS (Facebook AI Similarity Search)
* **Manipulação de Dados:** Pandas & NumPy
* **Estruturação de Dados:** Pydantic

## 🚀 Funcionalidades

* **🧠 Memória Conversacional:** O agente mantém o contexto da conversa para refinar as sugestões.
* **🔍 Busca Semântica (RAG):** Utiliza embeddings para encontrar as melhores opções de estadia e gastronomia baseadas na descrição do usuário (ex: "quero um restaurante italiano romântico").
* **✈️ Planejamento Completo:**
    * Sugestão de Voos (Preços e Companhias).
    * Recomendação de Hotéis baseada em avaliações e localização.
    * Curadoria de Restaurantes por tipo de culinária e faixa de preço.
    * Criação de itinerário dia-a-dia.
* **🛡️ Engenharia de Prompt:** Implementação de `personas` e `guardrails` para garantir que o agente siga um fluxo lógico de atendimento (Apresentação -> Coleta -> Roteiro -> Fechamento).

## 📂 Estrutura do Pipeline

1.  **Ingestão de Dados:** Carregamento e limpeza de datasets de Hotéis, Restaurantes e Voos (Foco: Emirados Árabes e África do Sul).
2.  **Processamento:** Uso do `Pydantic` para formatar os dados em texto estruturado.
3.  **Vetorização:** Criação de embeddings textuais utilizando a API da Cohere.
4.  **Indexação:** Armazenamento dos vetores no FAISS para recuperação rápida.
5.  **Geração:** O modelo Gemini recebe a pergunta do usuário + o contexto recuperado do banco vetorial para gerar a resposta final.

## 📦 Como Executar

1.  Clone o repositório:
    ```bash
    git clone [https://github.com/seu-usuario/voyager-ai-agent.git](https://github.com/seu-usuario/voyager-ai-agent.git)
    ```
2.  Instale as dependências:
    ```bash
    pip install langchain-google-genai langchain-cohere langchain-community faiss-cpu pandas
    ```
3.  Configure as chaves de API (Crie um arquivo `.env` ou exporte as variáveis):
    * `GOOGLE_API_KEY` (Para o Gemini)
    * `COHERE_API_KEY` (Para os Embeddings)
4.  Execute o notebook `Agente_de_Viagens_Voyager.ipynb`.

## 🔮 Próximos Passos e Melhorias

* Expandir a base de dados para cobrir mais países.
* Implementar deploy da aplicação usando Streamlit ou FastAPI.
* Adicionar persistência de histórico de chat em banco de dados.

---
**Autor:** [Seu Nome]
