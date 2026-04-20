<?php
$res = "";
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $a = $_POST['ambiente'] ?? '';
    switch ($a) {
        case "residencial":
            $res = "<b>Residencial</b><br>Equipamento Indicado: Roteador Wireless (SOHO).<br>Para ambientes residenciais, um roteador Wi-Fi padrão é suficiente.";
            break;
        case "pequeno_escritorio":
            $res = "<b>Pequeno Escritório</b><br>Equipamento Indicado: Switch Gerenciável de 24 Portas.<br>Recomendamos o uso de um Switch para conectar os computadores via cabo.";
            break;
        case "data_center":
            $res = "<b>Data Center</b><br>Equipamento Indicado: Roteador de Borda e Switch Layer 3.<br>Infraestrutura robusta para alta capacidade.";
            break;
        default:
            $res = "<span style='color:red'>Erro: Ambiente não reconhecido.</span>";
            break;
    }
}
?>
<!DOCTYPE html>
<html>
<head><meta charset="UTF-8"></head>
<body>
    <form method="POST">
        <select name="ambiente" required>
            <option value="">-- Selecione --</option>
            <option value="residencial">Casa / Apartamento</option>
            <option value="pequeno_escritorio">Pequeno Escritório</option>
            <option value="data_center">Data Center Corporativo</option>
        </select>
        <button type="submit">Ver Recomendação</button>
    </form>
    <div style="margin-top:20px;"><?php echo $res; ?></div>
</body>
</html>
