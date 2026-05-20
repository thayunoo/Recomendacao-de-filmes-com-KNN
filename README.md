# 🎬 Sistema de Recomendação de Filmes com KNN

Sistema de recomendação de filmes e séries baseado no algoritmo 
K-Nearest Neighbors (KNN), utilizando dados do IMDb para sugerir 
obras com base em gênero, ano de lançamento, duração e número de 
avaliações.

---

## 📋 Sobre o Projeto

Com a ascensão dos serviços de streaming, encontrar obras que 
correspondam ao gosto pessoal tornou-se um desafio diante da 
enorme quantidade de títulos disponíveis. Este projeto oferece 
uma solução baseada em Machine Learning, recomendando filmes e 
séries de forma personalizada a partir das preferências do usuário.

---

## 🗂️ Base de Dados

Os dados utilizados são provenientes do **IMDb (Internet Movie 
Database)**, uma das maiores fontes de informações sobre filmes 
e programas de TV do mundo, contendo atributos como:

- Gênero(s)
- Ano de lançamento
- Duração da sessão (em minutos)
- Número de avaliações

---

## ⚙️ Como Funciona

O algoritmo utiliza o **KNN (K-Nearest Neighbors)**, que 
classifica cada título calculando sua distância em relação 
aos vizinhos mais próximos no espaço de atributos. Os títulos 
com características mais similares às preferências fornecidas 
são retornados como recomendações.

O valor de **K** (número de vizinhos considerados) impacta 
diretamente o desempenho:
- **K pequeno** → mais sensível a ruídos (risco de overfitting)
- **K grande** → mais robusto, porém pode generalizar demais 
(risco de underfitting)

---

## 🚀 Como Usar

### 1. Instale as dependências

```bash
pip install pandas scikit-learn statsmodels openpyxl
```

### 2. Execute o notebook e ajuste os parâmetros

No dataframe de entrada, defina suas preferências:
- Atributos **binários** (0 ou 1): gêneros como Action, Comedy, 
Drama, Horror, etc.
- Atributos **numéricos**: `startYear`, `runtimeMinutes`, 
`numVotes`

```python
new_movie = pd.DataFrame({
    'isAdult': [0],
    'startYear': 2000,
    'runtimeMinutes': 70,
    'numVotes': 1000,
    'Action': 0,
    'Sport': 1,
    # ... demais gêneros
})

recommended_movies = recommend_movies(new_movie.values[0])
print(recommended_movies)
```

### 3. Receba as recomendações

O sistema retorna os **20 títulos mais próximos** às 
características fornecidas.

---

## 🗃️ Estrutura do Projeto

```plaintext
📦 projeto-recomendacao-filmes
 ┣ 📄 Dados.xlsx          # Base de dados IMDb
 ┣ 📄 recomendacao.ipynb  # Notebook principal
 ┗ 📄 README.md
```
---

## 🛠️ Tecnologias Utilizadas

| Biblioteca | Uso |
|---|---|
| `pandas` | Manipulação de dados |
| `scikit-learn` | Algoritmo KNN e normalização |
| `statsmodels` | Suporte estatístico |

---

## ⚠️ Limitações

- Base de dados limitada a 1.000 registros por padrão 
(ajustável via `nrows`)
- Atributos como diretor, elenco e sinopse não foram incluídos 
por restrições de acesso aos dados
- As probabilidades retornadas são baseadas em similaridade de 
atributos, não em avaliações subjetivas do usuário

---

## 📚 Referências

- [Scikit-learn — Nearest Neighbors](https://scikit-learn.org/stable/modules/neighbors.html)
- [IMDb Non-Commercial Datasets](https://developer.imdb.com/non-commercial-datasets/)
- [KNN Algorithm — GeeksforGeeks](https://www.geeksforgeeks.org/k-nearest-neighbours/)
