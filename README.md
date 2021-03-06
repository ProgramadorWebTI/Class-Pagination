# Class-Pagination
Classe de paginação

# Métodos publicos

# MaxPerPage($max)
<p>Método que recebe o valor máximo de registros por página</p>

# Page($name_page)
<p>Método que recebe o nome do page <strong>Ex: </strong>/usuarios?<strong>pagina</strong></p>

# MaxLinks($maxlinks)
<p>Método que recebe o valor máximo de links visiveis a esquerda e a direita da paginação</p>

# Places(array $places_values)
<p>Método que recebe um array para usar como substitutos no Bind</p>

# CreatePagination($Query)
<p>Método que recebe uma string SQL para retornar os itens para a paginação</p>

# CreateLinks()
<p>Método que gera os links de paginação</p>

# Com essa classe podemos fazer varios tipos de busca ao banco inclusive fazendo uso de Join's

# Exemplo de Select básico para apenas uma tabela

<p>$pagination->CreatePagination("SELECT * FROM users");</p>

# Exemplo de Select com JOIN

<p>$pagination->CreatePagination("SELECT v.*,i.* FROM vendas AS v 
                                 INNER JOIN iten_venda AS i 
                                 ON v.id_venda = i.id_venda");</p>

# Exemplo de Select onde será necessário passar os valores que serão substituidos pelo método Places
<p>$pagination->Places(['id' => 1]);</p>
<p>$pagination->CreatePagination("SELECT * FROM pedidos WHERE id_pedido = :id");</p>

# Exemplo de uso:

        require './vendor/autoload.php';

        use App\Helpers\Pagination;

        $pagination = new Pagination();
        try {
            $listagem = $pagination->CreatePagination("SELECT * FROM users");
            $links = $pagination->CreateLinks();
        } catch (Exception $e) {
            die($e->getMessage());
        }
        /* Aqui em listagem voce pode criar uma tabela em html e extrair os dados nesta tabela */
        echo "<pre>";
        var_dump($listagem);
        echo "<pre>";

        echo $links;


