# Cat

## What

```text
Easy leaks
```

## How

```text
(printf "\x1f\x8b\x08\x00\x00\x00\x00\x00" ; tail -c +25 cat.ab ) | tar xvz
```
