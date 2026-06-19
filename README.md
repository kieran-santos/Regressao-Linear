# Regressão Linear Simples

Trabalho desenvolvido para a disciplina de **Machine Learning**, com o objetivo de implementar uma **regressão linear simples do zero**, sem o uso de bibliotecas de Machine Learning (como `scikit-learn`), apenas com `numpy`.

O projeto está dividido em dois notebooks: um com um exemplo didático e simples, e outro aplicando o mesmo método a um conjunto de dados real do mercado imobiliário.

## Estrutura do projeto

```
.
├── regressao_basic.ipynb     # Regressão linear simples com dados de exemplo
├── dataset.csv                # Dados de exemplo (tamanho x preço)
├── regressao_houses.ipynb    # Regressão linear aplicada a dados reais de imóveis
└── kc_house_data.csv          # Dataset de vendas de imóveis (King County, EUA)
```

## Notebooks

### `regressao_basic.ipynb`

Implementação inicial da regressão linear simples, usada para entender o método de **mínimos quadrados** na prática:

- Carregamento dos dados do `dataset.csv`
- Separação das variáveis independente (X) e dependente (y)
- Cálculo manual dos coeficientes da reta (a e b) a partir das fórmulas de mínimos quadrados
- Estimativa de valores com a reta encontrada

O `dataset.csv` é um conjunto de dados simples com 10 amostras relacionando **tamanho** e **preço**.

### `regressao_houses.ipynb`

Aplicação do mesmo método de regressão linear, agora em um cenário mais próximo da realidade, usando o dataset **King County House Sales** (`kc_house_data.csv`):

- Leitura dos dados com `numpy`, usando as colunas `sqft_living` (área do imóvel) como variável independente (X) e `price` (preço) como variável dependente (y)
- Cálculo dos coeficientes da reta de regressão (a e b)
- Cálculo do **Coeficiente de Correlação de Pearson (r)**
- Cálculo do **Coeficiente de Determinação (R²)**
- Visualização gráfica dos dados reais junto com a reta de regressão, usando `matplotlib`

## Tecnologias utilizadas

- Python 3
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Pandas](https://pandas.pydata.org/)
- Jupyter Notebook

## Como executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/regressao-linear.git
   cd regressao-linear
   ```

2. Instale as dependências:
   ```bash
   pip install numpy matplotlib pandas
   ```

3. Abra os notebooks com Jupyter:
   ```bash
   jupyter notebook
   ```

4. Execute as células de `regressao_basic.ipynb` ou `regressao_houses.ipynb` em ordem.

>  Os arquivos `dataset.csv` e `kc_house_data.csv` precisam estar na mesma pasta dos respectivos notebooks para que a leitura dos dados funcione corretamente.

## Sobre o dataset `kc_house_data.csv`

Conjunto de dados público com informações sobre vendas de imóveis no condado de King, EUA (incluindo Seattle), contendo atributos como preço, área construída, número de quartos, banheiros, ano de construção, entre outros. Neste projeto, foram utilizadas apenas as colunas `sqft_living` e `price` para a regressão linear simples.

## Observações

Este projeto tem fins **didáticos**, com foco em compreender o funcionamento matemático da regressão linear (mínimos quadrados, correlação e coeficiente de determinação) implementando os cálculos manualmente, em vez de utilizar bibliotecas prontas de Machine Learning.
<br><br><br>


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Regressão Múltipla

Trabalho desenvolvido para a disciplina de [Machine Learning], com o objetivo de implementar uma **regressão linear múltipla do zero**, sem o uso de bibliotecas de Machine Learning (como `scikit-learn`), apenas com `numpy`.

O projeto está dividido em dois notebooks: um implementando o método da Equação Normal e aplicando-o a um conjunto de dados real do mercado imobiliário, e outro explorando quais variáveis realmente ajudam a explicar o preço de um imóvel.

## Estrutura do projeto

```
.
├── regres_mult_basic.ipynb       # Regressão linear múltipla com dados de exemplo e dados reais
├── exercicio_regres_mult.ipynb   # Exercício de exploração de variáveis na regressão múltipla
└── kc_house_data.csv              # Dataset de vendas de imóveis (King County, EUA)
```

## Notebooks

### `regres_mult_basic.ipynb`

Implementação da regressão linear múltipla usando a **Equação Normal** (`β = (XᵀX)⁻¹ Xᵀy`) para encontrar os coeficientes:

- Um primeiro exemplo simples e controlado (3 amostras, 2 features), só para validar que a equação normal funciona corretamente
- Aplicação no `kc_house_data.csv`, prevendo o `price` a partir de `bedrooms`, `bathrooms` e `sqft_living`
- Inclusão da coluna de intercepto (β₀) na matriz X com `np.c_[np.ones(m), X_features]`
- Teste de previsão comparando o preço real e o preço previsto para o primeiro imóvel do dataset

### `exercicio_regres_mult.ipynb`

Exercício de exploração: investigar quais variáveis do dataset realmente ajudam a explicar o `price`, e quais combinações de variáveis reduzem o erro do modelo.

- Inspeção do dataset com `pandas` (`df.info()`, `df.head()`) para entender os tipos de cada coluna
- Tentativa de incluir a variável `floors` como preditora além de `bedrooms` e `bathrooms`
- **Ponto de atenção:** ao ler a coluna `floors` diretamente com `np.genfromtxt`, os valores vêm como `nan`. Isso propaga `nan` para a matriz `XᵀX`, tornando-a não inversível e fazendo com que todos os coeficientes calculados também sejam `nan`
- Esse resultado evidencia a importância de **tratar/validar os tipos de dados antes de aplicar a Equação Normal**, já que colunas com strings, valores ausentes ou mal formatados quebram o cálculo da matriz inversa

> Esse notebook documenta um erro real do processo de aprendizado (e não um modelo funcional), mantido propositalmente para registrar a investigação sobre qual conjunto de variáveis é viável de usar.

## Tecnologias utilizadas

- Python 3
- [NumPy](https://numpy.org/)
- [Pandas](https://pandas.pydata.org/)
- Jupyter Notebook

## Como executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/regressao-multipla.git
   cd regressao-multipla
   ```

2. Instale as dependências:
   ```bash
   pip install numpy pandas
   ```

3. Abra os notebooks com Jupyter:
   ```bash
   jupyter notebook
   ```

4. Execute as células de `regres_mult_basic.ipynb` ou `exercicio_regres_mult.ipynb` em ordem.

> O arquivo `kc_house_data.csv` precisa estar na mesma pasta dos notebooks para que a leitura dos dados funcione corretamente.

## Sobre o dataset `kc_house_data.csv`

Conjunto de dados público com informações sobre vendas de imóveis no condado de King, EUA (incluindo Seattle), contendo atributos como preço, área construída, número de quartos, banheiros, ano de construção, entre outros. Neste projeto, foram utilizadas combinações das colunas `bedrooms`, `bathrooms`, `sqft_living` e `floors` para prever a coluna `price`.

## Observações

Este projeto tem fins **didáticos**, com foco em compreender o funcionamento matemático da regressão linear múltipla (Equação Normal) implementando os cálculos manualmente, em vez de utilizar bibliotecas prontas de Machine Learning. Os erros e resultados inesperados (como o caso do `exercicio_regres_mult.ipynb`) foram mantidos intencionalmente, pois fazem parte do processo de aprendizado sobre tratamento de dados antes de aplicar um modelo.
