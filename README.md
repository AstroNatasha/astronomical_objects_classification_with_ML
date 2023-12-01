# Classificando objetos astronômicos utilizando técnicas de Machine Learning

## Resumo



## Sobre o repositório

- ‘k_means_clustering_and_decision_tree_objects_classification.ipynb’: Código em Python que realiza as classificações

## Dependências

- numpy
- matplotlib
- pandas
- astroquery
- sklearn

## Como usar o código

Clone este repositório ou baixe o arquivo ‘k_means_clustering_and_decision_tree_objects_classification.ipynb’ para o seu ambiente de trabalho. Execute o código Python ‘k_means_clustering_and_decision_tree_objects_classification.ipynb’ em seu ambiente. Você pode fazer isso usando um ambiente Python de sua escolha, como Jupyter Notebook ou um ambiente de desenvolvimento integrado (IDE).

Primeiro, certifique-se de que os arquivos de imagem estão presente no mesmo diretório que o arquivo Python. As bibliotecas devem estar instaladas em seu ambiente Python.

## Metodologia


### K-Means Clusternig - Modelo não-supervisionado

Em nosso caso, K-Means será separado em K=4, pois queremos fazer subgrupos dentro dos grupos "cLabels" definidos pela tabela. Este metodo separa nossos dados em aglomerados de acordo com similaridades nos parâmetros dos dados após várias iterações. Primeiro os aglomerados serão definidos de acordo com a posição arbitrária dos centróides. Depois, a média das distâncias para cada aglomerado é calculada. Em seguida, os centróides são ajustados novamente até a média parar de variar.

### Decision Tree - Modelo supervisionado

A Árvores de Decisão irá utilizar os dados da amostra, de forma a separar os dados o máximo possível. Após cada separação feita, um novo parâmetro é utilizado para tal. Por este modelo ser supervisionado, o teste e treino foi separado em uma proporção de 70/30.


## Conclusão

O fato de termos um número de dados razoavelmente grande (em torno de 6k) neste catálogo possibilitou a aplicação das técnicas. Há uma correlação entre as cores no optico e infravermelho dos objetos com suas magnitudes. A etapa de clusterização foi útil para ter alguns insights iniciais, assim como as estatísticas básicas da tabela. A separação de clusters foi um sucesso. Depois da primeira clusterização, uma tentativa para cada classificação de objetos (cLabels) foi realizada, afim de comparar seus posicionamentos e testar novas separações dentro de cada classificação. Já na etapa da árvore de decisão, houve um bom resultado, com precisões boas e obtendo poucas classificações falsas (falso positivo/falso negativo). A maior concentração de falsos ocorreu na classificação dos objetos considerados desconhecidos/candidatos, possivelmente por já não serem bem identificados nos próprios catálogos e pelo número baixo de amostras de dados presentes. Para estudos futuros, sugiro um estudo mais aprofundado sobre a relação entre os objetos desconhecidos e EM, uma vez que houve certa confusão ao classificar estes objetos.

## Referências
Trevor Z. Dorn-Wallenstein et al 2021 ApJ 913 32
