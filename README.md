# Análise Preditiva de Churn para Clientes de Telecom

## 📖 Visão Geral do Projeto

Este projeto realiza uma análise de ponta a ponta sobre um dataset de uma empresa de telecomunicações, com o objetivo de entender os fatores que levam ao cancelamento de clientes (churn) e construir um modelo de Machine Learning para prever quais clientes têm a maior probabilidade de sair.

A análise parte de uma hipótese moderna sobre o impacto dos serviços de streaming na retenção e culmina em um diagnóstico preciso com recomendações de negócio acionáveis para a empresa.

## 🎯 Principais Questões e Hipóteses

O projeto foi guiado para responder às seguintes perguntas:
1.  A assinatura de serviços de streaming (`StreamingTV`, `StreamingMovies`) está associada a uma maior ou menor taxa de churn?
2.  Qual o impacto real da cobrança mensal (`MonthlyCharges`) na decisão de cancelamento?
3.  Quais são os perfis de clientes com maior e menor risco de churn?

## 📂 Estrutura de Arquivos

```
/
├── data/
|   └── Telco-Customer-Churn.csv
├── notebooks/
|   └── churn_analysis_report.ipynb # Notebook principal que apresenta a análise
├── images/
|   ├── top_10_fatores_diminuem_churn.png
|   ├── top_10_fatores_aumentam_churn.png
|   ├── cobranca_mensal.png
|   ├── taxa_churn_por_combo.png   
|   └── taxa_churn_por_assinatura.png
├── requirements.txt
└── README.md
```

## 📊 Análise e Descobertas

### 1. Análise Exploratória de Dados (EDA)

A investigação inicial revelou um insight surpreendente. Embora clientes com serviços de streaming apresentassem uma taxa de churn maior, uma análise mais profunda mostrou que a verdadeira causa não era o serviço em si.

Um **violin plot** cruzando `Churn`, `Status de Streaming` e `Cobrança Mensal` revelou o fator principal: **clientes com faturas mensais mais altas cancelam muito mais**, e os serviços de streaming são, na verdade, um indicador de uma fatura mais cara.

### 2. Modelagem Preditiva e Resultados

Foram testados dois modelos de classificação para prever o churn:
* **Baseline (Regressão Logística):** Apresentou uma performance sólida e consistente.
* **Avançado (Random Forest):** Um modelo mais complexo e robusto.

De forma inesperada, a **Regressão Logística se saiu ligeiramente melhor** para este problema específico, provando a importância de testar múltiplos algoritmos sem assumir que o mais complexo é sempre superior. O modelo final alcançou um **F1-Score de 0.61** e um **Recall de 0.57** para a classe de clientes que cancelaram, sendo um modelo comercialmente viável.

### 3. Interpretação do Modelo e Fatores de Risco

A análise dos coeficientes do modelo vencedor (Regressão Logística) nos permitiu identificar os perfis de risco:

* **🔴 Principais Fatores que AUMENTAM o Churn (Vilões):**
    1.  **Internet de Fibra Ótica:** Atrai um perfil de cliente mais exigente e sensível a preço e concorrência.
    2.  **Pagamento com Boleto Eletrônico:** Método de alto atrito que força uma decisão de pagamento mensal.
    3.  **Contrato Mensal:** Ausência de uma barreira de longo prazo para o cancelamento.

* **🟢 Principais Fatores que DIMINUEM o Churn (Heróis):**
    1.  **Contratos de 1 ou 2 anos:** De longe, o fator de retenção mais poderoso.
    2.  **Serviços de Valor Agregado:** Suporte Técnico e Segurança Online aumentam a lealdade.
    3.  **Perfil sem Internet:** Clientes apenas com telefonia fixa são extremamente leais.

## 📈 Recomendações de Negócio

Com base nos insights do modelo, as seguintes ações são recomendadas para a empresa:
1.  **Focar em Migração de Contratos:** Criar campanhas agressivas para converter clientes de planos mensais para contratos anuais, oferecendo pequenos descontos como incentivo.
2.  **Incentivar Pagamentos Automáticos:** Oferecer benefícios (ex: R$5 de desconto) para clientes que mudarem do boleto eletrônico para o pagamento automático via cartão de crédito.
3.  **Criar Retenção Proativa para Clientes de Fibra:** Desenvolver um programa de lealdade e suporte dedicado para o segmento de clientes com fibra ótica, que, apesar do alto risco, são clientes de alto valor.

## 🛠️ Tecnologias Utilizadas

* Python 3
* Pandas
* Matplotlib & Seaborn
* Scikit-learn
* Jupyter Notebook

## ⚙️ Como Executar o Projeto

1.  Clone o repositório.
2.  Instale as dependências: `pip install -r requirements.txt`.
3.  Para a análise completa e visual, execute o notebook `churn_analysis_report.ipynb`.

