<?php
$resultado = "";
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $ambiente = $_POST['ambiente'] ?? '';
    switch ($ambiente) {
        case "residencial":
            $resultado = "<h3>Residencial</h3>Equipamento Indicado: Roteador Wireless (SOHO).<br>Para ambientes residenciais, um roteador Wi-Fi padrão é suficiente para conectar smartphones, TVs e notebooks.";
            break;
        case "pequeno_escritorio":
            $resultado = "<h3>Pequeno Escritório</h3>Equipamento Indicado: Switch Gerenciável de 24 Portas.<br>Para um escritório, recomendamos o uso de um Switch para conectar os computadores via cabo, garantindo estabilidade e segurança na rede local (LAN).";
            break;
        case "data_center":
            $resultado = "<h3>Data Center</h3>Equipamento Indicado: Roteador de Borda e Switch Layer 3.<br>Para Data Centers, é necessária uma infraestrutura robusta com equipamentos de alta capacidade para lidar com grande tráfego de dados e roteamento avançado.";
            break;
        default:
            $resultado = "<b style='color:red;'>Erro: Ambiente não reconhecido em nosso banco de dados.</b>";
            break;
    }
}
?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>ConectaJá Consultoria</title>
</head>
<body>
    <form method="POST">
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
    <?php if ($resultado) echo "<div style='margin-top:20px;'>$resultado</div>"; ?>
</body>
</html>
