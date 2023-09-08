# regressao-linear-tecnicas-avancadas

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=FINALIZADO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/regressao-linear-tecnicas-avancadas)

| :placard: Vitrine.Dev |    |
| -------------  | --- |
| :sparkles: Nome        | **Regressão Linear: técnicas avançadas de modelagem**
| :label: Tecnologias | python
| :rocket: URL         | [Notebook](https://www.kaggle.com/code/fabianadesouza/regressao-linear-2-preco-de-carros) no Kaggle
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

O primeiro modelo, fiz através de uma estimação com *statsmodels* e para fazer sua avaliação, fiz um ‘*.summary()*’. Ele apresenta diversas informações estatísticas, por exemplo, no *R-squared* vemos que 72,8% da variação no *preço dos carros* pode ser explicada pelas variáveis independentes no modelo, também temos o *F-statistic* e o *Prob (F-statistic)*, que são o *teste F* e a *Aceitação*, respectivamente. Ter um teste F alto, no caso deste modelo é de 99790, e uma Aceitação menor do que 0.05, significa que o modelo de regressão é estatisticamente significativo, pois isso quer dizer que posso rejeitar a hipótese nula e concluir que pelo menos uma das variáveis independentes é significativamente relacionada à variável dependente.

![image](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/aafb1fdb-e6ba-4536-8379-5cfa9641a339)

Para testar, fiz um novo modelo, com as cinco variáveis no *X* e o resultado não foi muito diferente. O *R-squared* subiu para 0.728, a *Aceitação* se manteve em 0.00 e o *teste F* caiu para 81930, mas continuou um valor alto, indicando que também é um bom modelo.

![summary](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/6ffea9a8-9e85-4558-a010-e04b2eb106c2)

Mesmo com estes dois modelos, criei outro usando *LinearRegression*, do *scikit-learn*. Reaproveitei os conjuntos *X* e *y*, que já havia criado, para estimar o ajuste do modelo. Calculei o R² (R-squared) do conjunto de treino e obtive *0.728* de retorno.

![r2-treino](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/5af8109a-2e65-43ce-b198-e8acf504ddc3)

Gerei previsões para o conjunto de teste, calculei seu R² e obtive *0.731* de retorno. Considero o resultado positivo, já que ele não apresentou um valor muito diferente do R² calculado anteriormente.

![r2-teste](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/8ac5861c-a3ea-4476-8608-ba699ae60c69)

Após obter os resultados, fiz uma previsão pontual. Ou seja, forneci os dados do veículo e o modelo me retornou seu valor. Peguei os valores da primeira linha do conjunto de teste, armazenei seus registros em uma variável e passei ela para o último modelo treinado. O retorno foi de *10.14*, porque os valores estão na escala logarítmica e para obter o valor real do veículo, precisei inverter a transformação. Após aplicar a função exponencial ao resultado, obtive *25529.68*, que segundo o conversor do Google, é aproximadamente R$29.402,00.

![zt](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/f0c522e6-4ba6-4931-b8b6-8d2fc96532e0)

Também forneci novos dados para o modelo calcular o valor do automóvel. Armazenei nas variáveis *Ano_fabricacao*, *Km_rodado*, *Potencia_motor*, *Tamanho_motor* e *Numero_portas* alguns valores, os transformei em valores logarítmicos, passei para o modelo e inverti a transformação do valor calculado.

![precos](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/e379b081-8b07-4c5a-9409-85baee312cf3)

Fiz uma breve interpretação dos coeficientes do modelo. Na seguinte tabela, o intercepto representa o efeito médio em *y* (preço do carro) tendo todas as variáveis explicativas excluídas do modelo, ou seja, é o valor esperado da variável dependente quando todas as variáveis independentes são iguais a zero. No entanto, o *-1156.73*, após passar pela exponenciação, é 0. Os demais dados significam que um acréscimo de 1% àquela variável, haverá um acréscimo, ou decréscimo, no preço do veículo. Mantendo as demais variáveis, ao aumentar o ano de fabricação, potência do motor ou tamanho do motor causa um aumento de 152,67%, 0,76% e 0,45%, respectivamente. Enquanto que aumentar a quilometragem ou número de portas, causa um decréscimo de *-0,08* e *-0.29*, respectivamente, no preço.

![tab](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/8e67b2a3-f0e9-41bd-840a-2bacc667b706)

Para finalizar, plotei um gráfico comparando o preço *real* com o valor *previsto* pelo modelo. Nele, vemos que o lado esquerdo do gráfico está com um comportamento disperso, enquanto outra parte está mais uniforme, seguindo uma linha diagonal. Diante este comportamento, posso inferir que o modelo está funcionando bem para alguns valores, mas não para outros e isso pode acontecer por razões como a presença de outliers ou a falta de dados em algumas faixas de valores.

![grafico](https://github.com/fab-souza/regressao-linear-tecnicas-avancadas/assets/67301805/ef2a6ea6-177c-4e19-9e53-4e89df0ba40d)

# Conclusão 🏁

Bom… Infelizmente, não obtive um modelo de previsão de preço que chegou próximo ao que foi feito durante o curso. Mesmo acertando mais do que 70% dos registros de teste, o gráfico entre **Real X Previsto** mostrou que o modelo não está funcionando bem em alguns casos.

Para melhorar o resultado, poderia verificar os outliers e considerar removê-los ou tratá-los de alguma forma. Ou verificar se há dados suficientes em todas as faixas de valores das variáveis independentes. Se encontrasse lacunas, poderia coletar mais dados nessas faixas. Ou até mesmo tentar ajustar os parâmetros do modelo ou experimentar diferentes algoritmos de *machine learning* para ver se consigo obter um ajuste melhor, algo que foi abordado em outros cursos desta formação e farei futuramente.


---

Muito obrigada por chegar até aqui e até a próxima 🤗


## Ferramentas utilizadas 🧰

<p>
  <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
  <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> 
  <a href="https://numpy.org/" target="_blank" rel="noreferrer"> <img src="https://numpy.org/images/logo.svg" alt="numpy" width="40" height="40"/> </a>
  <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a>
  <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a>
 <a href="https://www.statsmodels.org/stable/index.html" target="_blank" rel="noreferrer"> <img src="https://www.statsmodels.org/stable/_images/statsmodels-logo-v2-no-text.svg" alt="statsmodels" width="40" height="40"/> </a>
</p>
