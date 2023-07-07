# Case Técnico Beanalytic
Resolução Case Engenheiro de Dados Jr Beanalytic

# Metodologia
Para a resolução do case, foi utilizado um código Python com o objetivo de realizar a raspagem de dados do site `(https://steamdb.info/sales/)` e posteriormente concluir a carga de dados no data warehouse Google Big Query. Diante disso, foram utilizadas as seguintes bibliotecas para o auxílio dessa tarefa:

1. `import requests`
2. `import pandas as pd`
3. `from google.cloud import bigquery`
4. `from google.oauth2 import service_account`
5. `from bs4 import BeautifulSoup`

# Executando o código
Para executar o código, primeiramente você terá que ter os Headers de configuração para realizar a requisição HTTP, no qual podem ser encontrados nos passos a seguir:
1. Acesse o site `https://steamdb.info/sales/`
2. Em seguida, pressione o botão direito do mouse e clique em inspecionar elemento ou aperte a tecla F12.
3. Após isso, encontre a aba `Network` e pressione as teclas Ctrl + R. Fazendo isso, irá aparecer algumas colunas,  na coluna `Name` encontre uma linha com o nome de `Sales`.
4. Realizando os passos anteriores, clique com o botão direito do mouse em `Sales` -> `Copy` -> `Copy as cURL (cmd)`.
5. Com isso, você terá as configurações dos headers para realizar a requisição HTTP com o site.

Ao realizar o passo a passo anterior, para finalizar a carga no GBQ será necessario ter um arquivo `.JSON` com as configurações de conexão do Google cloud plataform, para obter esse arquivo siga os passos as seguir no Google Big query, tendo em vista que já tenha uma conta configurada.
1. `Menu de navegação` -> `IAM e administrador` -> `Contas de serviço` -> `Escolher uma conta existente ou criar uma nova` -> `Nos 3 pontos, clicar em criar chave`

Após realizar essas configurações, execute o código.

# Desafios
Durante o processo, o principal desafio encontrado foi a tentativa de captura do HTML do site. O link fornecido é protegido pelo Cloudflare, onde impossibilita a captura direta do HTML via Selenium (Que foi minha primeira tentativa para a captura) devido às medidas de proteção implementadas pelo Cloudflare para detectar e bloquear atividades automatizadas não autorizadas. Após inúmeras tentativas, consegui capturar os dados por meio de um Headers de configuração para realizar a requisição HTTP, utilizando as bibliotecas `requests` e `BeautifulSoup`, conseguindo com êxito capturar o HTML da página.

Após isso, o outro desafio era destrinchar o HTML para conseguir capturar os dados, que por falta de tempo não consegui obter algumas informações, como as colunas `Ends in` e `Started`. Na minha visão, consegui capturar as principais colunas: `Name, Highlighted Deal, Discount Percentage, Price, Rating e Release`. No qual podemos realizar análises comparativas, identificar as ofertas mais destacadas, acompanhar a evolução dos preços, avaliar a relação custo-benefício e monitorar as avaliações e lançamentos dos produtos em questão. Onde esses dados fornecem uma base sólida para tomadas de decisão informadas e estratégias de compra mais inteligentes.

# Visualização dos dados via Google sheets
No Google Sheets é possivel conectar diretamente uma planilha a uma bases de dados do Big Query, onde ela é atualizada em tempo real caso seja atualizada a fonte de dados.

Para realizar a conexão do Big Query com a planilha basta encontrar na aba de ferramentas a opção `Dados` e em seguida selecionar `Conectores de dados`, onde poderá facilmente conectar ao GBQ.

Para concluir o desafio é diponibilizado os dados em uma planilha pública do Google Sheets:
https://docs.google.com/spreadsheets/d/1sKPYpZqXo988MNLVYWdkkcu60FOVZZyz9SMDJXAAq6o/edit?usp=sharing

# Conclusão
Em virtude do desafio, conclui-se que consegui ter uma visão ampla da área de engenharia de dados, compreendendo desde a coleta e processamento dos dados onde obtive uma experiência nova, que é o Google BigQuery, uma poderosa plataforma de análise de dados baseada em nuvem.
