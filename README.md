# Desafio_SQL
Neste outro desafio lançado pela Escola DNC, fiz um dashboard totalmente em SQL para analisar vários aspectos da aquisição de clientes para ver o status do crescimento de novos usuários na empresa fictícia.

![a](https://github.com/OliveiraIuri/Desafio_SQL/assets/120345667/fd47930f-5498-4f3f-adca-94d87d697d7d)

1 - Gráfico "Quantidade de pessoas por gênero"

    SELECT CASE WHEN gender = 'male' THEN 'masculino' ELSE 'feminino' END AS gender, COUNT(*) AS quantidade
    FROM leads_basic_details
    GROUP BY gender;

Neste primeiro código, a primeira coluna selecionada é definida usando a expressão CASE WHEN gender = 'male' THEN 'masculino' ELSE 'feminino' END AS gender. Isso significa que, para cada registro da tabela, será verificado se a coluna gender é igual a "male". Se for verdadeiro, o valor "masculino" será retornado. Caso contrário, o valor "feminino" será retornado. Após isso, utilizo o GROUP BY para agrupar as informações de acordo com a coluna GENDER.

2 - Cartão "Média de idade"

    SELECT AVG (age) 
    FROM leads_basic_details

Neste segundo código, mais simples, utilizo um cálculo matemático AVG (média) para me retornar no cartão a média de idade dos clientes.

3 - Gráfico "Quantidade de pessoas por graduação"

    SELECT current_education, COUNT (*) as quantidade 
    FROM leads_basic_details
    GROUP BY current_education
    ORDER BY quantidade

Neste código, utilizei a expressão COUNT (contagem) para contar o número de linhas da tabela, agrupando essa informação pela coluna CURRENT_EDUCATION e utilizando o ORDER BY para ordenar as informações de acordo com a QUANTIDADE.

4 - Tabela "Média de visualizações por idioma"

    SELECT language, AVG (watched_percentage) 
    FROM leads_demo_watched_details
    WHERE watched_percentage > 0.5
    GROUP BY language
   
Aqui, utilizei novamente a AVG (média) aliada com a expressão condicional WHERE para filtrar somente os valores acima de 0.5, seguindo de um GROUP BY por LANGUAGE.

5 - Gráfico "Ligações por plataforma ao longo do tempo"

    SELECT lead_gen_source, call_done_date, COUNT(*) 
    FROM leads_basic_details
    LEFT JOIN leads_interaction_details ON leads_basic_details.lead_id = leads_interaction_details.lead_id
    GROUP BY lead_gen_source, call_done_date
    ORDER BY lead_gen_source

Nesta última análise, utilizei o COUNT (contagem) para contar o número de linhas da tabela em relação a origem dos leads e o dia da ligação. Para isso, utilizei o LEFT JOIN para unir duas tabelas diferentes mas relacionadas entre si para poder ter a informação completa para o gráfico. Após isso, utilizei a função GROUP BY e ORDER BY para finalizar a análise.



