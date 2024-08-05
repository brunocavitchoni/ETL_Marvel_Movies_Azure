<h1>Projeto de ETL (Extração, Transformação e Carregamento de dados), com banco de dados em formato CSV, referente aos filmes da Marvel Cinematic Universe, disponibilizado pela plataforma Kaggle.</h1>

<h2>Utilizei este tema para treinamento do processo de ingestão de dados de ponta a ponta, utilizando Data Factory da Azure Cloud</h2>

![pipeline](https://github.com/user-attachments/assets/b1bbdd79-db0b-446b-94a5-7c113a96830a)

---------------------

<h2>Criação de Grupo de Recursos, com os seguintes recursos:</h2>

- Sistema de Armazenamento (DataLake)
- Servidor SQL
- Banco de dados SQL
- Data Factory

![image](https://github.com/user-attachments/assets/36f4bfd6-2b63-4dc1-b179-a7d0a46d0aa1)

---------------------

<h3>Criar contêiner e inserir o arquivo CSV</h3>

![image](https://github.com/user-attachments/assets/1481fe75-734a-4ee0-994a-49278046fc90)

---------------------

<h3>Criação de tabelas no Banco de Dados</h3>

![image](https://github.com/user-attachments/assets/1f7af3e2-2faa-4154-a09d-e3461345347f)

---------------------

![image](https://github.com/user-attachments/assets/8093c10b-c69a-4a3e-aeb4-638faed0cff6)

---------------------

![image](https://github.com/user-attachments/assets/8c09040e-d8ae-4bed-93dc-ccfb3810184d)

---------------------

![image](https://github.com/user-attachments/assets/dc8f4329-d3ca-44a0-ba41-983f96087e0e)

---------------------

![image](https://github.com/user-attachments/assets/284f8131-c595-47bd-8b0a-eb3206c83b11)

---------------------

![image](https://github.com/user-attachments/assets/3665b463-b06d-42c6-b4f6-cd22583599de)

---------------------

![image](https://github.com/user-attachments/assets/a7ac0942-c641-4d96-8c46-00629332f128)

---------------------

<h3>Configuração do Banco de Dados após criação das tabelas</h3>

![image](https://github.com/user-attachments/assets/360bc6e5-c6fb-45ed-8cbd-7b3ee4632456)

---------------------

<h1>Data Factory</h1>
<h3>Criar Serviços Vinculados para utilizar no Pipeline</h3>

![image](https://github.com/user-attachments/assets/8519d5a5-9411-4c48-86ef-748e7f7cd11e)

---------------------

<h3>Criar Conjuntos de Dados para utilizar no Pipeline</h3>

![image](https://github.com/user-attachments/assets/7c4f843b-c85d-406b-995e-60a4330c1ba1)

---------------------

![image](https://github.com/user-attachments/assets/77acc33c-2db1-4267-9a5b-de1a422d2096)

---------------------

<h1>Pipeline de dados</h1>
<h3>Criar Pipeline para copiar os dados do arquivo CSV para o Banco de Dados</h3>

![image](https://github.com/user-attachments/assets/3af635d6-d921-441b-b264-35cb9ff5ae93)

---------------------

<h6>Utilizei apenas as 10 primeiras linhas, para facilitar a visualização dos dados neste arquivo.</h6>
<h3>Conteúdo das colunas</h3>
<p>movie_title: Nome do filme</p>
<p>mcu_phase: Fase do filme dentro do MCU</p>
<p>release_date: Data de lançamento</p>
<p>tomato_meter: Nota dos críticos no Rotten Tomatoes</p>
<p>audience_score: Nota do público geral</p>
<p>movie_duration: Duração do filme em minutos</p>
<p>production_budget: Gastos com a produção do filme em US$</p>
<p>opening_weekend: Arrecadação da bilheteria no primeiro final de semana após a estreia</p>
<p>domestic_box_office: Arrecadação da bilheteria nos Estados Unidos</p>
<p>worldwide_box_office: Arrecadação da bilheteria em todo o mundo, incluindo Estados Unidos</p>

<h1>CAMADA SILVER</h1>

<h3>Criar Scripts para transformação de dados, criando as tabelas silver_marvel_movies e silver_franchise_mapping</h3>

![image](https://github.com/user-attachments/assets/053eb026-3d75-438e-8ff5-fa1549c8b006)

---------------------

![image](https://github.com/user-attachments/assets/35e5d2e5-769c-4681-93df-b92c4e543a61)

---------------------

<h3>Modificações realizadas:</h3>

<p>Modificação de release_date de varchar para DATE</p>
<p>Modificação de production_budget de varchar para DECIMAL, com até 20 digitos, e com 2 digitos decimais</p>
<p>Modificação de opening_weeked de varchar para DECIMAL, com até 20 digitos, e com 2 digitos decimais</p>
<p>Modificação de domestic_box_office de varchar para DECIMAL, com até 20 digitos, e com 2 digitos decimais</p>
<p>Modificação de worldwide_box_office de varchar para DECIMAL, com até 20 digitos, e com 2 digitos decimais</p>

<h1>Conectar Pipeline e depurar para testar as conexões</h1>

![image](https://github.com/user-attachments/assets/3f9dd5cd-ebea-415a-b9a8-62c58e066b99)

---------------------

<h1>CAMADA GOLD</h1>

<h3>Transformação final dos dados, criando tabelas úteis para análises posteriores. Criei tabelas para análises qualitativas (gold_movies_summary e gold_franchises_summary), referente às notas que cada filme e franquia receberam pela audience e pela crítica no site Rotten Tomatoes, e tabelas para análise quantitativa (gold_movies_financial_performance e gold_franchises_financial_performance), referente aos valores arrecadados por filme e por franquia</h3>

<h2>CRIAÇÃO DA TABELA gold_movies_summary</h2>

![image](https://github.com/user-attachments/assets/6a93e1f4-754e-4c6a-99c2-d022ccf2f80d)

---------------------

<p>Esta tabela tem por objetivo a visualização dos dados referentes as notas da crítica e da audiência para cada filme, ordenadas pela maior nota da crítica, em ordem decrescente</p>

<h2>CRIAÇÃO DA TABELA gold_movies_financial_performance</h2>

![image](https://github.com/user-attachments/assets/9ef842a1-b69d-4011-9370-56de1653649b)

---------------------

<p>Esta tabela tem por objetivo a visualização dos dados referentes a arrecadação financeira para cada filme, ordenadas pelo lucro total, em ordem decrescente</p>

<h2>CRIAÇÃO DA TABELA gold_franchises_summary</h2>

![image](https://github.com/user-attachments/assets/5ace6281-2341-47b5-a266-5416064f24db)

---------------------

<p>Esta tabela tem por objetivo a visualização dos dados referentes as notas da crítica e da audiência para cada franquia, ordenadas pela maior nota da crítica, em ordem decrescente</p>

<h2>CRIAÇÃO DA TABELA gold_franchises_financial_performance </h2>

![image](https://github.com/user-attachments/assets/a502d28c-f6b8-4a0a-afe6-a978ab360db4)

---------------------

<p>Esta tabela tem por objetivo a visualização dos dados referentes a arrecadação financeira para cada franquia, ordenadas pelo lucro total, em ordem decrescente</p>

<h1>Conectar Pipeline e depurar para testar as conexões</h1>

![image](https://github.com/user-attachments/assets/1d0e501e-4744-4f08-9e8e-ca195b57d854)
