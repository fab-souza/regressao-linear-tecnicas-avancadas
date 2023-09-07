# regressao-linear-tecnicas-avancadas

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/regressao-linear-tecnicas-avancadas)

| :placard: Vitrine.Dev |    |
| -------------  | --- |
| :sparkles: Nome        | **Regressão Linear: técnicas avançadas de modelagem**
| :label: Tecnologias | python
| :rocket: URL         | Notebook
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

![df](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/3cee8867-80a2-4fa3-9ef3-5491657045ce)

Com mais de 208 mil registros. Porém, decidi trabalhar com apenas seis colunas:
- Preço;
- Ano de fabricação;
- Quilômetros rodados;
- Potência do motor; 
- Tamanho do motor;
- e Número de portas.

![dados-head](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/a5847220-0ac1-4d04-b6ce-efea7c33c7c2)

Após tratá-los, por exemplo, fazendo a exclusão de dados nulos e discrepantes, iniciei minhas análises em um DataFrame com 203.813 registros. Começando pela estatística descritiva, observa-se que todas as colunas possuem a mesma quantidade de registros, na coluna *Preço*, os veículos vão de zł585,00 até quase 7 milhões de Zloty (moeda polonesa), achei o valor um pouco alto demais, que veremos com maior detalhe mais adiante. Em relação ao ano de fabricação, os veículos mais novos são de 2021, mas também há veículos de 1915. Já sobre os quilômetros rodados, o valor mínimo é de 1, onde podemos inferir que todos os veículos do DataFrame são usados.

![describe](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/609cad2a-fff5-4b7f-833f-28971bd07609)

Passando para a matriz de correlação, vemos que, em relação ao *Preço*, nossa variável dependente (Y), a *Potencia_motor* é a única que possui uma correlação maior do que 0,5. Em relação às variáveis *Ano_fabricação* e *Tamanho_motor*, vemos que também há uma associação positiva em relação ao *Preço*, enquanto para as variáveis *Km_rodado* e *Número_portas* há uma associação negativa. 

Podemos inferir que, quanto maior for a quilometragem rodada, o veículo precisará passar por uma análise mais rigorosa a cada manutenção, fator que pode jogar o preço de revenda para baixo. Já em relação ao número de portas, a inferência que consigo elaborar é em relação aos modelos dos carros: automóveis do tipo conversível/esportivo, que são os mais caros, possuem poucas portas. Por outro lado, também há veículos com preços mais acessíveis, que dão preferência à comodidade das pessoas, muitas vezes, oferecem mais espaço para passageiros, ou acomodação para transportar grandes objetos, consequentemente, eles precisam de um número maior de portas. Mas, não posso esquecer que há veículos, de duas portas, que **não** são do tipo conversível ou esportivo. Nesses casos, o carro oferece relativo conforto, baixo consumo de combustível e baixo custo de manutenção.

![matriz-corr](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/27d1d1dc-e8aa-4cfe-8dba-425576d3e481)

Ao fazer o **box-plot** dos *Preços*, vemos que o carro de quase 7 milhões está muito distante dos demais e decidi apagá-lo. Após a retirada do **outlier**, observa-se que o box-plot ainda possui uma assimetria, indicando uma maior concentração dos *Preços* a 0,0 do que a 2,5 (na escala e^6).

![box-plot](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/7182a8a6-72d5-42b6-8081-5f35a61d0f20)

![box-plot2](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/6a6df985-8e01-4a96-83b1-822a66c0cc32)

Passando para a distribuição de frequência dos *Preços*, vemos que o comportamento observado no box-plot se repete. Há mais carros com valores mais baixos, com aproximadamente o mesmo preço e seguindo um mesmo padrão, do que carros de luxo, que compõem a minoria e são mais caros. Isso faz com que ocorra problemas na criação do modelo de regressão, já que o ideal é trabalhar com dados que estejam distribuídos de forma simétrica, pois testes paramétricos assumem que os dados amostrais foram coletados de uma população com distribuição de probabilidade conhecida.

![frequencias](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/19c99d08-4b28-4048-a967-3ba3e1533fbb)

Para deixar a distribuição dos registros em um formato mais simétrico, apliquei a função matemática **logaritmo**, também conhecida como *log*, à todas as variáveis. 

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/731cb029-f66b-4e50-970c-dbff69bc475f)

Verificamos o resultado desta transformação ao plotar um novo gráfico de distribuição de frequência dos preços dos carros. Nele, vemos que os dados assumiram um comportamento mais simétrico.

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/438dda64-12dd-4137-a766-9695242d8f3f)

Em seguida, determinei que a variável *log_preco* seria *y*, enquanto as variáveis *log_fabricacao*, *log_quilometragem*, *log_potencia* e *log_portas* seriam *X*. Repare que não utilizei a variável *log_tamanho_motor*, pois quis fazer um modelo apenas com estas variáveis, analisaria seu resultado e depois criaria um novo modelo. Fiz a separação entre os conjuntos de **Treino** e **Teste**, atribuindo uma porcentagem de 25% aos teste e um *random_state* de 9876.

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.25, random_state = 9876)
```

Antes de criar o modelo, adicionei uma constante ao conjunto *X_train*, conhecido como *intercepto* ou *coeficiente linear do modelo*. Tive que fazer isso, porque em um modelo de regressão linear, a equação geralmente tem a forma:

*y = ax + b*
 
onde *a* é a inclinação (ou coeficiente) e *b* é a intercepção no eixo *y* (ou constante). A intercepção representa o valor esperado de *y* quando todas as variáveis independentes (*x*) são iguais a 0. Se eu não fizesse isso, os algoritmos de regressão linear, assumiriam que *b = 0* em *y = ax + b*, e ajustariam o modelo usando *b = 0* em vez de calcular o que ele deveria ser, com base nos dados.

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/ffb18c75-4c81-4604-bdde-a5f15e4300a3)















# Conclusão 🏁
















## Ferramentas utilizadas 🧰

<p>
  <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
  <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> 
  <a href="https://numpy.org/" target="_blank" rel="noreferrer"> <img src="https://numpy.org/images/logo.svg" alt="numpy" width="40" height="40"/> </a>
  <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a>
  <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a>
</p>
