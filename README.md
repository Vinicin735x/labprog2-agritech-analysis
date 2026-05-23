# 📊 Análise PINTEC — Impacto do Investimento em P&D na Inovação do Agronegócio

> Trabalho final desenvolvido para submissão no **SIMPEP** (Simpósio de Engenharia de Produção).  
> Base de dados: **PINTEC — Pesquisa de Inovação (IBGE)** | Período: 2008, 2011, 2014 e 2017.

---

## 🎯 Objetivo

Analisar como o volume de investimento financeiro em Pesquisa e Desenvolvimento (P&D) se converte na adoção de inovações de produto e processo em empresas dos seguintes setores do agronegócio:

| Código | Setor |
|--------|-------|
| 10 | Fabricação de Produtos Alimentícios |
| 11 | Fabricação de Bebidas |
| 20 | Fabricação de Produtos Químicos |
| 28.3 | Fabricação de Tratores e Máquinas para Agricultura e Pecuária |

---

## 📁 Estrutura do Projeto

```
.
├── analise_pintec.py     # Script principal de análise
├── tabela5453.csv        # Nº de empresas que implementaram inovações (PINTEC/IBGE)
├── tabela5464.csv        # Valor dos dispêndios em atividades inovativas (PINTEC/IBGE)
├── graficos_pintec.png   # Visualizações geradas pelo script
└── README.md             # Este arquivo
```

---

## ⚙️ Requisitos

- Python 3.8+
- Bibliotecas:

```bash
pip install pandas numpy matplotlib scipy scikit-learn
```

---

## ▶️ Como Executar

1. Clone o repositório e entre na pasta do projeto:

```bash
git clone <url-do-repositorio>
cd <nome-da-pasta>
```

2. Instale as dependências:

```bash
pip install pandas numpy matplotlib scipy scikit-learn
```

3. Execute o script:

```bash
python analise_pintec.py
```

Os resultados serão impressos no terminal e o arquivo `graficos_pintec.png` será gerado na mesma pasta.

---

## 📈 Análises Realizadas

### 1. Estatística Descritiva
Média, desvio-padrão, mínimo e máximo do número de empresas inovadoras e dos dispêndios em inovação, segmentados por setor.

### 2. Correlação de Pearson
Mede a força da relação linear entre o investimento em P&D e o número de empresas que adotaram inovações.

- **Resultado geral: r = 0,8645 (p < 0,05)** — correlação forte e estatisticamente significativa.

### 3. Regressão Linear Simples
Modelo preditivo com dispêndio em inovação como variável independente.

- **R² = 0,747** — o modelo explica 74,7% da variância no número de empresas inovadoras.
- **Equação:** `Nº_empresas = -1407,23 + 0,001771 × Dispêndio (Mil R$)`
- A cada **R$ 1 bilhão** investido, estima-se um acréscimo de **~1.771 empresas** adotando inovações.

### 4. Visualizações (`graficos_pintec.png`)
- Evolução temporal do nº de empresas inovadoras por setor
- Evolução temporal dos dispêndios em inovação por setor
- Dispersão com reta de regressão (dispêndio × nº de empresas)
- Comparativo de dispêndios por setor entre 2011 e 2017

---

## ⚠️ Limitações

- O dataset contém apenas 4 setores e 4 pontos temporais, resultando em **15 observações** após remoção de valores ausentes (dado de Máquinas Agrícolas em 2008 indisponível na fonte).
- A correlação por setor individualmente não atingiu significância estatística devido ao número reduzido de observações por grupo — a análise mais robusta é a **correlação geral** entre todos os setores.
- Os dados refletem triênios (não anos-calendário individuais), conforme metodologia da PINTEC.

---

## 📚 Fonte dos Dados

IBGE — Instituto Brasileiro de Geografia e Estatística.  
**Pesquisa de Inovação (PINTEC).**  
Disponível em: https://www.ibge.gov.br/pintec

---

## ✍️ Autores

- Kaique Araújo
- Kauan Menezes
- Vinícius Castelhano