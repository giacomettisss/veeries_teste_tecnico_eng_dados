# Teste Técnico para Desenvolvedor na Veeries

As respostas das questões da Atividade 1 e 2 encontram-se no diretório docs no arquivo atividades.md.

## Passo a passo para iniciar o projeto e implementar as soluções do Processamento de Dados e disponibilização da API

### Criando ambiente virtual e instalando dependencias

O primeiro passo é criar um ambiente virtual para importar todas as bibliotecas e executar os scripts
 - Crie um novo ambiente virtual executando o código: `python3 -m venv venv`

Abra o ambiente virtual para que possamos instalar as bibliotecas externas.
 - Execute: `source venv/bin/activate`

Insta-le as bibliotecas externas.
 - Execute: `pip install -r requirements.txt`


### Executando scripts do Processamento de Dados

Agora com os requisitos mínimos vamos iniciar o Processamento de Dados.
O Processamento de Dados é responsável pela construção de algumas tabelas essenciais assim como a população dessas tabelas.

Mude para o diretório de processamento de dados.
 - Execute: `cd pipeline_process`

Vamos executar o primeiro Script para que possamos popular a tabela `state_neighborhood`.
 - Excute: `python3 process_state_neighborhood.py`

Agora vamos para o segundo Script, o qual é responsável por popular as tabelas `colheita` e `producao`, assim como criar a view `produtividade`.
 - Execute: `python3 process_harvest_production.py`

### Disponbilizando APIs

Agora com todos os ETLs já executados, tabelas populadas, views contruiídas estamos preparados para disponibilizar o acesso aos nossos cliente via no API.

Mude para o diretório de APIs.
 - Execute: `cd ../apis_system_integration`

Suba a API Harvest Production.
 - Execute: `python3 api_harvest_production.py`

Perfeito!
Parece que está tudo pronto. Vamos acessar alguns endpoints e realizar algumas consultas.

### Acessando endpoints

Esses são endpoints disponbilizamos pela nossa API:
 - Url: `/harvested_area?neighborhood_id={id}&year={year}`
  - Método: `GET`
  - Descrição: Esse endpoint retorna o valor de uma área colhida de um código de município de um ano.
 - Url: `/productivity?year={year}&state={state1}`
  - Método: `GET`
  - Descrição: Esse endpoint retorna o(s) valor(es) de produtividade de um ou mais estados brasileiros de um ano.
 - Url: `/produced_quantity?year={year1}&neighborhood_id={id1}`
  - Método: `GET`
  - Descrição: Esse endpoint retorna múltiplos valores de quantidade produzida de um ou mais municípios de um ou mais anos.

http://127.0.0.1:5000/harvested_area?year=2018&neighborhood_id=1100015
http://127.0.0.1:5000/harvested_area?year=2018,2019&neighborhood_id=1100015


http://127.0.0.1:5000/productivity?year=2018&state=RO&state=AM&state=PA
http://127.0.0.1:5000/productivity?state=RO&state=AM&state=PA


http://127.0.0.1:5000/produced_quantity?year=2018&year=2019&neighborhood_id=1100015&neighborhood_id=1501451
http://127.0.0.1:5000/produced_quantity?year=2018&year=2019&year=2020&year=2021&year=2022&year=2023&neighborhood_id=1100015&neighborhood_id=1501451&neighborhood_id=1501600&neighborhood_id=1201709&neighborhood_id=1501725&neighborhood_id=1501758&neighborhood_id=1501782&neighborhood_id=1501808&neighborhood_id=1501907&neighborhood_id=1501956&neighborhood_id=1502004&neighborhood_id=1502103&neighborhood_id=1502152&neighborhood_id=1502202&neighborhood_id=1502301&neighborhood_id=1502400&neighborhood_id=1502509&neighborhood_id=1502608