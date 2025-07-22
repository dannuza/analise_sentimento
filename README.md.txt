- Machine Learning - Análise de Sentimento

Este projeto demonstra como criar um recurso no Azure Machine Learning para fazer uma análise de sentimentos no Portal do Azure, sem usar código, apenas usando a interface do Portal.

Será criado:

1. Recurso do Azure Machine Learning
2. Dados para treinamento
3. Modelo de classificação de sentimento usando AutoML

- Prints do Portal do Azure:

Criar Serviços Cognitivos
![Criar_cognitive_services] (print/Criar_cognitive_services.png)
![Dados_cognitive_services] (print/Dados_cognitive_services.png)

Habilitar/Desabilitar Exceções de Serviços Confiáveis
![Hab_Desab_services1] (print/Hab_Desab_services1.png)
![Hab_Desab_services2] (print/Hab_Desab_services2.png)

Exportar o ARM Template do recurso
![ARM_Template_JSON] (print/ARM_Template_JSON.png)


- Como usar: Passo a passo

1. Acesse o Portal do Azure Estúdio
  [https://azure.microsoft.com]

2. Crie um Grupo de Recursos
  Preencha: Assinatura, Grupo de Recursos e Região.
  Clique em "Criar e revisar" e após verificação, em "Criar"

3. Crie um Workspace no Machine Learning
  Na barra de pesquisa, busque por Machine Learning
  Clique em "Criar"
  Preencha: Assinatura, Grupo de recursos, Região, Nome, Tipo de armazenamento. Application Insights, Key Vault e Container Registry: Deixe como “Criar novo” (padrão)
  Clique em "Criar e revisar" e após verificação, em "Criar"

4. Acesse o Azure ML Studio 
  Vá até o recurso criado e clique em "Studio web URL" 

5. Suba os dados para o ML Studio
  No menu esquerdo, selecione "Dados"
  Clique em "Criar" e escolha "arquivo local"
  Nomeie o arquivo
  Escolha o formato, CSV, com cabeçalho
  Clique em "Criar"
  
6. Crie um experimento de AutoML
  No menu esquerdo, clique em "ML automatizado"
  Clique em "+ Novo trabalho de ML automatizado"
  Preencha: Novo nome do experimento
  Tipos de tarefa, selecione "Classificação" e selecione a base de dados
  Em configurações de tarefas, selecione a coluna alvo ou destino, que neste caso é a "Sentiment"
  Em Computação, selecione "Cluster de Cálculo" -> "+Novo"
  Escolha VM: Standard_DS11_v2 (ou menor, se for teste)
  Preencha: Nome da computação
  Min nodes: 0 / Max nodes: 2
  "Criar"
  "Avançar"
OBS: Dicas para acelerar

Ative early stopping no AutoML → ele para de testar modelos ruins cedo.

Reduza o número de iterações (Max concurrent iterations = 2, Max iterations = 5~10) se só quer validar o fluxo.

Se for só um teste rápido, pode até rodar localmente (Jupyter com automl SDK), já que 61 linhas cabem tranquilo na memória.



7. Avalie e publique o melhor modelo
  Após o AutoML treinar os modelos, clique no melhor modelo 
  Vá para a aba "Models" e clique em "Register Model"
  Preencha: Nome e versão
  Após registrado, clique em "Deploy ou Implantar" > "Real-time endpoint"
  Preencha: Nome e Tipo de Computador
  Clique em "Deploy ou Implantar"

 
- Tecnologias Usadas

 1. Microsoft Azure - (https://azure.microsoft.com/)
 2. Azure Machine Learning - (https://ml.azure.com/)
 3. ARM Templates - (https://learn.microsoft.com/azure/azure-resource-manager/templates/overview)
 4. Markdown para documentação

- Autor
  Dannuza Martins Cardoso Silva
 
 


