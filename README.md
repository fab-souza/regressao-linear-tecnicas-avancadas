# regressao-linear-tecnicas-avancadas

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/regressao-linear-tecnicas-avancadas)

| :placard: Vitrine.Dev |    |
| -------------  | --- |
| :sparkles: Nome        | **Regressão Linear: técnicas avançadas de modelagem**
| :label: Tecnologias | python
| :rocket: URL         | 
| :fire: Desafio     | Conteúdo do [curso](https://www.alura.com.br/curso-online-data-science-modelo-regressao-linear-assimetria-statsmodel)

![](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/9b9aa0b1-2c78-4800-ac0f-c5c357e5b70d#vitrinadev)

# Sobre o curso 📚
Continuando a pôr em prática o que aprendi na formação Data Science/Estatística da [Alura](https://www.alura.com.br/), neste curso, também ministrado pelo instrutor [Rodrigo Dias](https://www.linkedin.com/in/rodrigo-fernando-dias-118181120/), aprendi novas técnicas de:

- análises preliminares do dataset, incluindo informações do DataFrame Pandas e avaliações descritivas dos dados; 
- mais análises gráficas, como comportamento da variável dependente, box-plot e distribuição de frequências; 
- transformação de variáveis, destacando sua importância e o uso de transformações logarítmicas;
- e regressão linear, usando StatsModels e Scikit Learn, abrangendo a estimativa do modelo, interpretação dos coeficientes, análises gráficas e testes formais.

Para pôr em prática estes conteúdos, utilizamos um dataset de uma amostra aleatória de 5000 imóveis disponíveis para venda no município do Rio de Janeiro. Ele é composto por quatro variáveis: 

- **Valor** - Preço (R$) de oferta do imóvel
- **Area** - Área do imóvel em m²
- **Dist_Praia** - Distância do imóvel até a praia (km) (em linha reta)
- **Dist_Farmacia** - Distância do imóvel até a farmácia mais próxima (km) (em linha reta)

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/2045aed8-6ca6-40d5-8d5f-518afc2ebf58)

Ao longo do curso, desenvolvemos alguns modelos de predição de valor e finalizando com a predição de um valor a partir de dados pontuais.

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/b6ae81d7-cd2f-495a-b2db-023956357480)




# Minha prática 👩🏻‍💻 

Para praticar o que aprendi, utilizei um dataset disponível no [Kaggle](https://www.kaggle.com) sobre [preço de carros na Polônia](https://www.kaggle.com/datasets/bartoszpieniak/poland-cars-for-sale-dataset). Originalmente, composto por mais de 20 colunas:

* ID - ID do carro
* Price - preço do veículo
* Currency - moeda de negociação do veículo (złoty polenês ou euro)
* Condition - condição, novo ou usado
* Vehicle_brand - marca do fabricante
* Vehicle_model - modelo do veículo
* Vehicle_generation - geração do veículo
* Vehicle_version - versão do veículo
* Production_year - ano de fabricação
* Mileage_km - quilometragem rodada
* Power_HP - potência do motor, em horse power (cavalo vapor)
* Displacement_cm3 - tamanho do motor, em centímetro cúbico
* Fuel_type - tipo de combustível
* CO2_emissions - emissão de CO2, em g/km
* Drive - tipo de condução do carro
* Transmission - ipo de transmissão
* Type - estilo do carro
* Doors_number - número de portas
* Colour - cor do veículo
* Origin_country - país de origem do carro
* First_owner - se o carro está no primeiro proprietário
* First_registration_date - data do primeiro registro de compra
* Offer_publication_date - data de publicação da venda
* Offer_location - endereço do vendedor
* Features - características do carro (ABS, airbag, sensores de estacionamento, etc)

Com mais de 208 mil registros. Porém, decidi trabalhar com apenas seis colunas:
- Preço;
- Ano de fabricação;
- Quilômetros rodados;
- Potência do motor; 
- Tamanho do motor;
- e Número de portas.











# Conclusão 🏁
















## Ferramentas utilizadas 🧰

<p>
  <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
  <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> 
  <a href="https://numpy.org/" target="_blank" rel="noreferrer"> <img src="https://numpy.org/images/logo.svg" alt="numpy" width="40" height="40"/> </a>
  <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a>
  <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a>
</p>
