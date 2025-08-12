# xai-credit-risk-lime
# Decifrando a Caixa Preta: Tornando Modelos de IA Explicáveis com LIME

## 1. Contextualização do Problema e Objetivos

O setor de crédito bancário confia cada vez mais em modelos de machine learning para tomar decisões sobre a concessão de empréstimos. Embora esses modelos possam ser altamente precisos, eles são frequentemente vistos como "caixas pretas" — sistemas que tomam decisões sem fornecer uma justificativa clara.

Este projeto foi desenvolvido para atender a uma necessidade crítica: a de explicar as decisões de um modelo de risco de crédito. O objetivo é demonstrar como a técnica de **Explainable AI (XAI)**, utilizando a biblioteca **LIME (Local Interpretable Model-agnostic Explanations)**, pode gerar explicações locais e transparentes para cada decisão individual, promovendo confiança, conformidade regulatória e justiça.

O projeto utiliza o dataset **Statlog (German Credit Data)** para simular um cenário real de concessão de crédito, onde o modelo deve prever se um cliente é um bom ou mau risco de crédito.

## 2. Modelo Preditivo Escolhido: Random Forest Classifier

Para este problema de classificação, optamos por um modelo **Random Forest Classifier**.

- **Por que escolhemos este modelo?** O Random Forest é um algoritmo de aprendizado de máquina de conjunto (ensemble) que constrói múltiplas árvores de decisão e combina suas previsões para obter um resultado mais robusto e preciso. Ele é conhecido por seu alto desempenho, capacidade de lidar com dados complexos e por ser menos propenso a *overfitting*.

O modelo foi treinado em um conjunto de dados de 700 clientes e testado em 300, alcançando uma acurácia de aproximadamente **77,00%**.

## 3. Explicações Geradas pelo LIME

A seguir, apresentamos um exemplo de como o LIME foi utilizado para explicar a previsão do nosso modelo para um cliente específico. A imagem abaixo mostra a explicação gerada:

![Explicação LIME para um cliente](images/explicacao_cliente_0.png)

**Análise da Explicação:**

- **Previsão do Modelo:** O modelo previu que este cliente tem um **Bom Risco** com alta probabilidade.
- **Fatores de Influência (Contribuição Positiva):** As características que mais contribuíram para a decisão de "Bom Risco" foram:
    - **`feature_1 < 4.00`**: O valor baixo desta característica foi o fator mais forte para o modelo classificar o cliente como de bom risco.
    - **`feature_3 > 3.00`**: O valor alto desta característica também teve um impacto significativo na previsão de bom risco.
- **Fatores de Influência (Contribuição Negativa):** Embora o modelo tenha aprovado o crédito, a característica **`feature_2 < 24.00`** teve uma pequena contribuição na direção de "Mau Risco". A decisão final do modelo foi influenciada positivamente pelos outros fatores.

## 4. Reflexões e Conclusão

A aplicação do LIME revelou a importância da interpretabilidade para além da simples acurácia do modelo.

- **Importância da Interpretabilidade:** As explicações locais do LIME permitem que a empresa de crédito não apenas tome uma decisão, mas também a justifique. Isso é crucial para a **confiança do cliente**, que pode entender por que seu pedido foi aprovado ou negado. Além disso, garante a **conformidade regulatória**, pois as decisões podem ser auditadas para evitar vieses.
- **Limitações:** É importante notar que o LIME fornece uma explicação **local** e **aproximada**. Ela descreve o comportamento do modelo em torno de uma única previsão, mas não explica o modelo globalmente. A estabilidade das explicações também pode variar.
- **Impacto na Prática:** As explicações do LIME poderiam ser usadas para:
    1.  Comunicar a decisão ao cliente de forma clara e objetiva.
    2.  Identificar e mitigar potenciais vieses no modelo.
    3.  Ajudar analistas de crédito a tomar decisões mais informadas.

## 5. Como Executar o Projeto

1.  **Clone o repositório:**
    `git clone https://github.com/C:\Users\Ola chatinha\OneDrive\Área de Trabalho\Xai-credit-risk-lime/xai-credit-risk-lime.git`
2.  **Instale as dependências:**
    `pip install -r requirements.txt`
3.  **Abra o notebook:**
    Execute o arquivo `credit_risk_xai.ipynb` em um ambiente Jupyter ou no Google Colab.
