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
List of cell phone numbers
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

## Links

[Gerador Brasileiro](http://geradorbrasileiro.com/)
