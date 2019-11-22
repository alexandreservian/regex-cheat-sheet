# Regex Cheat Sheet

Each example use regex groups `()` for to separate the symbol of data. This make we life very easy when we want to work using `replace` method.
Example:

```javascript
const text = "2019-26-09";
const regex = /(\d{4})-(\d{2})-(\d{2})/g;
console.log(text.replace(regex, "$2/$3/$1"));
// 26/09/2019
```

## Brazilian cell phone number

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
const regex = /(\(\d{2}\)\s?)?(\d{4,5})-?(\d{4})/gm;
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
const regex = /(\d{2}\.?\d{3})-?(\d{3})/gm;
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
const regex = /(\d{3})\.?(\d{3})\.?(\d{3})-?(\d{2})/gm;
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
const regex = /(\d{2})\.?(\d{3})\.?(\d{3})\/?(\d{4})-?(\d{2})/gm;
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

## CPF and CNPJ at the same time

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
const regex = /((\d{2})\.?(\d{3})\.?(\d{3})\/?(\d{4})-?(\d{2}))|((\d{3})\.?(\d{3})\.?(\d{3})-?(\d{2}))/gm;
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


## Links

[Gerador Brasileiro](http://geradorbrasileiro.com/)
