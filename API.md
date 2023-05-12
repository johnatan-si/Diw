
# Consumindo uma API com JavaScript

Você aprenderá como consumir uma API utilizando JavaScript. Utilizemos a linguagem JavaScript e HTML para criar uma aplicação web simples que faz requisições HTTP para a API OpenWeatherMap e exibe os dados do clima, incluindo temperatura e dia da semana, na página.

## Passo 1: Criando o arquivo HTML

1.  Crie um novo arquivo chamado `index.html` e abra-o no seu editor de texto ou IDE.
2.  Adicione o seguinte código HTML básico ao arquivo:

```<!DOCTYPE html>
<html>
<head>
    <title>Consumindo API</title>
    <script src="script.js"></script>
</head>
<body>
    <h1>Consumindo API</h1>
    <div id="result"></div>
</body>
</html>
```

Neste código, estamos criando uma página HTML com um título, um cabeçalho e uma div vazia onde exibiremos os resultados da API. Também estamos incluindo um arquivo JavaScript chamado `script.js` usando a tag `<script>`.

 ## Passo 2: Criando o arquivo JavaScript
 1.  Crie um novo arquivo chamado `script.js` e salve-o no mesmo diretório do arquivo HTML.
2.  Abra o arquivo `script.js` no seu editor de texto ou IDE.
3. 
## Passo 3: Fazendo uma requisição HTTP para a API

Vamos utilizar a função `fetch` do JavaScript para fazer a requisição HTTP para a API OpenWeatherMap. Neste exemplo, iremos obter a previsão do tempo para uma cidade específica, incluindo a temperatura em graus Celsius e o dia da semana.

1.  No arquivo `script.js`, adicione o seguinte código:

```
const apiKey = 'SUA_CHAVE_API';
const city = 'NOME_DA_CIDADE';

const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

fetch(url)
  .then(response => response.json())
  .then(data => {
    const temperature = data.main.temp;
    const date = new Date();
    const dayOfWeek = getDayOfWeek(date.getDay());
    const resultElement = document.getElementById('result');
    resultElement.textContent = `A temperatura em ${city} é de ${temperature}°C, neste ${dayOfWeek}.`;
  })
  .catch(error => {
    console.error('Erro:', error);
  });

function getDayOfWeek(day) {
  const daysOfWeek = ['Domingo', 'Segunda-feira', 'Terça-feira', 'Quarta-feira', 'Quinta-feira', 'Sexta-feira', 'Sábado'];
  return daysOfWeek[day];
}
```

Neste código, estamos definindo a chave de API como uma constante chamada `apiKey`. Certifique-se de substituir "SUA_CHAVE_API" pela sua própria chave de API fornecida pelo OpenWeatherMap (PEÇA AO PROF).

Também definimos a cidade de interesse como uma constante chamada `city`. Substitua "NOME_DA_CIDADE" pelo nome da cidade para a qual você deseja obter a previsão do tempo.

Neste código, estamos utilizando a template literal do JavaScript para construir a URL da API. A URL possui três partes:

-   A base da URL: `https://api.openweathermap.org/data/2.5/weather`
-   O parâmetro `q` que especifica a cidade: `?q=${city}`
-   O parâmetro `appid` que especifica a chave de API: `&appid=${apiKey}`
-   O parâmetro `units` que especifica a unidade de medida (nesse caso, Celsius): `&units=metric`

A chave de API e o nome da cidade são inseridos na URL utilizando interpolação de strings.

Essa URL completa será usada na função `fetch` para fazer a requisição HTTP à API OpenWeatherMap e obter os dados do clima para a cidade especificada.

Salve o arquivo `script.js` e teste a aplicação novamente para ver a previsão do tempo, incluindo a temperatura e o dia da semana, para a cidade escolhida.
