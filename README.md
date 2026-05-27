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
├── analise_pintec.py               # Script principal de análise
├── tabela5453.csv                  # Nº de empresas que implementaram inovações (PINTEC/IBGE)
├── tabela5464.csv                  # Valor dos dispêndios em atividades inovativas (PINTEC/IBGE)
├── graficos_pintec_principal.png   # Visualizações principais (evolução, dispersão, CAGR)
├── graficos_pintec_diagnostico.png # Diagnóstico da regressão (resíduos e Q-Q plot)
└── README.md                       # Este arquivo
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

Os resultados serão impressos no terminal e dois arquivos de gráficos serão gerados na mesma pasta.

---

## 📈 Análises Realizadas

### 1. Estatística Descritiva
Média, desvio-padrão, mínimo e máximo do número de empresas inovadoras e dos dispêndios em inovação, segmentados por setor.

### 2. CAGR — Taxa de Crescimento Anual Composta (2011 → 2017)
Mede a taxa de crescimento equivalente anual de cada setor no período, tanto em número de empresas inovadoras quanto em dispêndios.

| Setor | CAGR Empresas | CAGR Dispêndios |
|-------|:---:|:---:|
| Alimentos | +0,41% a.a. | −3,28% a.a. |
| Bebidas | +2,00% a.a. | −3,28% a.a. |
| Químicos | −0,04% a.a. | +4,24% a.a. |
| Máq. Agrícolas | +2,44% a.a. | −3,68% a.a. |

> Apenas o setor de Químicos expandiu os dispêndios no período. Os demais reduziram investimentos, mesmo com crescimento no número de empresas inovadoras.

### 3. Correlação de Pearson
Mede a força da relação linear entre o investimento em P&D e o número de empresas que adotaram inovações.

- **Resultado geral: r = 0,8645 (p < 0,05)** — correlação forte e estatisticamente significativa.
- A análise por setor individualmente não atingiu significância (n pequeno por grupo) — a correlação mais robusta é a **geral**, entre todos os setores.

### 4. Regressão Linear Simples
Modelo preditivo com dispêndio em inovação como variável independente.

- **R² = 0,747** — o modelo explica 74,7% da variância no número de empresas inovadoras.
- **Equação:** `Nº_empresas = −1407,23 + 0,001771 × Dispêndio (Mil R$)`
- A cada **R$ 1 bilhão** investido, estima-se um acréscimo de **~1.771 empresas** adotando inovações.

### 5. Diagnóstico da Regressão (`graficos_pintec_diagnostico.png`)
Verificação dos pressupostos do modelo de regressão linear:

| Pressuposto | Teste | Resultado |
|-------------|-------|-----------|
| Normalidade dos resíduos | Shapiro-Wilk (W=0,9438, p=0,4323) | ✅ Atendido |
| Homocedasticidade | Spearman \|resíduos\| vs ŷ (ρ=0,65, p=0,008) | ⚠️ Possível violação |

> A possível heterocedasticidade é esperada dado que o setor de Alimentos concentra valores muito superiores aos demais — isso é discutido como limitação no artigo.

---

## 📊 Visualizações Geradas

**`graficos_pintec_principal.png`**
- Evolução temporal do nº de empresas inovadoras por setor
- Evolução temporal dos dispêndios em inovação por setor
- Dispersão com reta de regressão (dispêndio × nº de empresas)
- CAGR dos dispêndios por setor (2011 → 2017)

**`graficos_pintec_diagnostico.png`**
- Gráfico de resíduos vs valores ajustados (verificação de homocedasticidade)
- Q-Q Plot dos resíduos com resultado do Shapiro-Wilk anotado

---

## ⚠️ Limitações
- O dataset contém apenas 4 setores e 4 pontos temporais, resultando em **15 observações** após remoção de valores ausentes (dado de Máquinas Agrícolas em 2008 indisponível na fonte).
- Os dados refletem triênios (não anos-calendário individuais), conforme metodologia da PINTEC.
- Heterocedasticidade detectada nos resíduos da regressão, possivelmente decorrente da dominância do setor de Alimentos — os coeficientes permanecem válidos, mas os intervalos de confiança devem ser interpretados com cautela.

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