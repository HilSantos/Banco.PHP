# Banco.PHP
Criação de banco de dados pelo php.

<?php
$servidor = "localhost";
$banco = "db_35_teste_php";
$usuario_db = "php_ti35_teste";
$senha_db = "abc123";
$link = mysqli_connect($servidor,$usuario_db,$senha_db,$banco);
$sql = "SELECT * FROM tb_clientes";
$result = mysqli_query($link,$sql);

?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Consulta Banco</title>
</head>
<body>
    <table border="1">
        <tr>
            <td>ID</td>
            <td>Nome</td>
            <td>Endereço</td>
            <td>e-mail</td>
            <td>Data de Nascimento</td>
        </tr>
        <?php
            while($tbl = mysqli_fetch_array($result)){
        ?>
        <tr>
            <td><?= $tbl[0] ?></td>
            <td><?= $tbl[1] ?></td>
            <td><?= $tbl[2] ?></td>
            <td><?= $tbl[4] ?></td>
            <td><?= $tbl[3] ?></td>
        </tr>
            <?php
            }
            mysqli_close($link);
            ?>
    </table>
</body>
</html>
