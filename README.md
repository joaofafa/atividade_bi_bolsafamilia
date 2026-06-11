# Controle de Acesso Regional - Bolsa Família com Power BI

## Objetivo

Este projeto tem como objetivo desenvolver um dashboard analítico do Programa Bolsa Família utilizando Power BI, implementando controle de acesso regional através de Row Level Security (RLS).

O sistema permite que gestores visualizem apenas os dados referentes à sua região de atuação, garantindo segurança e segregação das informações.

---

## Modelo de Dados

O modelo foi construído utilizando três tabelas:

### Tabela Fato

* amostra_bolsa

### Tabelas Dimensão

* dim_regioes
* dim_usuarios_rls

### Relacionamentos

* amostra_bolsa[UF] → dim_regioes[UF]
* dim_regioes → dim_usuarios_rls

---

## Medidas DAX

### Total Repasses

```DAX
Total Repasses =
SUM(amostra_bolsa[VALOR PARCELA])
```

### Total Beneficiários

```DAX
Total Beneficiarios =
DISTINCTCOUNT(amostra_bolsa[NIS FAVORECIDO])
```

### Ticket Médio

```DAX
Ticket Medio =
AVERAGE(amostra_bolsa[VALOR PARCELA])
```

### Municípios Atendidos

```DAX
Municipios Atendidos =
DISTINCTCOUNT(amostra_bolsa[NOME MUNICÍPIO])
```

---

## Dashboards

### Visão Geral Nacional

Indicadores apresentados:

* Total de Repasses
* Total de Beneficiários
* Ticket Médio
* Municípios Atendidos
* Repasses por Região
* Filtros por Ano e Mês

### Detalhe Regional

Indicadores apresentados:

* Matriz por UF
* Total de Repasses
* Total de Beneficiários
* Ticket Médio
* Municípios Atendidos
* Top 10 Municípios por Repasses
* Segmentação por Região

---

## Segurança de Dados (RLS)

### RLS Estático

Funções criadas:

* Admin
* Gestor_Norte
* Gestor_Nordeste
* Gestor_CentroOeste
* Gestor_Sudeste
* Gestor_Sul

Cada função possui acesso apenas à sua respectiva região.

### RLS Dinâmico

Implementado utilizando:

```DAX
[email_usuario] = USERPRINCIPALNAME()
```

O acesso é definido automaticamente de acordo com o usuário autenticado no Power BI Service.

---

## Tecnologias Utilizadas

* Power BI Desktop
* Power BI Service
* DAX
* Row Level Security (RLS)
* GitHub

---

## Autor

João Marcelo Campos Fafá

## Curso 
Ciência de Dados e Marchine Learning
3º Semestre
