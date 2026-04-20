<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>ConectaJá - Consultoria</title>
</head>
<body>
    <h2>Consultoria de Infraestrutura - ConectaJá</h2>
    <form action="recomenda_equipamento.php" method="POST"> 
        <label for="ambiente">Tamanho do Ambiente:</label> 
        <select name="ambiente" id="ambiente" required> 
            <option value="">-- Selecione --</option> 
            <option value="residencial">Casa / Apartamento</option> 
            <option value="pequeno_escritorio">Pequeno Escritório (Até 15 máquinas)</option> 
            <option value="data_center">Data Center Corporativo</option> 
        </select>

        <br><br>

        <button type="submit">Ver Recomendação</button>
    </form>
</body>
</html>


<?php
// Captura os dados enviados pelo formulário via método POST
$ambiente = isset($_POST['ambiente']) ? $_POST['ambiente'] : '';

echo "<h1>Recomendação Técnica</h1>";

// Estrutura switch para decidir o equipamento com base no ambiente
switch ($ambiente) {
    case "residencial":
        echo "<h3>Ambiente: Residencial</h3>";
        echo "<p><strong>Equipamento Indicado:</strong> Roteador Wireless (SOHO).</p>";
        echo "<p>Para ambientes residenciais, um roteador Wi-Fi padrão é suficiente para conectar smartphones, TVs e notebooks.</p>";
        break;

    case "pequeno_escritorio":
        echo "<h3>Ambiente: Pequeno Escritório</h3>";
        echo "<p><strong>Equipamento Indicado:</strong> Switch Gerenciável de 24 Portas.</p>";
        echo "<p>Para um escritório, recomendamos o uso de um Switch para conectar os computadores via cabo, garantindo estabilidade e segurança na rede local (LAN).</p>";
        break;

    case "data_center":
        echo "<h3>Ambiente: Datacenter</h3>";
        echo "<p><strong>Equipamento Indicado:</strong> Roteador de Borda e Switch Layer 3.</p>";
        echo "<p>Para Data Centers, é necessária uma infraestrutura robusta com equipamentos de alta capacidade para lidar com grande tráfego de dados e roteamento avançado.</p>";
        break;

    default:
        echo "<p style='color:red;'>Erro: Ambiente não reconhecido em nosso banco de dados.</p>";
        break;
}

echo "<br><a href='index.html'>Voltar ao formulário</a>";
?>
