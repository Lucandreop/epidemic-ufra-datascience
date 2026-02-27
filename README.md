# 🦟 Análise de Dados Epidemiológicos
**Dengue · Chikungunya · Zika · Febre Amarela**  
*Implicações para a Vigilância Epidemiológica e Saúde Pública no Brasil*

| | |
|---|---|
| **Instituição** | Universidade Federal Rural da Amazônia (UFRA) — ICIBE |
| **Curso** | Bacharelado em Sistemas de Informação |
| **Disciplina** | Ciência de Dados I |
| **Professor** | Roberto Yuri da Silva Franco |
| **Equipe** | Lucas André Oliveira Pinheiro · Eduardo Nogueira · Cynthia Pantoja de Melo Neiva |
| **Período** | 2025.2 |

---

## Descrição

Este projeto aplica técnicas de Ciência de Dados na análise epidemiológica das arboviroses dengue, chikungunya, zika vírus e febre amarela no Brasil, utilizando dados públicos disponibilizados pelo Ministério da Saúde via plataforma DataSUS.

O estudo analisa a evolução temporal, a distribuição geográfica e os padrões demográficos das notificações registradas no SINAN (Sistema de Informação de Agravos de Notificação) entre 2015 e 2024, discutindo as implicações dos resultados para a vigilância epidemiológica e para as políticas públicas de saúde.

A análise é restrita aos registros epidemiológicos disponíveis nos sistemas oficiais de notificação, sem análise direta de dados de cobertura vacinal. No caso da febre amarela, foram considerados exclusivamente os casos humanos, excluindo os registros de epizootias em primatas não-humanos, a fim de manter comparabilidade metodológica com as demais doenças analisadas.

---

## 🎯 Objetivos

- Analisar a evolução temporal dos casos de dengue, chikungunya, zika e febre amarela no Brasil
- Comparar a incidência das arboviroses entre diferentes períodos, estados, faixas etárias e grupos demográficos
- Identificar padrões epidemiológicos e possíveis sazonalidades
- Discutir as implicações dos resultados para a vigilância epidemiológica e a saúde pública
- Demonstrar a aplicação prática da Ciência de Dados no contexto da saúde pública

---

## 🗂️ Fonte dos Dados

Os dados foram obtidos da plataforma DataSUS, do Ministério da Saúde, por meio do SINAN. Os arquivos são baixados automaticamente pelo notebook diretamente das URLs públicas do repositório oficial.

| Arbovirose | Período | Formato |
|---|---|---|
| Dengue | 2015 – 2024 | CSV compactado (`.csv.zip`) |
| Chikungunya | 2017 – 2024 | CSV compactado (`.csv.zip`) |
| Zika Vírus | 2016 – 2024 | CSV compactado (`.csv.zip`) |
| Febre Amarela (casos humanos) | 1994 – 2025 | JSON compactado (`.json.zip`) |

> ⚠️ Os dados de Chikungunya referentes a 2015 e 2016 estão incompletos no repositório do DataSUS — esses anos não contêm a coluna de hospitalização e foram carregados sem esse campo.

---

## 🔬 Metodologia

O projeto seguiu o ciclo de vida da Ciência de Dados:

1. **Coleta** — download automatizado dos arquivos públicos via requisições HTTP
2. **Importação** — leitura seletiva de colunas para otimização de memória (pandas)
3. **Limpeza** — tratamento de valores ausentes, decodificação das variáveis SINAN e remoção de outliers de idade
4. **Transformação** — criação de variáveis derivadas (faixa etária, período epidemiológico) e normalização Z-score para comparação entre doenças de magnitudes distintas
5. **Análise exploratória** — estatísticas descritivas e tabelas de contingência
6. **Visualização** — 10 gráficos interativos produzidos com Plotly
7. **Interpretação** — discussão dos padrões observados à luz da literatura epidemiológica

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.10** — linguagem principal
- **pandas** — manipulação e análise dos dados tabulares
- **NumPy** — operações numéricas vetorizadas
- **Plotly** — visualizações interativas
- **scikit-learn** — normalização e codificação de variáveis
- **Jupyter Notebook** — ambiente de desenvolvimento e apresentação

