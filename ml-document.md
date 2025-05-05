# Objetivo
Implementar um modelo de previsão com ML que antecipe tendências dos indicadores macroeconômicos do IPEA, permitindo:
- Geração de insights futuros nos relatórios
- Criação de gráficos com dados projetados
- Filtros de tempo com alcance maior (ex: projeções de 3 meses a diante)
# Dados disponíveis (*via ipeadatapy*)
Pode ser coletado séries temporais como:
- IPCA: PRECOS12_IPCA12
- INPC: PRECOS12_INPC12
- IGP-M: PRECOS12_IGPM12
- CDI: BM12_CDI12
- Câmbio: BM12_TAXACAMBIO12
# Explicação sobre o filtro de tempo com alcance maior
A ideia é permitir que o usuário selecione:
- Intervalos como por exemplo: "Próximos 3, 6 ou 12 meses"
- E que o modelo use a série histórica para gerar previsões automaticamente
# Pipeline de ML para séries temporais
1. Pré-processamento
- Verificar e preencher valores faltantes (df.interpolate())
- Garantir frequência regular da série (.asfreq("MS"))
- Divisão em treino/teste (ex: últimos 12 meses para teste)
2. Modelos possíveis:
- Random Forest Regressor (usando features como mês, tendência, defasagens)
- XGBoost Regressor
- Redes Neurais (LSTM) – para cenários mais complexos
# Resultados esperados
- Um novo campo “Projeção” no dashboard/relatório
- Visualizações com a linha (gráfico) de previsão 
- Exportação das previsões para os relatórios automáticos
# Requisitos extraídos do ML para o software
- R1: O sistema deve permitir seleção de períodos futuros para previsão
- R2: O sistema deve armazenar previsões geradas e atualizar quando necessário
- R3: O sistema deve exibir as projeções graficamente e em formato exportável
- R4: O sistema deve oferecer explicações básicas sobre os resultados da previsão
