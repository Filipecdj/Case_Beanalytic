# Case Técnico Beanalytic
Resolução Case Engenheiro de Dados Jr Beanalytic

# Metodologia
Para a resolução do case, foi utilizado um código Python com o objetivo de realizar a raspagem de dados do site `(https://steamdb.info/sales/)` e posteriormente concluir a carga de dados no data warehouse Google Big Query. Diante disso, foram utilizadas as seguintes bibliotecas para o auxílio dessa tarefa.

1. `requests`
2. `pandas`
3. `google-cloud`
4. `google-oauth2`
5. `bs4`

# Executando o código
Para executar o código, primeiramente você terá que coletar os Headers de configuração para realizar a requisição HTTP, no qual podem ser obtidos seguindo os passos abaixo:
1. Acesse o site `https://steamdb.info/sales/`
2. Em seguida, pressione o botão direito do mouse e clique em `Inspecionar elemento` ou pressione o atalho `ctrl + shift + I`.
3. Após isso, vá para a aba `Network` e pressione as teclas Ctrl + R. Fazendo isso, vão  aparecer algumas requisições abaixo da coluna `Name`. Role a página até encontrar a requisição de nome `sales/`.
4. Realizando os passos anteriores, clique com o botão direito do mouse em `Sales` -> `Copy` -> `Copy all as cURL (cmd)`.
5. Com isso, você terá as configurações dos headers para realizar a requisição HTTP com o site.

Ao realizar o passo a passo anterior, para finalizar a carga no GBQ será necessario ter um arquivo `.JSON` com as configurações de conexão do Google cloud plataform. Para obter esse arquivo siga os passos a seguir no Google Big query, tendo em vista que já tenha uma conta configurada.
1. `Menu de navegação` -> `IAM e administrador` -> `Contas de serviço` -> `Escolher uma conta existente ou criar uma nova` -> `Nos 3 pontos, clicar em criar chave`

Após realizar essas configurações, execute o código.

# Desafios
Durante o processo, o principal desafio encontrado foi a tentativa de captura do HTML do site. O link fornecido é protegido pelo Cloudflare, onde impossibilita a captura direta do HTML via Selenium (que foi minha primeira tentativa para a captura). Devido às medidas de proteção implementadas pelo Cloudflare para detectar e bloquear atividades automatizadas não autorizadas e após inúmeras tentativas, consegui capturar os dados usando Headers de configuração para realizar a requisição HTTP, utilizando as bibliotecas `requests` e `BeautifulSoup`, conseguindo com êxito capturar o HTML da página.

Após isso, o outro desafio era destrinchar o HTML para conseguir capturar os dados, que por falta de tempo não consegui obter algumas informações, como as colunas `Ends in` e `Started`. Na minha visão, consegui capturar as principais colunas: `Name, Highlighted Deal, Discount Percentage, Price, Rating e Release`, no qual podemos realizar análises comparativas, identificar as ofertas mais destacadas, acompanhar a evolução dos preços, avaliar a relação custo-benefício e monitorar as avaliações e lançamentos dos produtos em questão, onde esses dados fornecem uma base sólida para tomadas de decisão informadas e estratégias de compra mais inteligentes.

# Visualização dos dados via Google sheets
No Google Sheets é possivel conectar diretamente uma planilha a uma base de dados do Big Query, onde ela é atualizada em tempo real caso a fonte de dados seja atualizada.

Para realizar a conexão do Big Query com a planilha basta encontrar na aba de ferramentas a opção `Dados` e em seguida selecionar `Conectores de dados`, onde poderá facilmente conectar ao GBQ.

Para concluir o desafio, os dados foram disponibilizados em uma planilha pública do Google Sheets:
https://docs.google.com/spreadsheets/d/1sKPYpZqXo988MNLVYWdkkcu60FOVZZyz9SMDJXAAq6o/edit?usp=sharing

# Conclusão
Em virtude do desafio, conclui-se que consegui ter uma visão ampla da área de engenharia de dados, compreendendo desde a coleta e processamento dos dados. Onde obtive uma experiência nova, que é o Google BigQuery, uma poderosa plataforma de análise de dados baseada em nuvem.
