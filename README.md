# Análise Epidemiológica de Violência Contra a Mulher (SINAN) | 2023 - 2025

## Objetivo do Projeto
Este projeto analisa os registros de casos suspeitos ou confirmados de violência contra a mulher, 
notificados no **Sistema de Informação de Agravos de Notificação (SINAN)**. 

Os dados são oriundos de notificações compulsórias realizadas por unidades de saúde, e
stabelecimentos de ensino, conselhos tutelares e centros de assistência social. O foco da análise está no período de **2023 a 2025**, compreendendo as dinâmicas de violência física, psicológica, sexual e autoprovocada.

> **Observação:** Os dados de 2025 são preliminares e sujeitos a atualizações semanais pelo sistema de vigilância epidemiológica, 
conforme novos casos são digitados pelas unidades de referência.

---

## Stack Técnica e Arquitetura
O projeto foi estruturado seguindo os princípios da **Arquitetura de Medalhão**, garantindo a rastreabilidade e a qualidade dos dados:

* **Camada Bronze (Raw):** Arquivos CSV originais extraídos do Tabnet.
* **Camada Silver (Trusted):** Dados limpos, tipados e normalizados, salvos em formato **Parquet** para otimização de performance e preservação de metadados.

**Ferramentas Utilizadas:**
* **Linguagem:** Python 3.x
* **Bibliotecas de Dados:** Pandas, Numpy
* **Visualização:** Matplotlib, Seaborn
* **Armazenamento:** FastParquet

---

##Processamento de Dados

Para garantir a confiabilidade das análises, realizei as seguintes etapas de ETL:
1.  **Normalização de Tipos:** Conversão de strings com encoding brasileiro e correção de idades (ajuste de separadores decimais `,` para `.`).
2.  **Padronização Textual:** Remoção de acentos e padronização de categorias para evitar duplicidade na contagem.
3.  **Feature Engineering:** * Criação de categorias de **Faixa Etária**.
    * Criação do índice de **Poliviolência** (identificação de múltiplos abusos simultâneos).
    * Estruturação de séries temporais mensais e anuais.

---

##Principais Insights Técnicos

* **Análise de Sazonalidade e Tendência:** Identificação de picos cíclicos de notificações. A decomposição temporal sugere que períodos de maior convívio doméstico (como finais de ano e férias) apresentam variações no volume de registros, o que auxilia no planejamento de contingência em unidades de saúde.
* **Distribuição da Natureza da Violência:** A análise revelou a predominância da violência física, mas também evidenciou a **subnotificação de violências psicológicas e sexuais**. Tecnicamente, isso demonstra a importância de treinar os agentes de saúde para identificar indicadores que não deixam marcas físicas aparentes.
* **Métrica de Poliviolência:** Foi identificado que uma parcela significativa das notificações contém múltiplos tipos de agressão registrados simultaneamente. Isso desafia a interpretação tradicional de "evento único" e exige um tratamento de dados que considere a complexidade da ocorrência.
---

## Organização do Repositório
```text
├── data/
│   └── silver/   # Base consolidada em .parquet
├── notebooks.ipynb  # Análises exploratórias e visualizações
└── README.md

---

Os números deste dataset contam histórias que o código, sozinho, não explica. Minhas principais reflexões ao fim desta análise são:

### 1. A Invisibilidade do Lar como Refúgio
Os dados revelam uma ironia cruel: o local onde a mulher deveria se sentir mais segura, sua própria residência, 
é estatisticamente o cenário mais frequente das agressões. Ao observar que a maioria das notificações ocorre no ambiente doméstico, 
percebemos que para muitas mulheres, o isolamento não é proteção, mas sim um fator de risco. 
Esta análise nos força a olhar além do gráfico e entender que a luta contra a violência exige políticas que penetrem as barreiras do privado e ofereçam redes de apoio que cheguem até a porta de casa.

### 2. A Sobrecarga da "Poliviolência" e a Saúde Mental
A análise de tipos de violência mostra que a agressão física raramente caminha sozinha. 
A presença constante da violência psicológica cruzada com a física aponta para um estado de vigilância e medo contínuo. 
Como mulheres, entendemos que as marcas invisíveis na saúde mental são tão profundas quanto as marcas físicas. 
O fato de os dados do SINAN permitirem múltiplos registros para uma mesma ocorrência é um grito dos dados sobre a complexidade do trauma, 
exigindo um olhar de saúde pública que seja integral e não apenas reparador de lesões físicas.

### 3. O Silêncio das Interseccionalidades
Ao cruzar os dados de raça, cor e faixa etária, a análise deixa de ser geral e passa a ter rosto. 
Observamos que mulheres pretas e pardas, ou aquelas em situações de maior vulnerabilidade social, 
muitas vezes enfrentam barreiras adicionais para que sua dor seja transformada em notificação. 
Esta conclusão humanizada nos lembra que o 'dado nulo' ou 'ignorado' no dataset pode ser, na verdade, um silenciamento sistêmico. 
O projeto reforça que dar visibilidade a esses números é o primeiro passo para garantir que nenhuma dessas mulheres seja apenas uma estatística esquecida.

---

---

<div align="center">

[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/morgana-silva-prado/)

**Desenvolvido por Morgana Silva Prado**

</div>