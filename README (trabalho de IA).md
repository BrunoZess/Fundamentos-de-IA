Análise de Sentimento de Avaliações de E-commerce (B2W)

=Objetivo=

Classificar automaticamente avaliações de clientes de e-commerce como positivas ou 
negativas, com base apenas no texto da avaliação.
Uma aplicação como essa pode ser usada, por exemplo, para priorizar o
atendimento a clientes insatisfeitos ou monitorar a reputação de
produtos.

=Integrantes=

- Thiago Freire
- Paulo Vinicius
- Bruno Ulisses

=Fonte dos dados=

Dataset B2W de avaliações de e-commerce brasileiro, disponível em:
https://www.kaggle.com/datasets/fredericods/ptbr-sentiment-analysis-datasets

-Atributo alvo: polarity (0 = avaliação negativa, 1 = avaliação positiva)
-Atributo preditivo: review_text (texto livre da avaliação)
-Tipo da tarefa: Classificação binária

=Tipo da tarefa=

Classificação, pois o atributo alvo representa categorias
(positivo/negativo), e não um valor numérico contínuo.

=Organização dos arquivos=

.
├── README.md
├── Projeto_Final_Sentimentos.ipynb --- notebook principal (abre no Colab)
└── data/
    └── b2w.csv                     --- dataset 

=Como abrir o notebook no Colab=

1. Acesse o notebook `Projeto_Final_Sentimentos.ipynb` neste repositório.
2. Clique em Open in Colab (ou abra manualmente pelo Google Colab,
   usando *File → Open notebook → GitHub e colando o link deste
   repositório).
3. Execute as células em ordem (Runtime → Run all). O notebook baixa
   o dataset automaticamente via kagglehub, não é necessário
   nenhum arquivo local.

=Modelos utilizados=

| Modelo |-| Papel |

| DummyClassifier  |-| Baseline |
| SGDClassifier |-| Modelo mínimo exigido (linear) |
| RandomForestClassifier |-| Modelo mínimo exigido (ensemble) |
| LogisticRegression |-| Modelo adicional de comparação |

Todos os modelos foram treinados sobre representações TF-IDF
(unigramas e bigramas, 5.000 features).

=Principais resultados=

| Modelo | Acurácia | Precisão | Revocação | F1-score |
|
| Regressão Logística | 0,933 | 0,946 | 0,919 | 0,932 |
| SGDClassifier | 0,931 | 0,951 | 0,910 | 0,930 |
| RandomForestClassifier | 0,920 | 0,924 | 0,915 | 0,919 |
| Baseline (classe majoritária) | 0,500 | 0,000 | 0,000 | 0,000 |

O modelo final escolhido foi a Regressão Logística, por apresentar
o maior F1-score entre os modelos avaliados, com desempenho
equilibrado entre as classes positiva e negativa. Os erros mais
frequentes ocorrem em avaliações com sentimento misto (elogio e
crítica no mesmo texto), uma limitação esperada de uma abordagem que se
baseia em frequência de palavras.

=Vídeo=

Link do vídeo de apresentação: (inserir link)

=Uso de ferramentas de Inteligência Artificial=

- Ferramenta utilizada: Claude (Anthropic)
- Finalidade: revisar o notebook e identificar erros de sintaxe e
  de lógica presentes no código original.
- Partes do trabalho em que foi utilizada: trechos do notebook no
  Google Colab que continham erros de sintaxe e de lógica (incluindo
  um vazamento de dados na etapa de vetorização TF-IDF e um erro na
  geração de uma das nuvens de palavras).
- Forma de verificação: todo o código foi executado pelo grupo no
  Google Colab, e os resultados numéricos (métricas, gráficos,
  matrizes de confusão) apresentados neste README e no notebook
  foram conferidos a partir da execução real do notebook, não gerados
  ou estimados pela IA.
