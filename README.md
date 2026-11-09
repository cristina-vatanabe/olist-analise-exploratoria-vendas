# Fatores associados ao desempenho das vendas: análise exploratória da base Olist

Projeto Aplicado I da Pós-graduação em Análise Estratégica de Dados (IFMG, Campus Formiga), desenvolvido em dupla com a metodologia **CRISP-DA** (etapas 1 a 4).

**Autoras:** Cristina Satie Vatanabe ([LinkedIn](COLE-AQUI-O-LINK)) e Beatriz Maria Pereira Ribon ([LinkedIn](COLE-AQUI-O-LINK))

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU-USUARIO/NOME-DO-REPOSITORIO/blob/main/projeto_aplicado_olist.ipynb)

---

## Pergunta de negócio

> Quais fatores (categoria do produto, estado do cliente, mês da compra e valor do frete) estão associados ao valor total de vendas dos pedidos entregues na base Olist?

## Principais achados

- **Categorias:** as 10 categorias líderes concentram 62,43% da receita. Beleza e saúde lidera (9,33%), seguida de relógios e presentes (8,82%) e cama, mesa e banho (7,74%). Volume e receita nem sempre andam juntos: há categorias de alto giro e baixo ticket convivendo com categorias de baixo giro e alto ticket.
- **Estados:** SP lidera em receita (38,33%) e em pedidos (41,98%), mas tem o menor ticket médio da base (R$ 125,12). Estados de menor volume (PB, AC, AP e AL) têm ticket médio acima de R$ 187.
- **Evolução temporal:** de 2017-01 a 2018-08, o crescimento veio do **volume de pedidos**, não do ticket médio, que ficou estável (entre R$ 124,38 e R$ 149,06). O pico foi em novembro de 2017 (7.289 pedidos). A relação com a Black Friday é uma hipótese, não um efeito comprovado.
- **Frete x vendas:** associação moderada e positiva (Pearson r = 0,411; Spearman rho = 0,470; R² = 0,169). Isso indica associação estatística, **não causa e efeito**. Apenas 336 pedidos (0,35% da base) têm frete zero.

## Metodologia (CRISP-DA)

| Etapa | O que foi feito |
|---|---|
| 1. Entendimento do negócio | Contexto, objetivos, pergunta de negócio e questões de investigação |
| 2. Entendimento dos dados | Inspeção de 4 das 9 tabelas da Olist: dimensões, tipos, ausentes, duplicados e variáveis categóricas |
| 3. Preparação dos dados | Conversão de tipos, tratamento de ausentes, validação das chaves e da cardinalidade dos joins, filtro de pedidos entregues, agregação por pedido, verificação de cobertura temporal |
| 4. Análise exploratória (EDA) | Estatística descritiva, outliers (IQR), gráficos, correlação (Pearson e Spearman) e regressão linear simples |

Em seguida, o notebook consolida resultados, conclusões, recomendações gerenciais, limitações e trabalhos futuros.

## Dados

- Fonte: [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- Tabelas usadas: `olist_customers_dataset`, `olist_order_items_dataset`, `olist_orders_dataset` e `olist_products_dataset`
- Os dados **não** estão neste repositório. O notebook baixa a base diretamente do Kaggle com `kagglehub`.

## Como reproduzir

1. Clique no botão "Abrir no Colab" acima (ou baixe o notebook e abra no Jupyter).
2. Execute as células em ordem.
3. Para rodar localmente, instale as bibliotecas:

```bash
pip install kagglehub pandas numpy matplotlib seaborn scipy
```

## Ferramentas

Python, pandas, NumPy, Matplotlib, Seaborn, SciPy (`scipy.stats`) e Google Colab.

## Limitações

- Cobertura temporal desigual: três meses iniciais foram excluídos da análise de evolução temporal, e os meses de janeiro de 2017 e agosto de 2018 têm cobertura parcial.
- Uso de 4 das 9 tabelas (sem pagamentos, avaliações, vendedores e geolocalização).
- Associações estatísticas, sem inferência de causalidade.
- Estados com poucos pedidos têm ticket médio mais sensível a valores atípicos.
- Sem dados de custo e margem: a análise trata de receita, não de rentabilidade.

## Próximos passos

- Incorporar as tabelas de pagamento e avaliação do cliente.
- Aplicar regressão múltipla (ou modelos de machine learning) para estimar o efeito conjunto dos fatores.
- Investigar a relação entre a localização do vendedor e o valor do frete.
- Repetir a análise com ciclos anuais completos para separar sazonalidade real de limitação de cobertura.