---

## 📁 Estrutura do Repositório

```
TRABALHO-CIENCIA-DADOS/
│
├── base_dados/
│   └── base.txt                           # Base de dados bruta utilizada nas análises
│
├── dicionario_dados/
│   ├── dic_dados_chikungunya.pdf          # Dicionário de variáveis — Chikungunya
│   ├── dic_dados_dengue.pdf               # Dicionário de variáveis — Dengue
│   ├── dic_dados_febre amarela.pdf        # Dicionário de variáveis — Febre Amarela
│   └── dic_dados_zika.pdf                 # Dicionário de variáveis — Zika
│
├── relatorio/
│   └── relatorio_epidemiologico_NAP2.pdf  # Relatório final do projeto
│
├── src/
│   └── analise_arboviroses_NAP2.ipynb     # Notebook principal com toda a análise
│
├── .gitignore                             # Arquivos e pastas ignorados pelo Git
└── README.md                              # Documentação do projeto (este arquivo)
```

### Descrição das pastas

**`base_dados/`** — Contém os dados brutos utilizados como entrada para as análises. O arquivo `base.txt` reúne os registros epidemiológicos que alimentam o notebook.

**`dicionario_dados/`** — PDFs com os dicionários de variáveis para cada arbovirose estudada. Descrevem o significado de cada campo da base de dados, tipos de valores aceitos e definições técnicas do SINAN.

**`relatorio/`** — Relatório epidemiológico final com os resultados, discussões e conclusões obtidas a partir das análises.

**`src/`** — Código-fonte do projeto. O notebook `analise_arboviroses_NAP2.ipynb` concentra toda a análise: coleta, limpeza, transformação e visualização dos dados.

---

## ▶️ Como Executar

**Requisitos:** Python 3.10 ou superior e conexão com internet.

```bash
# 1. Instalar as dependências
pip install pandas numpy plotly scikit-learn requests openpyxl jupyter

# 2. Abrir o notebook
jupyter notebook src/analise_arboviroses_NAP2.ipynb
```

> Os dados são baixados automaticamente na primeira execução — não é necessário baixar nenhum arquivo manualmente.  
> **VS Code:** o notebook já está configurado para renderizar os gráficos Plotly corretamente nesse ambiente.

---

## ⚠️ Limitações

- **Subnotificação:** casos leves que não chegam ao atendimento médico não constam nas bases, resultando em subestimativa da incidência real
- **Inconsistências temporais:** o padrão de preenchimento das fichas melhorou ao longo dos anos, dificultando comparações entre períodos distantes
- **Ausência de variáveis externas:** dados climáticos, socioeconômicos e de cobertura vacinal não foram incluídos na análise
- **Recorte descritivo:** não foram realizados testes de hipóteses, modelos preditivos ou análises de causalidade

---

## Conclusão

Os resultados mostram que a dengue mantém circulação endêmica com picos cíclicos — o ano de 2024 registrou o maior volume histórico, com 6,5 milhões de notificações. A chikungunya apresentou crescimento progressivo desde 2017. O zika exibiu o padrão clássico de epidemia em população sem imunidade prévia: pico em 2016 e queda abrupta nos anos seguintes. A febre amarela manteve circulação focal, com surto expressivo entre 2017 e 2019 na Região Sudeste.

O projeto demonstra que é possível construir uma análise epidemiológica robusta a partir de dados públicos, com ferramentas abertas e acessíveis, contribuindo para a compreensão da dinâmica das arboviroses no Brasil.

---

*Trabalho acadêmico desenvolvido para fins educacionais no âmbito da disciplina Ciência de Dados I — UFRA, 2025.*
