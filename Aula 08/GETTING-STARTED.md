### Importando a biblioteca pandas e realizando a leitura do arquivo csv:

``` python
import pandas as pd
notas = pd.read_csv(‘ratings.csv’)
notas.head()
notas.shape
```

### Renomeando as colunas do dataFrame:

``` python
notas.columns = [‘usuarioID’, ‘filmeID’, ‘nota’, ‘momento’]
notas.head()
```

### Verificando os valores únicos das notas:

``` python
notas[‘nota’].unique()
```

### Contando quantas vezes cada valor de nota aparece:

``` python
notas[‘nota’].value_counts()
```

### Calculando o valor da média e da mediana das notas:

``` python
media = notas[‘nota’].mean()
mediana = notas[‘nota’].median()
print(f’Media {media} – Mediana {mediana}’)
```

### Plotando um histograma das notas:

``` python
notas[‘nota’].plot(kind=’hist’)
#outra forma de acessar a coluna ‘nota’ é notas.nota
```

### Exibindo diversas medidas dos dados das notas:

``` python
notas.nota.describe()
```

### Exibindo um boxplot utilizando a biblioteca seaborn:

``` python
import seaborn as sns
sns.boxplot(notas.nota)
```

Olhando os filmes do dataset MovieLens

``` python
filmes = pd.read_csv(‘movies.csv’)
filmes.columns = [‘filmeID’, ‘titulo’, ‘generos’]
filmes.head()
```

### Analisando algumas notas específicas por filme

``` python
#media das notas do filme de id igual a 1
notas.query(‘filmeID==1’).nota.mean()
#agrupando as medias por filme
medias_por_filme = notas.groupby(‘filmeID’).mean()[‘nota’]
medias_por_filme.head()
medias_por_filme.plot(‘kind=’hist’)
#distplot é o histograma da biblioteca seaborn
sns.distplot(medias_por_filme, bins=10) #bins é o numero de caixas
```

### O matplotlib é a maneira mais “baixo nivel” para plotar e tanto o pandas quanto o seaborn utilizam o pyplot

``` python
import matplotlib.pyplot as plt
plt.hist(medias_por_filme)
plt.title(“Histograma das médias por filmes”)
```