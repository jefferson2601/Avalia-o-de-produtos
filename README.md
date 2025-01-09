Avaliacao de produtos

O gestor pediu para que fosse feita uma analise sobre a popularidade dos produtos oferecidos pela empresa.
usando o sql.

01 - QUANTIDADE TOTAL DE AVALIACOES:

      select count(*) from Reviews

02 - QUANTIDADE DE PRODUTOS AVALIADOS POR CATEGORIAS:

    select 
     count (distinct Product_ID), Category
    from Reviews
    left join PRODUCTS on Reviews.Product_ID = PRODUCTS.ID
    group by Category
    order by Category desc

03 - MEDIA DE AVALIACOES:

    select avg(Rating) from Reviews

04 - MEDIA DE AVALIACAO POR CATEGORIA:

    select 
    Rating, Category
    from ORDERS
    left join PRODUCTS on Product_ID = Product_ID
    group by Category

05 - TOP 10 PRODUTOS EM AVALIACAO:

    select 
     avg (Reviews.Rating) as nota, PRODUCTS.ID, Title
    from Reviews
    left join PRODUCTS on Reviews.Product_ID = PRODUCTS.ID
    group by PRODUCTS.ID
    order by avg (Reviews.Rating) desc
    limit 10

06 - TABELA DE PRODUTOS MAIS VENDIDOS E COM MELHOR AVALIACAO:

    select 
     count (ORDERS.ID) as Quantidade, 
    PRODUCTS.ID, Title, Category,
    avg(Rating) as nota
    from ORDERS
    left join PRODUCTS on ORDERS.Product_ID = PRODUCTS.ID
    group by PRODUCTS.ID
    ORDER by count (ORDERS.ID) desc
    limit 15


      
