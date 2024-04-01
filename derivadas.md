---
title: "Derivadas e Integrais"
author: "Lucas Maltoni"
date: "2024-04-01"
output: 
  html_document: 
    keep_md: true
---



```r
library(Deriv) # Capaz de realizar derivadas e integrais
```

```
## Warning: package 'Deriv' was built under R version 4.2.3
```

```r
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 4.3.3
```


```r
# Define the function
f <- function(x) sin(x)

# Calculate the symbolic derivative
derivada <- Deriv(f, "x")

# Exiba a derivada
derivada
```

```
## function (x) 
## cos(x)
```

```r
# Derivada para um valor
derivada(0)
```

```
## [1] 1
```

```r
x_vals <- seq(-10, 10, length.out = 100)

# Calcula os valores das funções e derivadas para os valores de x
f_vals <- f(x_vals)
derivada_vals <- eval(derivada(x_vals))

# Cria um dataframe com os valores de x e as funções
dados <- data.frame(x = x_vals, f_x = f_vals, derivada_x = derivada_vals)

# Cria o gráfico usando ggplot2
grafico <- ggplot(dados, aes(x)) +
  geom_line(aes(y = f_x, color = "Função")) +
  geom_line(aes(y = derivada_x, color = "Derivada")) +
  labs(x = "x", y = "y", color = "Legend") +
  ggtitle("Gráfico da função e sua derivada") +
  scale_color_manual(values = c("Função" = "blue", "Derivada" = "red"),
                     labels = c("Função", "Derivada")) +
  theme_minimal()

# Exibe o gráfico
print(grafico)
```

![](derivadas_files/figure-html/derivada-1.png)<!-- -->


