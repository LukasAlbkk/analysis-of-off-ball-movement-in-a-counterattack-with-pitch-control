# ⚽ Predição de Sucesso em Contra-Ataques no Futebol

Este projeto tem como objetivo prever se um contra-ataque em uma partida de futebol será bem-sucedido (isto é, se resultará em entrada na grande área) a partir de sequências de matrizes de pitch control. As matrizes são codificadas por um autoencoder e analisadas por uma LSTM para classificação.

---

## 🚀 Pipeline do Projeto

✅ **1) Geração das Matrizes de Pitch Control**  
Cada frame de um contra-ataque é convertido em uma matriz representando o controle de posse de bola no campo.

✅ **2) Autoencoder**  
Treinado de forma **não supervisionada** com todas as matrizes de pitch control para gerar embeddings compactos dos frames. Após treinado, seus pesos foram congelados para uso na LSTM.

✅ **3) LSTM**  
Treinada em sequências dos embeddings gerados pelo autoencoder para prever a probabilidade de sucesso do contra-ataque.

---

## ⚙️ Melhorias Aplicadas

- Redução do learning rate inicial para maior estabilidade no treino.
- Aumento do dropout e adição de regularização L2 para reduzir overfitting.
- Uso de EarlyStopping com restore_best_weights para interromper o treino na melhor época.
- Uso de ReduceLROnPlateau para ajustar automaticamente o learning rate quando a validação estagna.
- Aumento do batch size para reduzir flutuação nas métricas de validação.
- Ajuste do threshold de decisão para otimizar o F1-score da classe minoritária.

---

## 📊 Resultados

- **Acurácia no conjunto de teste:** ~81%  
- **F1-score para a classe Sucesso:** 0.61 (usando threshold ótimo de 0.45)  
- **Estabilidade nas curvas de loss e acurácia**, sem picos abruptos durante o treino.

---

## 📁 Estrutura do Repositório

