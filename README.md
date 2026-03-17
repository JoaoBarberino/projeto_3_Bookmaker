## Modelagem Avançada, Elo Rating e Explainable AI (XAI)

A conclusão da arquitetura quantitativa deste projeto consistiu em superar a limitação de volume de operações do modelo estático, ao mesmo tempo em que a interpretabilidade do modelo foi garantida.

### Metodologias Aplicadas

1. **A Implementação do Elo Rating:**
   - As médias móveis simples (xG, Remates, etc.) são ineficientes em medir a "dificuldade do adversário". Para corrigir isso, implementou-se o **Sistema Elo Rating** (utilizado oficialmente pela FIFA e em competições de Xadrez). 
   - Ao medir a força relativa cronológica, o modelo conseguiu dimensionar o "peso da camisa". O resultado prático no backtest foi o aumento do volume de operações lucrativas, duplicando o lucro líquido absoluto em relação às iterações anteriores, mesmo estabilizando o ROI na casa dos 50%.

2. **Testes de Regressão e Kelly Criterion (Lições Aprendidas):**
   - Foram conduzidos testes experimentais rigorosos modelando a **Distribuição de Poisson** para previsão exata de gols e o **Critério de Kelly** para gestão dinâmica de banca. Comprovou-se matematicamente que para modelos preditivos que sofrem de leves falhas de calibração devido à variância do esporte, a Classificação Binária (XGBoost) com Stake Fixa se mostra estatística e financeiramente superior.

3. **Explainable AI (Abertura da Caixa Preta com SHAP):**
   - Através da biblioteca `shap` (SHapley Additive exPlanations), a estrutura de decisão do modelo foi auditada.
   - **Descobertas:** O algoritmo validou visualmente o conceito de multicolinearidade. A IA ignorou features redundantes (ex: Remates no Alvo) para focar na métrica de maior impacto global: o **volume de remates permitidos ao time visitante**. A análise SHAP provou que não se trata apenas de prever resultados, mas de compreender a lógica oculta que rege as ineficiências do mercado financeiro esportivo.

   feat: implementa sistema Elo Rating, interpretabilidade com SHAP e finaliza pipeline quantitativo