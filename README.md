# AVC-DASHBOARD
Power BI dashboard com 103k+ casos de AVC no Brasil — mapa coroplético, 5 slicers com cross-filtering bidirecional, ranking dinâmico de cidades e distribuição demográfica por raça/cor, sexo e faixa etária. Power Query · DAX · Modelagem dimensional.
# Dashboard AVC — Análise Epidemiológica com Power BI

> Dashboard interativo para análise de 103.000+ casos de Acidente Vascular Cerebral (AVC) no Brasil, com mapa coroplético por estado, cross-filtering avançado e 5 slicers integrados.

![Ferramenta](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Dataset](https://img.shields.io/badge/dataset-103k%20casos-blueviolet?style=flat-square)
![Contexto](https://img.shields.io/badge/contexto-acadêmico-blue?style=flat-square)

---

## Visão Geral

Dashboard de análise epidemiológica desenvolvido em **Power BI Desktop**, com foco em visualização de dados de saúde pública e boas práticas de BI: cross-filtering bidirecional, hierarquia de filtros e design orientado à tomada de decisão.

O painel transforma um dataset bruto de casos de AVC em **insights visuais acionáveis** sobre perfil demográfico, tipo de acidente, distribuição geográfica e ranking de cidades — com tema escuro e layout em grid pensado para leitura rápida.

---

## Screenshots

### Visão geral — Brasil completo (sem filtros)
![Dashboard geral](<img width="909" height="501" alt="dashboard total" src="https://github.com/user-attachments/assets/173328c6-e1a8-4aae-9a30-2faec608f0fa" />)

### Drill-down por estado — filtro UF = MG
![Filtro MG](<img width="906" height="497" alt="dashboard mg" src="https://github.com/user-attachments/assets/89d0ad77-ac43-44cb-9015-0348473a9fa9" />)

*Ao clicar em Minas Gerais no mapa, todos os visuais se atualizam simultaneamente: o Top 5 muda para cidades mineiras, o gráfico de área reflete apenas casos de MG e o KPI passa a exibir o total filtrado para o estado — o total geral sem filtros é 103 Mil casos.*

---

## Estrutura do Dashboard

### KPI — Total de Casos
Card fixo no topo exibindo **103 Mil** casos totais. Atualiza em tempo real conforme os filtros são aplicados, funcionando como âncora de contexto para todos os outros visuais.

---

### Mapa Coroplético — "Casos de AVC por Estado"

Mapa do Brasil com intensidade de cor proporcional ao volume de casos por UF. Funciona como filtro visual bidirecional: clicar em um estado filtra toda a página.

- **Sem filtro:** todos os estados visíveis, com MG e SP destacados por maior volume
- **Com filtro MG ativo:** o mapa dá zoom na região sudeste, exibindo as principais cidades — Belo Horizonte, Uberlândia, Juiz de Fora, Ribeirão Preto, Campinas

---

### Slicers — 5 Filtros com Cross-Filtering Bidirecional

| Slicer | Valores disponíveis |
|--------|---------------------|
| **UF** | Todos os estados brasileiros |
| **Tipo de AVC** | AVC não especificado · Outras doenças cerebrovasculares · AVC hemorrágico · AVC isquêmico |
| **Raça/cor** | Amarela · Branca · Ignorado · Indígena · Parda · Preta |
| **Sexo** | Todos · Masculino · Feminino |
| **Faixa Etária** | 0-19 · 20-39 · 40-59 · 60-79 · 80+ |

> Qualquer combinação de filtros atualiza simultaneamente o mapa, o gráfico de área, o ranking de tipos, o Top 5 de cidades e a distribuição por faixa etária. Cross-filtering configurado nas interações entre visuais — não apenas nos slicers.

---

### Gráfico de Área — "Distribuição de casos por faixa etária e raça/cor"

Gráfico de área empilhada mostrando a evolução da incidência de AVC por faixa etária, segmentado por raça/cor (Amarela · Branca · Ignorado · Indígena · Parda · Preta).

**Padrão observado nos dados:**
- Incidência praticamente nula nas faixas 0–19 e 20–39
- Crescimento expressivo a partir de 40–59
- Pico acentuado na faixa 60–79
- Raça Parda (verde) e Preta (laranja/vermelho) lideram o volume em todas as faixas etárias adultas

---

### Gráfico de Barras — "Tipo de AVCs mais comuns"

Ranking dos 4 tipos de AVC por volume total, com legenda por cor:

| Posição | Tipo | Cor na legenda |
|---------|------|---------------|
| 1º | AVC não especificado | Azul claro |
| 2º | Outras doenças cerebrovasculares | Verde |
| 3º | AVC hemorrágico | Roxo |
| 4º | AVC isquêmico | Amarelo/laranja |

---

### Gráfico de Barras — "Top 5 cidades com mais casos"

Ranking dinâmico que atualiza conforme o filtro de UF selecionado:

| Brasil (sem filtro) | MG (com filtro) |
|---------------------|-----------------|
| Rio de Janeiro | Belo Horizonte |
| São Paulo | Juiz de Fora |
| Recife | Teófilo Otoni |
| Salvador | Montes Claros |
| Fortaleza | Salinas |

---

### Gráfico de Barras — "Distribuição por faixa etária"

Leitura consolidada do volume absoluto de casos por grupo etário, sem segmentação por raça. Complementa o gráfico de área com uma visão mais direta para comparações rápidas.

---

## Técnicas Aplicadas

**Power Query**
- Limpeza e padronização dos dados brutos: tratamento de nulos, tipagem de campos, normalização de categorias (raça/cor, tipo de AVC)
- Criação de coluna de faixa etária agrupada a partir da idade numérica

**Modelagem**
- Relacionamentos entre tabela de fatos (casos) e dimensões (UF, tipo, raça/cor, faixa etária)
- Hierarquia geográfica: País → Estado → Cidade (habilita drill-down no mapa)

**DAX**
- Medida `Total Casos` responsiva ao contexto de filtro de cada visual
- Medidas condicionais para KPI dinâmico
- Contagens por categoria para os rankings de tipo e cidade

**Design**
- Tema escuro personalizado para leitura sob diferentes condições de iluminação
- Paleta de cores consistente entre o gráfico de área e sua legenda de raça/cor
- Layout em grid com hierarquia visual clara: KPI → Mapa → Gráfico principal → Gráficos de suporte

---

## Como Abrir

1. Instale o [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (gratuito)
2. Clone o repositório ou baixe o arquivo `.pbix`
3. Abra o arquivo no Power BI Desktop
4. Interaja com o mapa e os slicers — qualquer clique filtra toda a página

```bash
git clone https://github.com/mlssnw/dashboard-avc.git
```

---

## Aprendizados

- Cross-filtering bidirecional como ferramenta de análise exploratória, não apenas recurso visual
- A importância do Power Query antes da modelagem — dados mal tipados corrompem qualquer cálculo DAX
- Modelagem dimensional aplicada a dados de saúde pública com múltiplas dimensões de corte
- Responsabilidade ética na apresentação de dados segmentados por raça, sexo e faixa etária
- Hierarquia visual em dashboards: onde o olho vai primeiro importa tanto quanto os dados

---

## Contexto Acadêmico

Projeto desenvolvido durante o curso de **Engenharia de Software** na UniSociesc / Grupo Ânima, complementar ao uso profissional diário do Power BI em ambiente corporativo.
