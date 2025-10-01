# 🍄 Classificação de Cogumelos com IA

Este projeto investiga se é possível **identificar cogumelos comestíveis ou venenosos** apenas analisando características do **chapéu**, usando **Inteligência Artificial (IA)**.

---

## 📌 Contexto
A classificação correta de cogumelos é **crucial em biologia e micologia**.  
A hipótese: **o chapéu sozinho contém informações suficientes para prever toxicidade?**  

---

## 📊 Base de Dados
- **Origem:** Dataset público UCI Mushroom Dataset  
- **Tamanho:** 8.124 exemplares  
- **Classes:** Comestíveis (e) e Venenosos (p)  
- **Características usadas:** 20 variáveis do chapéu (cor, textura, formato)  

**Pré-processamento:**
- One-Hot Encoding de variáveis categóricas  
- Normalização das variáveis numéricas  
- Separação treino/teste (80/20)  

---

## 🧩 Tecnologias e Conceitos

### 🔹 SVM (Support Vector Machine)
Algoritmo de **classificação supervisionada** que encontra um **hiperplano ótimo** separando as classes.  

**Analogia:** Imagine colocar uma régua entre duas espécies de sementes na mesa; se não for suficiente, levantamos a mesa em uma dimensão maior para separá-las melhor.  

---

### 🔹 GridSearchCV
Técnica para encontrar a **melhor combinação de parâmetros** do modelo (`C`, `gamma`, `kernel`) usando **validação cruzada**.  

**Analogia:** Testar várias receitas até achar a mais saborosa.  

---

### 🔹 Cross-Validation
Divide o dataset em “folds” para **garantir generalização** e evitar overfitting.  

**Analogia:** Estudar com várias listas de exercícios para garantir preparo completo.  

---

### 🔹 Matriz de Confusão
Analisa **acertos e erros** do modelo:

| Predição | Comestível | Venenoso |
|----------|------------|----------|
| **Comestível** | TN | FN |
| **Venenoso**   | FP | TP |

**Falsos Negativos (FN):** o mais perigoso, cogumelos venenosos classificados como comestíveis.  

---

### 🔹 Possíveis Extensões
- **Random Forest / XGBoost**: bons para dados tabulares  
- **CNNs (Redes Neurais Convolucionais)**: úteis para imagens reais  
- **Ensemble Methods**: combinar modelos para maior acurácia  

---

## 🤖 Metodologia
- **Modelo:** SVM  
- **Otimização:** GridSearchCV (`C`, `kernel`, `gamma`)  
- **Validação:** Cross-validation  

---

## 📈 Resultados
- **Acurácia final:** 71,6%  
- **Acertos:** 7 em cada 10 cogumelos  
- **Crítico:** 195 cogumelos venenosos classificados como comestíveis (**falsos negativos**)  

---

## ⚠️ Limitações
- Apenas o **chapéu** foi usado  
- Outras características (pé, esporos, odor) são importantes  
- Modelo **não confiável para uso real**  

---

## 🚀 Aplicações Futuras
- Incluir **mais variáveis biológicas**  
- Testar **outros algoritmos**: Random Forest, XGBoost, Redes Neurais  
- Usar **visão computacional (CNNs)** em imagens reais  
- Desenvolver **apps móveis** como apoio em pesquisas de campo  

---

## ❓ FAQ

**Por que apenas o chapéu?**  
- É a parte mais visível e fácil de caracterizar.  

**Apenas visuais bastam?**  
- Não. O chapéu isolado não garante segurança na classificação.  

**Como aumentar acurácia?**  
- Mais variáveis, novos algoritmos e análise de imagens (CNNs).  

---

## 👥 Autores
- Avrahan Ben Aram de Souza  
- Gabriel Yukio Yamaguti Minato  
- Felipe Seiji Namiyama Nishina  
- Miguel Santana da Costa  

---

📌 **Conclusão:** O chapéu isolado **não é suficiente para prever toxicidade**. Apesar de 71,6% de acurácia, os riscos de falsos negativos tornam o modelo inseguro para uso prático, indicando a necessidade de variáveis adicionais e técnicas de IA mais avançadas.
