# 🌾 Previsão de Culturas Agrícolas com Machine Learning
<img width="530" height="354" alt="Image" src="https://github.com/user-attachments/assets/038008dd-04d9-48a0-acc3-2e3ffbd31174" />

# 📑 Estudo de Caso

Medir métricas essenciais do solo, como níveis de nitrogênio, fósforo, potássio e valor de pH, é fundamental para avaliar as condições do solo. Porém, esse processo pode ser caro e demorado, levando agricultores a priorizar quais métricas medir conforme o orçamento disponível.

Ao decidir qual cultura plantar a cada safra, os agricultores têm várias opções. O objetivo principal é maximizar a produtividade, levando em conta diferentes fatores. Um fator crucial que afeta o crescimento das culturas é a condição do solo no campo, que pode ser avaliada medindo elementos básicos como os níveis de nitrogênio e potássio. Cada cultura tem uma condição de solo ideal que favorece o desenvolvimento e a produtividade máximos.

Um agricultor nos procurou para ajudar a escolher a melhor cultura para o seu campo. Ele forneceu um conjunto de dados chamado soil_measures.csv, que contém:

"N": proporção de nitrogênio no solo
"P": proporção de fósforo no solo
"K": proporção de potássio no solo
valor de "pH" do solo
"crop": valores categóricos contendo várias culturas.
Cada linha desse conjunto de dados representa diversas medidas do solo em um determinado campo. Com base nessas medições, qual a cultura indicada na coluna "crop", é a melhor escolha para aquele campo.

# 🎯 Objetivo
O objetivo principal deste projeto é ajudar agricultores a escolher a cultura ideal (crop) para o seu solo com base em métricas de nutrientes e propriedades químicas (Nitrogênio N, Fósforo P, Potássio K e pH).

# 📊 Importação dos dados para análise

<img width="870" height="646" alt="Image" src="https://github.com/user-attachments/assets/9c4f4758-2980-4bb4-9c2b-2b946bb83d8c" />

<img width="885" height="642" alt="Image" src="https://github.com/user-attachments/assets/0580d07e-3b33-435b-8abf-1048ff88a9fa" />

# 🔍 Análise por Característica Individual

Este bloco de código abaixo foi responsável por treinar e avaliar um modelo de regressão logística para cada uma das características (N, P, K, pH) separadamente, a fim de identificar qual delas tem o maior poder preditivo.

<img width="728" height="660" alt="Image" src="https://github.com/user-attachments/assets/546490cc-cb17-4a3c-84b6-cd8f99222a5d" />

<img width="840" height="257" alt="image" src="https://github.com/user-attachments/assets/4977a1b9-b88e-4ae6-b9cd-4b5098ef9249" />

Como pode ser visto, a característica 'K' (Potássio) possui o F1-Score mais alto, confirmando que é a característica individual mais importante para o desempenho preditivo.

**Interpretação:**

*   **Potássio (K)**: Com um F1-Score de **0.2390**, o Potássio (K) demonstrou ser a característica individual mais preditiva entre N, P e K para a seleção da cultura. Isso significa que, quando utilizado isoladamente, o nível de K no solo é o que melhor ajuda o modelo a classificar corretamente a cultura ideal.
*   **Fósforo (P)**: O Fósforo (P) teve um F1-Score de **0.1476**, indicando um poder preditivo menor que o Potássio, mas ainda superior ao Nitrogênio.
*   **Nitrogênio (N)**: O Nitrogênio (N) apresentou o menor F1-Score de **0.0915** entre os três, sugerindo que, por si só, é o menos eficaz para prever a cultura neste dataset.

# 📏 Características padronizadas

<img width="840" height="637" alt="image" src="https://github.com/user-attachments/assets/3a4c7b04-dd51-4450-ab5f-05e0b349e313" />
<img width="1100" height="701" alt="image" src="https://github.com/user-attachments/assets/b6d85934-0ee1-4ad2-b05e-7f857cd1d819" />

Com base na análise individual, o **Potássio (K)** é a característica do solo mais importante e preditiva dentre N, P e K para determinar a cultura mais adequada. No entanto, é crucial lembrar, conforme demonstrado no modelo com **Todas as Características Padronizadas**, que a combinação e padronização de todos os nutrientes (N, P, K e pH) oferece um desempenho preditivo significativamente superior, atingindo um F1-Score de **0.6475**. Isso reforça que, embora K seja o melhor isoladamente, o cenário mais eficaz para o agricultor envolve a medição e análise conjunta de todos os parâmetros.

# 🌱 Matriz de Correlação de Nutrientes

<img width="688" height="243" alt="image" src="https://github.com/user-attachments/assets/4b634fdf-9257-4e3e-acb6-62e63bd0ecdf" />
<img width="637" height="528" alt="Image" src="https://github.com/user-attachments/assets/4523a2aa-9978-4545-870a-cc8e27ec85d7" />

