# Banco.PHP
Criação de banco de dados pelo php.

<?php
// Definição das credenciais de conexão com o banco de dados
$servidor = "localhost"; // Endereço do servidor
$banco = "db_35_teste_php"; // Nome do banco de dados
$usuario_db = "php_ti35_teste"; // Usuário do banco de dados
$senha_db = "abc123"; // Senha do banco de dados

// Estabelece conexão com o banco de dados utilizando MySQLi
$link = mysqli_connect($servidor, $usuario_db, $senha_db, $banco);

// Verifica se a conexão foi bem-sucedida
if (!$link) {
    die("Falha na conexão: " . mysqli_connect_error());
}

// Query para buscar todos os registros da tabela 'tb_clientes'
$sql = "SELECT * FROM tb_clientes";
$result = mysqli_query($link, $sql); // Executa a query e guarda o resultado

?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Consulta Banco</title>
</head>
<body>
    <!-- Criação da tabela para exibição dos dados -->
    <table border="1">
        <tr>
            <td>ID</td>
            <td>Nome</td>
            <td>Endereço</td>
            <td>e-mail</td>
            <td>Data de Nascimento</td>
        </tr>
        <?php
        // Iteração sobre os resultados da query para preenchimento da tabela
        while($tbl = mysqli_fetch_array($result)){
        ?>
        <tr>
            <td><?= $tbl[0] ?></td> <!-- ID do cliente -->
            <td><?= $tbl[1] ?></td> <!-- Nome do cliente -->
            <td><?= $tbl[2] ?></td> <!-- Endereço do cliente -->
            <td><?= $tbl[4] ?></td> <!-- E-mail do cliente -->
            <td><?= $tbl[3] ?></td> <!-- Data de nascimento do cliente -->
        </tr>
        <?php
        }
        // Fecha a conexão com o banco de dados após a consulta
        mysqli_close($link);
        ?>
    </table>
</body>
</html>
