# OBSERVATORIO DE SEGURANCA PUBLICA - TOCANTINS

Painel interativo de indicadores de seguranca publica do Estado do Tocantins, desenvolvido em React com visualizacoes dinamicas e exportacao de dados em CSV para analise.

## Sumario

- [Visao Geral](#visao-geral)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Requisitos](#requisitos)
- [Instalacao](#instalacao)
- [Execucao](#execucao)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Indicadores Disponiveis](#indicadores-disponiveis)
- [Exportacao de Dados](#exportacao-de-dados)
- [Metodologia](#metodologia)
- [Personalizacao](#personalizacao)
- [Licenca](#licenca)

## Visao Geral

O Observatorio de Seguranca Publica e uma ferramenta de visualizacao de dados criminais e operacionais do Estado do Tocantins. O painel permite:

- Monitoramento de indicadores de criminalidade
- Analise temporal (mensal e anual)
- Comparativo entre municipios e regioes
- Exportacao de dados para estudos e pesquisas

**IMPORTANTE**: Os dados apresentados sao SIMULADOS para fins de demonstracao do layout. Para uso em producao, integrar com APIs oficiais da SSP-TO.

## Funcionalidades

### Abas Disponiveis

| Aba | Descricao |
|-----|-----------|
| Visao Geral | Dashboard com principais indicadores e graficos consolidados |
| Crimes Violentos | CVLI, homicidios dolosos, serie historica |
| Crimes Patrimoniais | Roubos e furtos, comparativos anuais |
| Indicadores Operacionais | Operacoes, prisoes, apreensoes, veiculos recuperados |
| Analise Territorial | Distribuicao por regiao integrada, mapa de calor |
| Ranking Municipal | Top 10 municipios, tabela detalhada com taxas |
| Metodologia | Notas tecnicas, glossario, fontes de dados |

### Recursos

- Graficos interativos (linha, barra, area, pizza, compostos)
- Tooltips informativos ao passar o mouse
- Filtro por periodo (2023, 2024, 2025)
- Exportacao CSV em cada secao
- Design responsivo
- Tema escuro com paleta dourado/purpura

## Tecnologias

- **React 18** - Biblioteca de interface
- **Vite 5** - Build tool e dev server
- **Recharts 2.12** - Biblioteca de graficos
- **Google Fonts** - Cinzel e Playfair Display

## Requisitos

- Node.js 18+ (recomendado: 20 LTS ou 24)
- npm 9+

## Instalacao

### Windows (CMD)

```cmd
cd C:\Users\SEU_USUARIO\Downloads
tar -xf observatorio-seguranca-to.zip
cd observatorio-sp
npm install
```

### Linux/macOS

```bash
unzip observatorio-seguranca-to.zip
cd observatorio-sp
npm install
```

## Execucao

### Desenvolvimento

```bash
npm run dev
```

Acesse: http://localhost:5173

### Build de Producao

```bash
npm run build
```

Os arquivos otimizados serao gerados em `dist/`.

### Preview do Build

```bash
npm run preview
```

## Estrutura do Projeto

```
observatorio-sp/
├── index.html          # HTML principal
├── package.json        # Dependencias e scripts
├── vite.config.js      # Configuracao do Vite
└── src/
    ├── main.jsx        # Entry point React
    └── App.jsx         # Componente principal (todo o codigo)
```

## Indicadores Disponiveis

### Crimes Violentos

| Indicador | Descricao |
|-----------|-----------|
| CVLI | Crimes Violentos Letais Intencionais (homicidio doloso + latrocinio + lesao seguida de morte) |
| Homicidio Doloso | Morte causada intencionalmente (art. 121, CP) |
| Taxa CVLI/100mil | (CVLI / populacao) x 100.000 |

### Crimes Patrimoniais

| Indicador | Descricao |
|-----------|-----------|
| Roubo | Subtracao mediante grave ameaca ou violencia (art. 157, CP) |
| Furto | Subtracao sem violencia (art. 155, CP) |

### Indicadores Operacionais

| Indicador | Descricao |
|-----------|-----------|
| Operacoes | Numero de operacoes policiais realizadas |
| Prisoes | Total de prisoes efetuadas (flagrante + mandado) |
| Apreensoes | Apreensoes de drogas |
| Veiculos | Veiculos recuperados |

### Outros

| Indicador | Descricao |
|-----------|-----------|
| Trafico | Crimes da Lei n. 11.343/2006 |
| Armas | Apreensoes de armas de fogo |

## Exportacao de Dados

### Formato CSV

- Separador: ponto e virgula (;)
- Encoding: UTF-8 com BOM
- Decimais: virgula (compativel Excel BR)

### Arquivos Disponiveis

| Arquivo | Conteudo |
|---------|----------|
| dados_gerais_seguranca_to_2025.csv | Todos os indicadores mensais |
| serie_historica_anual_to.csv | Comparativo anual 2020-2025 |
| crimes_violentos_to_2025.csv | CVLI e homicidios mensais |
| crimes_patrimoniais_to_2025.csv | Roubos e furtos mensais |
| indicadores_operacionais_to_2025.csv | Operacoes, prisoes, apreensoes |
| dados_regionais_to_2025.csv | Dados por regiao integrada |
| ranking_municipal_to_2025.csv | Dados por municipio |

### Como Exportar

1. Navegue ate a secao desejada
2. Clique no botao "CSV" ou "Baixar CSV"
3. O arquivo sera baixado automaticamente
4. Abra no Excel, LibreOffice ou importe em R/Python

### Exemplo de Uso em Python

```python
import pandas as pd

df = pd.read_csv('dados_gerais_seguranca_to_2025.csv', 
                 sep=';', 
                 encoding='utf-8-sig',
                 decimal=',')

print(df.head())
print(df.describe())
```

### Exemplo de Uso em R

```r
library(readr)

df <- read_delim('dados_gerais_seguranca_to_2025.csv',
                 delim = ';',
                 locale = locale(decimal_mark = ','))

summary(df)
```

## Metodologia

### Fontes de Dados (Producao)

- Sistema Integrado de Gestao Operacional (SIGO)
- Boletim de Ocorrencia Eletronico (BOe)
- Sistemas da Policia Militar e Policia Civil

### Periodicidade

- Indicadores mensais: ate o 15o dia util do mes subsequente
- Indicadores anuais: consolidacao em janeiro

### Classificacao

As tipologias seguem:
- Classificacao penal brasileira
- Definicoes operacionais do SINESP/MJSP
- Anuario Brasileiro de Seguranca Publica (FBSP)

### Anonimizacao

Dados agregados em conformidade com a LGPD (Lei n. 13.709/2018).

## Personalizacao

### Alterando Cores

Edite o objeto `COLORS` em `src/App.jsx`:

```javascript
const COLORS = {
  bg: "#0a0614",           // Fundo principal
  bgCard: "#110d1f",       // Fundo dos cards
  gold: "#C9A84C",         // Cor de destaque
  red: "#FF4D4D",          // Indicadores negativos
  green: "#4CAF50",        // Indicadores positivos
  // ...
};
```

### Adicionando Dados Reais

Substitua os arrays de mock data por chamadas a API:

```javascript
const [monthlyData, setMonthlyData] = useState([]);

useEffect(() => {
  fetch('https://api.ssp.to.gov.br/indicadores/mensais')
    .then(res => res.json())
    .then(data => setMonthlyData(data));
}, []);
```

### Adicionando Nova Aba

1. Adicione ao array `tabs`:

```javascript
const tabs = [
  // ...existentes
  { id: "novaAba", label: "Nova Aba" },
];
```

2. Crie o componente:

```javascript
function NovaAba() {
  return <ChartCard title="Titulo">Conteudo</ChartCard>;
}
```

3. Adicione ao objeto `tabContent`:

```javascript
const tabContent = {
  // ...existentes
  novaAba: <NovaAba />,
};
```

## Deploy

### Vercel

```bash
npm run build
npx vercel --prod
```

### Netlify

```bash
npm run build
npx netlify deploy --prod --dir=dist
```

### GitHub Pages

```bash
npm run build
npx gh-pages -d dist
```

## Troubleshooting

### npm nao reconhecido (Windows)

```cmd
set PATH=%PATH%;C:\caminho\para\node
```

### Porta 5173 em uso

```bash
npm run dev -- --port 3000
```

### Erro de dependencias

```bash
rm -rf node_modules package-lock.json
npm install
```

## Creditos

- **Desenvolvimento**: Prototipo para SSP-TO
- **Design**: Tema escuro institucional
- **Dados**: Simulados para demonstracao

## Licenca

Este projeto e um prototipo de demonstracao. Para uso institucional, consulte a SSP-TO.

---

**Contato**: joaopedro.passos@mail.uft.edu.br

**Versao**: 1.0.0

**Ultima Atualizacao**: Marco/2026
