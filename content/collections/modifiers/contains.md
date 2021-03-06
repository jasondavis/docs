---
types:
  - condition
  - array
  - string
id: 75145be0-966f-490e-af3d-ed122eb6445b
---
Check if a value contains another value. Supports both strings and arrays.

Returns `true` if a match is found, otherwise `false`. 

The first parameter is the "needle" to find in the "haystack". It will read from the context if there is a matching 
variable, otherwise it will use the parameter as the value.

### Strings

Case-insensitive by default but can be made sensitive by setting the second parameter to `true`.

```.language-yaml
summary: "It was the best of times, it was the worst of times."
adjective: best
noun: carrot
```

```
{{ if summary | contains:BEST }}
{{ if summary | contains:BEST:true }}
{{ if summary | contains:adjective }}
{{ if summary | contains:noun }}
```

```.language-output
true   (the substring "BEST" was in the string, and it didn't care about the case.)
false  (the substring "BEST" was in the string, however it didn't match the case.)
true   (there's a field named "adjective", and it got the value which was "best")
false  (there's a field named "noun", and it got the value which was "carrot")
```

### Arrays

``` .language-yaml
foods:
  - bacon
  - bread
  - tomato
delicious: bacon
gross: broccoli
```

```
{{ if foods | contains:bacon }}
{{ if foods | contains:delicious }}
{{ if foods | contains:gross }}
```

``` .language-output
true   (there's no field named "bacon", so it searched for literally "bacon") 
true   (there's a field named "delicious", and it got the value which was "bacon")
false  (there's a field named "gross", and it got the value which was "broccoli")
```
