# Regex Cheat Sheet

Todos os exemplos usam grupos do regex `()` para separar o simbolo do dado. Isto é feito para tornar a vida mais facil para o programador, quando for usar o método `replace`.
Exemplo:

```javascript
const text = "2019-26-09";
const regex = /(\d{4})-(\d{2})-(\d{2})/g;
console.log(text.replace(regex, "$2/$3/$1"));
// 26/09/2019
```

> Todos os dados foram gerados nos sites [4Devs](https://www.4devs.com.br/) e [Gerador Brasileiro](http://geradorbrasileiro.com/).


## Número de telefone

```javascript
const text = `
- (77) 95684-9783
- (71) 92184-0315
- 905731497
- 95088-2649
- 70908447
- 3421-8868
- (6) 96237-7008
- (68)90499-9922
- (87) 997410611
- (16)929439353
`;
const regex = /(\((\d{2})\)\s?)?(\d{4,5})[-]?(\d{4})/gm;
console.log(text.match(regex));
/*
[
  '(77) 95684-9783',
  '(71) 92184-0315',
  '905731497',
  '95088-2649',
  '70908447',
  '3421-8868',
  '96237-7008',
  '(68)90499-9922',
  '(87) 997410611',
  '(16)929439353'
]
*/
```

## CEP

```javascript
const text = `
- 58204-824
- 69337-978
- 69.938-863
- 72874988
`;
const regex = /(\d{2}[.]?\d{3})[-]?(\d{3})/gm;
console.log(text.match(regex));
// [ '58204-824', '69337-978', '69.938-863', '72874988' ]
```

## CPF

```javascript
const text = `
- 294.755.728-05
- 337617902-60
- 31568262353
`;
const regex = /(\d{3})[.]?(\d{3})[.]?(\d{3})[-]?(\d{2})/gm;
console.log(text.match(regex));
// [ '294.755.728-05', '337617902-60', '31568262353' ]
```

## CNPJ

```javascript
const text = `
- 97.164.674/0001-63
- 76293834/0001-02
- 82142821/000127
- 128913760001-12
- 57783170000107
`;
const regex = /(\d{2})[.]?(\d{3})[.]?(\d{3})[/]?(\d{4})[-]?(\d{2})/gm;
console.log(text.match(regex));
/*
[ 
  '97.164.674/0001-63',
  '76293834/0001-02',
  '82142821/000127',
  '128913760001-12',
  '57783170000107' 
]
*/
```

## CPF e CNPJ ao mesmo tempo

```javascript
const text = `
- 294.755.728-05
- 337617902-60
- 31568262353
- 97.164.674/0001-63
- 76293834/0001-02
- 82142821/000127
- 128913760001-12
- 57783170000107
`;
const regex = /((\d{2})[.]?(\d{3})[.]?(\d{3})[/]?(\d{4})[-]?(\d{2}))|((\d{3})[.]?(\d{3})[.]?(\d{3})[-]?(\d{2}))/gm;
console.log(text.match(regex));
/*
[ 
  '294.755.728-05',
  '337617902-60',
  '31568262353',
  '97.164.674/0001-63',
  '76293834/0001-02',
  '82142821/000127',
  '128913760001-12',
  '57783170000107' 
]
*/
```

## Título de eleitor

```javascript
const text = `
- 9165.1348.1830
- 871560272755
`;
const regex = /(\d{4})[.]?(\d{4})[.]?(\d{4})/gm;
console.log(text.match(regex));
// [ '9165.1348.1830', '871560272755' ]
```

## PIS/PASEP

```javascript
const text = `
- 038.54391.67-8
- 8972716250-2
- 74189540820
`;
const regex = /(\d{3})[.]?(\d{5})[.]?(\d{2})[-]?(\d)/gm;
console.log(text.match(regex));
// [ '038.54391.67-8', '8972716250-2', '74189540820' ]
```

## CNH

```javascript
const text = `
- 151464680-66
- 19533844800
`;
const regex = /(\d{9})[-]?(\d{2})/gm;
console.log(text.match(regex));
// [ '151464680-66', '19533844800' ]
```

## Placa de carros no padrão normal e o novo padrão Mercosul

```javascript
const text = `
- RKN-4503
- EDQ-5579
- LOR0285
- COM9A55
- ANT1G05
- MOD3L05
`;
const regex = /(([A-Z]{3})[-]?(\d{4}))|(([A-Z]{3})(\d{1})([A-Z]{1})(\d{2}))/gm;
console.log(text.match(regex));
/*
[ 
  'RKN-4503',
  'EDQ-5579',
  'LOR0285',
  'COM9A55',
  'ANT1G05',
  'MOD3L05'
]
*/
```

## Renavam

```javascript
const text = `
- 2406618318-6
- 30693589258
`;
const regex = /(\d{10})[-]?(\d{1})/gm;
console.log(text.match(regex));
// [ '2406618318-6', '30693589258' ]
```

## Inscrição Estadual

```javascript
const text = `
- AC - 01.618.974/339-10
- AL - 2480456110
- AP - 039519660
- AM - 80.938.148-6
- BA - 116884-93
- CE - 53525140-8
- DF - 07127383001-42
- ES - 46249822-0
- GO - 10.945.363-8
- MA - 12749382-4
- MT - 7901625213-0
- MS - 28825429-5
- MG - 087.075.583/0925
- PA - 15-919530-6
- PB - 41867640-2
- PR - 042.31026-32
- PE - 4956703-91
- PI - 80788482-0
- RJ - 89.048.76-1
- RN - 20.210.143-6
- RS - 993/7064762
- RO - 2860516573540-8
- RR - 24259146-1
- SP - 365.456.289.105
- SC - 975.869.620
- SE - 22610269-6
- TO - 9703391962-0
`;
const regex = /(?=\d)(?![\d/\-.]*[/\-.]{2})[\d/\-.]{1,16}\d/gm;
console.log(text.match(regex));
/*
[ 
  '01.618.974/339-10',
  '2480456110',
  '039519660',
  '80.938.148-6',
  '116884-93',
  '53525140-8',
  '07127383001-42',
  '46249822-0',
  '10.945.363-8',
  '12749382-4',
  '7901625213-0',
  '28825429-5',
  '087.075.583/0925',
  '15-919530-6',
  '41867640-2',
  '042.31026-32',
  '4956703-91',
  '80788482-0',
  '89.048.76-1',
  '20.210.143-6',
  '993/7064762',
  '2860516573540-8',
  '24259146-1',
  '365.456.289.105',
  '975.869.620',
  '22610269-6',
  '9703391962-0'
]
*/
```

## Cartão Mastercard

```javascript
const text = `
- 5125 8108 3239 3913
- 5213-4033-9663-4675
- 5392.9140.7548.2098
- 5460805328094911
- 5571073331809322
`;
const regex = /(?=[5][1-5])(\d{4})[\s-.]?(\d{4})[\s-.]?(\d{4})[\s-.]?(\d{4})/gm;
console.log(text.match(regex));
/*
[ 
  '5125 8108 3239 3913',
  '5213-4033-9663-4675',
  '5392.9140.7548.2098',
  '5460805328094911',
  '5571073331809322' 
]
*/
```

## Cartão Visa

```javascript
const text = `
- 4929 8066 6172 1969
- 4024.0071.9067.6451
- 4916-1801-5471-1621
- 4556201055723856
`;
const regex = /(?=[4])(\d{4})[\s-.]?(\d{4})[\s-.]?(\d{4})[\s-.]?(\d{4})/gm;
console.log(text.match(regex));
/*
[ 
  '4929 8066 6172 1969',
  '4024.0071.9067.6451',
  '4916-1801-5471-1621',
  '4556201055723856'
]
*/
```

## CVV dos cartões Mastercard ou Visa

```javascript
const text = `
- 894
- 815
`;
const regex = /(\d{3})/gm;
console.log(text.match(regex));
// [ '894', '815' ]
```

## Validade dos cartões Mastercard ou Visa

```javascript
const text = `
- 06/20
- 03-21
- 0425
`;
const regex = /(?=(0[1-9])|(1[0-2]))([0-1][0-9])[/-]?(\d\d)/gm;
console.log(text.match(regex));
// [ '06/20', '03-21', '0425' ]
```

## Validação de senha forte

Vamos criar um exemplo de validação de senha forte. Valida se tem:
- Pelo menos uma letra maiúscula;
- Pelo menos um número;
- Pelo menos um simbolo `(!@#$%&*()-+.,;?{[}]^><:)`;
- Que tenha entre 6 a 12 caracteres;
- Aceitando somente letras de `a - z` maiúscula e minúscula, números e os simbolos `(!@#$%&*()-+.,;?{[}]^><:)`

> Neste exemplo, vamos usar o método `test` do objeto `RegExp`, para testar se a string contem ou não nossa regra.

```javascript
const senha1 = '#1Wl4i';
const senha2 = 'mm7i%KX^+';
const senha3 = 'Q3tYR+Y1dL:P';
const senha4 = 'y-fw6&q';
const senha5 = 'kA{Lbo';
const senha6 = 'uuksEy6';
const senha7 = '(8gp30d0@%;Ms}0';
const senha8 = 'U:oTKrçãé';
const regex = /^(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%&*()+\-.,;?\^.,;?><:{}\[\]])[\w!@#$%&*()+\-.,;?\^.,;?><:{}\[\]]{6,12}$/;
console.log(regex.test(senha1)); //true
console.log(regex.test(senha2)); //true
console.log(regex.test(senha3)); //true
console.log(regex.test(senha4)); //false (não contem uma letra maiúscula)
console.log(regex.test(senha5)); //false (não contem pelo menos um número)
console.log(regex.test(senha6)); //false (não contem pelo menos um simbolo)
console.log(regex.test(senha7)); //false (contem mais de 12 caracteres)
console.log(regex.test(senha8)); //false (contem caracteres diferentes de letras de a-z, números ou simbolo)
```



## Links

[4Devs](https://www.4devs.com.br/)
[Gerador Brasileiro](http://geradorbrasileiro.com/)
[O que significa cada número do cartão de crédito](https://www.tecmundo.com.br/cartao-de-credito/43322-o-que-significa-cada-numero-do-cartao-de-credito-ilustracao-.htm)