
# Análise de resultados - ML

O presente case visa executar um modelo de Machine Learning para prever o preço total mensal das ações de uma empresa de telecomunicações nos próximos 12 meses. Por preço total mensal se define a soma dos valores de fechamento diários agrupados por mês. 

Ao final, busca-se analisar os resultados obtidos para assegurar se o modelo oferece a acuracidade fundamental para embasar estratégias. 
## Instalação

O único passo para a instalação é contar com o [Jupyter Notebook](https://jupyter.org), e se certificar de ter todas as bibliotecas necessárias instaladas.
## Como usar
Com todas as bibliotecas instaladas e com a base de dados no mesmo repositório da solução, basta executar o código no Jupyter Notebook.
## Desenvolvimento

### Escolha da base de dados
O objetivo inicial era escolher a base de dados no Kaggle para poder desenvolver o case com um contexto interessante.

Dentre a variedade oferecida, a escolhida foi a de [Vendas de Telecomunicações](https://www.kaggle.com/datasets/brmil07/telecommunications-company-stock-price?resource=download), trazendo informações como data, preço em abertura, fechamento, e os picos de variação, e a volumetria.

Desse mode, em uma análise inicial dos campos disponíveis, optei por somar o preço de fechamento das ações, agrupar por mês, e prever o comportamento nos próximos 12 meses.

### Escolha do modelo de ML
Após escolher o insumo para o case, comecei a busca pelo modelo Machine Learning ideal.

O primeiro método observado foi o modelo de **Regressão Linear**, disponível no seguinte  [vídeo](https://www.youtube.com/watch?v=20fbgWm5M2o). Embora tenha conseguido replicar o código, não obtive sucesso ao tentar implementar a previsão para datas futuras, portanto não avancei com a implementação na base escolhida.

O segundo método testado, ainda **Regressão Linear**, difere um pouco do anterior na escolha dos dados para teste e treino, e apresenta uma forma de prever valores futuros (conteúdo presente neste [notebook](https://github.com/vijendra-code/Time-Series-Forecasting/blob/master/Time%20Series%20Shampoo%20Sales%20Forecast.ipynb)). No entando, mesmo tendo sucesso na réplica, descartei a solução pois o modelo oferecia apenas uma linha reta de tendência, enquanto eu esperava uma solução mais precisa.

Por fim, escolhi o modelo ARIMA (Média Móvel Integrada Autoregressiva) presente neste [artigo](https://towardsdatascience.com/an-end-to-end-project-on-time-series-analysis-and-forecasting-with-python-4835e6bf050b), pois após a leitura ficou claro que era o mais próximo do desejado.

Vale salientar que esse foi o período mais demorado do case, comportamento explicado principalmente pela dificuldade de encontrar conteúdo resumido com a previsão de datas futuras (a esmagadora maioria parava no teste com as datas conhecidas), e pela pouca experiência com modelos de ML para poder escrever por mim próprio o código que faltava nos modelos mencionados.

Também é importante destacar a falta dos arquivos de soluções dos outros métodos, pois a implementação foi descartada ainda na fase de cópia do modelo.

### Codificação
Após a escolha, o primeiro passo foi replicar o código do artigo para testar a funcionalidade e entender um pouco do funcionamento. 

Com o arquivo funcionando, comecei a replicar o mesmo código fazendo ligeiras alterações para tornar a base escolhida por mim compatível ao código. 

### Resultados
Após a execução, o modelo previu o seguinte comportamento para os próximos 12 meses (conteúdo também disponível no [arquivo final de solução](https://github.com/ToxicOtter/Case-dados/blob/main/case.ipynb))

![Gráfico contendo o histórico de dados e a previsão para os próximos 12 meses](https://github.com/ToxicOtter/Case-dados/blob/main/images/grafico-previsao.png?raw=true)

![Tabela com as datas e valores da previsão para os próximos 12 meses](https://github.com/ToxicOtter/Case-dados/blob/main/images/previsao-mes.png?raw=true)


Abrindo os valores previstos, é perceptível que a diferença entre os valores mínimos e máximos da previsão já começa alta, e aumenta ainda mais de acordo com o maior prazo no futuro. 

![Tabela com as datas e valores mínimos e máximos da previsão para os próximos 12 meses](https://github.com/ToxicOtter/Case-dados/blob/main/images/previsao-min-max-mes.png?raw=true)

Um ponto que reforça a grande variação entre os valores previstos é o Erro Médio Quadrático (The Root Mean Squared Error). Conforme observado, a pontuação está distante do zero, o que minimamente cria um ponto de reflexão sobre o output do modelo.

**De forma geral, os resultados absolutos indicam que teremos uma evolução constante no valor mensal, com apenas algumas quedas, mas já retomando o crescimento**. 
## Conclusão
Por conta da grande margem de variação nos valores previstos e do valor do erro médio quadrático, é difícil cravar a precisão dos resultados e permitir que sejam utilizados como base para planejamentos.

Considerando a volumetria do histórico de dados dos anos anteriores, o ideal é propor uma previsão limitada à apenas um mês no futuro, a mudança do escopo mensal para diário e, em caso das duas soluções não melhorarem a precisão, reavaliar o modelo escolhido.
## Autor

- [Luan Lima Lopes (@ToxicOtter)](https://github.com/ToxicOtter)