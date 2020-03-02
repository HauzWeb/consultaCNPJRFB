# [DEPRECATED] 

Devido a RFB disponibilizar a base completa de CNPJs, a dependência não é mais necessária.

Baixe os 20 arquivos no site da RFB [aqui](http://receita.economia.gov.br/orientacao/tributaria/cadastros/cadastro-nacional-de-pessoas-juridicas-cnpj/dados-publicos-cnpj).

Use o [CNPJ-full](https://github.com/fabioserpa/CNPJ-full) para converter os dados para CSV ou SQLITE.

Após convertido, importe no banco de dados que preferir.

(O download e a conversão pode demorar algumas horas)

# Consulta CNPJ

Módulo para consulta do CNPJ na base da Receita Federal do Brasil.

## Dependências

* [Cheerio.js](https://cheerio.js.org/)
* [Iconv-Lite](https://github.com/ashtuchkin/iconv-lite)
* [Request](https://github.com/request/request)
* [Request-Promise-Request](https://github.com/request/request-promise-native)

## Autor

* **Gabriel Lopes** - [Gabriel Lopes](https://github.com/biutas)

## Instalação

    $ npm i --save consultaCnpj

## Como Usar

### Utilitário: Unmask

Utilitário para retirar os caractéres não-numéricos.

```js
const cnpj = consultaCnpj.unmask('12.123.123/1234-12'); // 12123123123412
const cep = consultaCnpj.unmask('12.123-123'); // 12123123
const cpf = consultaCnpj.unmask('123.123.123-12'); // 12312312312
```

### Utilitário: Validate

Utilitário para validar o CNPJ.

```js
const result = consultaCnpj.validate('21.876.883/0001-78'); // true
const result = consultaCnpj.validate('21876883000178'); // true
const result = consultaCnpj.validate('00.000.000/0000-00'); // false
const result = consultaCnpj.validate('00000000000000'); // false
```

### Consultar o CNPJ

```js
const params = consultaCnpj.getParams(); // Objeto com o sessionId e captcha (em base64) ou erro.
const data = consultaCnpj.getBasicInfos('21.876.883/0001-78', sessionId, 'solvedCaptcha'); // Objeto com as informações do CNPJ ou erro.
const moreData = consultaCnpj.getAdvancedInfos(sessionId); // Objeto com as informações de QSA e Capital social ou erro.
```

### [Exemplo](https://github.com/antonellisantos/consultaCnpj/tree/master/example)

    $ npm run example

## Licença

Este projeto é licenciado sob o modelo MIT License - veja [LICENSE.md](LICENSE.md) para mais detalhes.
