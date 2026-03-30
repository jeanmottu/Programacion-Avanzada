<?php

$productos = [
    ["nombre" => "Laptop", "precio" => 1200.50],
    ["nombre" => "Mouse", "precio" => 25.99],
    ["nombre" => "Teclado", "precio" => 45.00],
    ["nombre" => "Monitor", "precio" => 300.75]
];

// Calcular total
$total = 0;
foreach ($productos as $producto) {
    $total += $producto["precio"];
}

?>

<!DOCTYPE html>
<html>
<head>
    <title>Tabla de Productos</title>
    <style>
        table {
            border-collapse: collapse;
            width: 50%;
        }
        th, td {
            border: 1px solid #000;
            padding: 8px;
        }
        th {
            background-color: #eee;
        }
        .total {
            margin-top: 10px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<h2>Lista de Productos</h2>

<table>
    <tr>
        <th>Nombre</th>
        <th>Precio</th>
    </tr>

    <?php foreach ($productos as $producto): ?>
        <tr>
            <td><?php echo $producto["nombre"]; ?></td>
            <td>$<?php echo number_format($producto["precio"], 2); ?></td>
        </tr>
    <?php endforeach; ?>

</table>

<div class="total">
    Total: $<?php echo number_format($total, 2); ?>
</div>

</body>
</html>
