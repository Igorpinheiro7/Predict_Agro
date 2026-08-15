# Modelagem Preditiva na Agricultura
<img width="530" height="354" alt="Image" src="https://github.com/user-attachments/assets/038008dd-04d9-48a0-acc3-2e3ffbd31174" />

# 🎯 Objetivo
O objetivo principal deste projeto é ajudar agricultores a escolher a cultura ideal (crop) para o seu solo com base em métricas de nutrientes e propriedades químicas (Nitrogênio N, Fósforo P, Potássio K e pH).

# Importação dos dados para análise

<img width="870" height="646" alt="Image" src="https://github.com/user-attachments/assets/9c4f4758-2980-4bb4-9c2b-2b946bb83d8c" />

<img width="885" height="642" alt="Image" src="https://github.com/user-attachments/assets/0580d07e-3b33-435b-8abf-1048ff88a9fa" />

# Análise por Característica Individual

Este bloco de código abaixo foi responsável por treinar e avaliar um modelo de regressão logística para cada uma das características (N, P, K, pH) separadamente, a fim de identificar qual delas tem o maior poder preditivo.

<img width="728" height="660" alt="Image" src="https://github.com/user-attachments/assets/546490cc-cb17-4a3c-84b6-cd8f99222a5d" />

<img width="840" height="257" alt="image" src="https://github.com/user-attachments/assets/4977a1b9-b88e-4ae6-b9cd-4b5098ef9249" />

Como pode ser visto, a característica 'K' (Potássio) possui o F1-Score mais alto, confirmando que é a característica individual mais importante para o desempenho preditivo.

**Interpretação:**

*   **Potássio (K)**: Com um F1-Score de **0.2390**, o Potássio (K) demonstrou ser a característica individual mais preditiva entre N, P e K para a seleção da cultura. Isso significa que, quando utilizado isoladamente, o nível de K no solo é o que melhor ajuda o modelo a classificar corretamente a cultura ideal.
*   **Fósforo (P)**: O Fósforo (P) teve um F1-Score de **0.1476**, indicando um poder preditivo menor que o Potássio, mas ainda superior ao Nitrogênio.
*   **Nitrogênio (N)**: O Nitrogênio (N) apresentou o menor F1-Score de **0.0915** entre os três, sugerindo que, por si só, é o menos eficaz para prever a cultura neste dataset.

# Características padronizadas

<img width="840" height="637" alt="image" src="https://github.com/user-attachments/assets/3a4c7b04-dd51-4450-ab5f-05e0b349e313" />
<img width="1100" height="701" alt="image" src="https://github.com/user-attachments/assets/b6d85934-0ee1-4ad2-b05e-7f857cd1d819" />

Com base na análise individual, o **Potássio (K)** é a característica do solo mais importante e preditiva dentre N, P e K para determinar a cultura mais adequada. No entanto, é crucial lembrar, conforme demonstrado no modelo com **Todas as Características Padronizadas**, que a combinação e padronização de todos os nutrientes (N, P, K e pH) oferece um desempenho preditivo significativamente superior, atingindo um F1-Score de **0.6475**. Isso reforça que, embora K seja o melhor isoladamente, o cenário mais eficaz para o agricultor envolve a medição e análise conjunta de todos os parâmetros.

# Matriz de Correlação de Nutrientes

<img width="688" height="243" alt="image" src="https://github.com/user-attachments/assets/4b634fdf-9257-4e3e-acb6-62e63bd0ecdf" />
<img width="637" height="528" alt="Image" src="https://github.com/user-attachments/assets/4523a2aa-9978-4545-870a-cc8e27ec85d7" />


