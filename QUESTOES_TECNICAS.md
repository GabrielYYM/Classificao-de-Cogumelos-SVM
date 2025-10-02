# 📌 Questões Técnicas – Conceitos, Tecnologias e Metodologias

Este documento apresenta um relatório técnico complementar ao README, detalhando conceitos, algoritmos, metodologias e decisões técnicas utilizadas no projeto de classificação de cogumelos com aprendizado de máquina.

---

## 🔹 Dados e Pré-processamento

O dataset utilizado continha cogumelos classificados como **comestíveis ou venenosos**, com **20 variáveis relacionadas ao chapéu**, incluindo cor, textura e formato. O conjunto de dados estava consistente, sem valores ausentes, permitindo um pré-processamento direto.

Para permitir que algoritmos de aprendizado de máquina interpretassem dados categóricos, aplicou-se **One-Hot Encoding**, representando variáveis nominais como vetores binários. Variáveis numéricas foram **normalizadas** para escalas compatíveis, evitando que características com maior amplitude influenciassem indevidamente o modelo.

Análises exploratórias mostraram que algumas variáveis apresentavam sobreposição de informação, mas todas foram mantidas para preservar a hipótese inicial do estudo.

---

## 🔹 Algoritmo de Classificação: SVM

O projeto utilizou **Support Vector Machine (SVM)** como algoritmo central. O SVM é um método de aprendizado supervisionado que busca um **hiperplano ótimo** para separar classes em um espaço n-dimensional, maximizando a **margem** entre elas. Apenas os **vetores de suporte** — pontos mais próximos à fronteira de decisão — determinam o posicionamento do hiperplano.

Para lidar com relações não lineares entre características do chapéu, foi utilizado o **kernel RBF**. Os principais parâmetros ajustados incluem:

- **C:** Controla a regularização, equilibrando viés e variância.  
- **gamma:** Define a influência de cada ponto no espaço transformado.  
- **kernel:** Função de transformação dos dados (RBF neste projeto).

**Referências e documentação:**  
- [SVM — Scikit-Learn](https://scikit-learn.org/stable/modules/svm.html)  
- [Understanding Support Vector Machines — Towards Data Science](https://towardsdatascience.com/support-vector-machines-svm-c9ef22815589)  
- [A Practical Guide to Support Vector Classification — Chih-Wei Hsu et al.](https://www.csie.ntu.edu.tw/~cjlin/papers/guide/guide.pdf)

---

## 🔹 Otimização de Hiperparâmetros: GridSearchCV

Para encontrar a combinação ideal de parâmetros do SVM, utilizou-se **GridSearchCV**, que realiza busca sistemática sobre uma grade de hiperparâmetros, avaliando cada combinação por meio de **validação cruzada (cross-validation)**.  

O processo inclui:

1. Definição de uma grade de parâmetros (`C`, `gamma`, `kernel`, etc.).  
2. Treinamento do modelo para cada combinação com cross-validation.  
3. Avaliação do desempenho usando métricas de interesse (acurácia, F1-score, recall, etc.).  
4. Seleção da configuração que maximize a performance e promova **boa generalização**, minimizando risco de overfitting.

### Exemplo em Python:

```python
from sklearn.model_selection import GridSearchCV
from sklearn.svm import SVC

param_grid = {
    'C': [0.1, 1, 10],
    'kernel': ['linear', 'rbf'],
    'gamma': [0.01, 0.1, 1]
}

grid = GridSearchCV(SVC(), param_grid, cv=5)
grid.fit(X_train, y_train)

print("Melhor combinação:", grid.best_params_)
```

---

## 🔹 Considerações Técnicas e Boas Práticas

O dataset apresentava classes relativamente equilibradas, dispensando técnicas adicionais de balanceamento como SMOTE.

A cross-validation foi utilizada para medir consistência do modelo e estabilidade de performance.

Ajustes de threshold e regularização foram considerados, mantendo a interpretação biológica das variáveis.

Futuras melhorias podem incluir ensemble methods e redes neurais convolucionais (CNNs), especialmente se forem analisadas imagens reais de cogumelos.

---

## 🔹 Limitações e Perspectivas

A principal limitação foi analisar apenas o chapéu dos cogumelos. Outras características — pé, esporos, odor e habitat — são determinantes para a toxicidade.

Para trabalhos futuros, recomenda-se:

- Incluir novas variáveis biológicas para enriquecer o modelo.  
- Explorar algoritmos como Random Forest, XGBoost ou CNNs se forem usadas imagens reais.  
- Aplicar ensemble methods para aumentar a robustez.  
- Ajustar threshold de decisão para reduzir falsos negativos, considerando trade-offs com precisão.

---

## 🔹 Interpretação e Impacto

O estudo confirma que o chapéu isolado não é suficiente para prever toxicidade, reforçando a necessidade de alinhar métodos de IA com conhecimento biológico.

Apesar das limitações, o projeto funciona como prova de conceito para demonstrar potencial e limites de modelos de classificação baseados em atributos visuais isolados, servindo como referência técnica para futuras pesquisas em IA aplicada à biologia.