### Explicação da Matriz de Correlação entre Nutrientes do Solo

A matriz de correlação (apresentada no heatmap anterior) nos mostra a relação linear entre cada par de variáveis numéricas no seu conjunto de dados. Cada célula na matriz contém um coeficiente de correlação, que varia de -1 a 1.

*   **1 (vermelho forte)**: Indica uma correlação positiva perfeita. Quando uma característica aumenta, a outra também aumenta na mesma proporção.
*   **-1 (azul forte)**: Indica uma correlação negativa perfeita. Quando uma característica aumenta, a outra diminui na mesma proporção.
*   **0 (cores claras/neutras)**: Indica nenhuma correlação linear. As características não têm uma relação linear clara.

#### Interpretando o Heatmap:

*   **Diagonal**: Os valores na diagonal são sempre **1.00** porque uma variável está perfeitamente correlacionada consigo mesma.
*   **Cores**: Cores mais quentes (vermelho) indicam correlações positivas mais fortes, enquanto cores mais frias (azul) indicam correlações negativas mais fortes. Tons mais claros indicam correlações mais fracas.

#### Análise das Relações:

Vamos analisar as correlações mais notáveis:

*   **Fósforo (P) e Potássio (K)**: Observamos um valor de **0.74** entre P e K. Isso indica uma **forte correlação positiva**. Em solos onde o nível de Fósforo é alto, é provável que o nível de Potássio também seja alto, e vice-versa. Isso é uma relação importante a ser considerada.

*   **Nitrogênio (N)**: O Nitrogênio tem correlações relativamente fracas com as outras características:
    *   **-0.23** com Fósforo (P): Uma correlação negativa fraca, sugerindo que um aumento em N pode estar ligeiramente associado a uma diminuição em P, mas a relação não é forte.
    *   **-0.14** com Potássio (K): Uma correlação negativa muito fraca, quase insignificante.
    *   **0.10** com pH: Uma correlação positiva muito fraca, quase insignificante.
    Isso sugere que a quantidade de Nitrogênio no solo não varia de forma linear significativa com os níveis de P, K ou pH, sendo mais independente dessas variáveis.

*   **pH**: O pH do solo mostra correlações fracas com os outros nutrientes:
    *   **-0.14** com Fósforo (P).
    *   **-0.17** com Potássio (K).
    *   **0.10** com Nitrogênio (N).
    Esses valores indicam que, embora haja pequenas tendências (negativas com P e K, positiva com N), o pH não tem uma relação linear forte com nenhum dos três nutrientes. Ou seja, o pH do solo não é um forte preditor dos níveis de N, P ou K de forma linear.

Em resumo, a relação mais notável e significativa é a **forte correlação positiva entre Fósforo (P) e Potássio (K)**. As outras características (N e pH) têm relações mais fracas entre si e com P e K. Esta análise pode ser útil para entender como os nutrientes interagem no solo.

# 🧪 Análise Comparativa entre Nitrogênio (N), Fósforo (P) e Potássio (K)

<img width="1053" height="281" alt="image" src="https://github.com/user-attachments/assets/d583c39c-6bdc-442f-b953-dcd6b72f5bc5" />
<img width="1280" height="641" alt="image" src="https://github.com/user-attachments/assets/2bcce139-5cc2-4cde-b47d-8ef4899210c8" />
<img width="790" height="490" alt="Image" src="https://github.com/user-attachments/assets/bc6d84cd-8de1-4f5d-a843-ceac1989a6fa" />

**Interpretação:**

Potássio (K): Com um F1-Score de 0.2390, o Potássio (K) demonstrou ser a característica individual mais preditiva entre N, P e K para a seleção da cultura. Isso significa que, quando utilizado isoladamente, o nível de K no solo é o que melhor ajuda o modelo a classificar corretamente a cultura ideal.
Fósforo (P): O Fósforo (P) teve um F1-Score de 0.1476, indicando um poder preditivo menor que o Potássio, mas ainda superior ao Nitrogênio.
Nitrogênio (N): O Nitrogênio (N) apresentou o menor F1-Score de 0.0915 entre os três, sugerindo que, por si só, é o menos eficaz para prever a cultura neste dataset.

**Solução:**

Com base na análise individual, o Potássio (K) é a característica do solo mais importante e preditiva dentre N, P e K para determinar a cultura mais adequada. No entanto, é crucial lembrar, conforme demonstrado no modelo com Todas as Características Padronizadas, que a combinação e padronização de todos os nutrientes (N, P, K e pH) oferece um desempenho preditivo significativamente superior, atingindo um F1-Score de 0.6475. Isso reforça que, embora K seja o melhor isoladamente, o cenário mais eficaz para o agricultor envolve a medição e análise conjunta de todos os parâmetros.
