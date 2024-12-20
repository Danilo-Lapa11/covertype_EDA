# Relatório: Avaliação de Modelos de Classificação para a Base Covertype
## 1. Introdução 
A base de dados Covertype foi utilizada para testar diferentes modelos de classificação. Este estudo teve como objetivo identificar o melhor modelo de classificação para predizer o tipo de cobertura do solo com base em variáveis ambientais e geográficas. Quatro algoritmos foram avaliados:
- Árvore de Decisão (Decision Tree Classifier);
- K-Nearest Neighbors (KNN);
- Support Vector Machine (SVM);
- Multi-Layer Perceptron (MLP).
## 2. Metodologia
### 2.1. Base de Dados 
A base Covertype foi limitada a 10.000 amostras para reduzir o tempo de execução. O conjunto foi dividido em treino (80%) e teste (20%) para avaliar o desempenho dos modelos. Além disso, os dados dos conjuntos de treinamento foram padronizados usando a função StandardScaler.
### 2.2. Modelos de Classificação
Decision Tree: Avaliado com profundidades e parâmetros variados para controle de sobreajuste e critério de construção da árvore.
KNN: Avaliou-se o impacto do número de vizinhos (k) e o uso de pesos uniformes e baseados na distância.
SVM: Testou diferentes kernels (sigmoid e rbf) e os parâmetros de regularização (C) e gama.
MLP: Explorou-se o número de camadas ocultas, taxas de aprendizado e regularização.
### 2.3. Busca de Hiperparâmetros 
Foi utilizada a técnica de RandomizedSearchCV para realizar a busca de hiperparâmetros em um espaço definido para cada modelo. Cinco rodadas foram realizadas para cada modelo, com três folds de validação cruzada.


## 3. Resultados 
Os resultados foram avaliados com base na acurácia no conjunto de teste após cada rodada da busca de hiperparâmetros. Os melhores resultados foram:
- Decision Tree: Acurácia média de 0.774 (variação: 0.75 a 0.79);
- KNN: Acurácia média de 0.793 (variação: 0.783 a 0.798);
- SVM: Acurácia média de 0.777 (variação: 0.621 a 0.809);
- MLP: Acurácia média de 0.834 (variação: 0.817 a 0.843).

Análise da Curva de Aprendizado para KNN O modelo MLP apresentou o melhor desempenho geral, com a configuração de:
```
'max_iter': 400,
'learning_rate': 'adaptive',
'hidden_layer_sizes': (100, 50),
'alpha': 0.01, 'activation': 'tanh'
```
A curva de aprendizado indicou:
A acurácia de treinamento foi relativamente alta (acima de 0.834);
A acurácia de validação estabilizou em torno de 0.83 conforme o tamanho do conjunto de treino aumentou.

## 5. Conclusões 
O MLP foi o modelo de melhor desempenho para a base Covertype, superando os outros algoritmos em termos de acurácia. O uso de RandomizedSearchCV otimizou os hiperparâmetros dos modelos, mas também aumentou o tempo de execução. A curva de aprendizado do MLP mostrou que mais dados de treino podem beneficiar o modelo, embora ele já demonstra um bom desempenho com o conjunto limitado.

## 6. Recomendações Finais Para futuros estudos:
- Aumentar o conjunto de dados para observar a escalabilidade dos modelos;
- Considerar otimização adicional, como GridSearchCV para hiperparâmetros mais refinados.

## 7. Visualizações
### Gráfico de evolução do score por rodada para todos os modelos;

Curva de aprendizado para o modelo MLP mostrando as acurácias de treinamento e validação.
Anexos Os códigos e os gráficos estão disponíveis para referência e reprodução do estudo.



