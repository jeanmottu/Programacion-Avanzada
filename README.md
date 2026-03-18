# Programacion-Avanzada
Ejercicios_profesor
Ejercicio 1
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

Ejercicio 2

 <?php

$productos = [
    ["nombre" => "Laptop", "precio" => 1200.50],
    ["nombre" => "Mouse", "precio" => 25.99],
    ["nombre" => "Teclado", "precio" => 45.00],
    ["nombre" => "Monitor", "precio" => 300.75]
];

?>

<!DOCTYPE html>
<html>
<head>
    <title>Productos</title>
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
        tr.selected {
            background-color: yellow;
        }
        .controls {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

<h2>Lista de Productos</h2>

<div class="controls">
    <input type="text" id="filtro" placeholder="Buscar producto...">
    <button onclick="ordenarPorPrecio()">Ordenar por precio ↑</button>
</div>

<table id="tabla">
    <thead>
        <tr>
            <th>Nombre</th>
            <th>Precio</th>
        </tr>
    </thead>
    <tbody>
        <?php foreach ($productos as $producto): ?>
            <tr onclick="toggleSeleccion(this)">
                <td><?php echo $producto["nombre"]; ?></td>
                <td class="precio"><?php echo $producto["precio"]; ?></td>
            </tr>
        <?php endforeach; ?>
    </tbody>
</table>

<script>
// Resaltar fila (toggle)
function toggleSeleccion(fila) {
    fila.classList.toggle("selected");
}

// Ordenar por precio
function ordenarPorPrecio() {
    const tabla = document.getElementById("tabla").getElementsByTagName("tbody")[0];
    const filas = Array.from(tabla.rows);

    filas.sort((a, b) => {
        const precioA = parseFloat(a.cells[1].innerText);
        const precioB = parseFloat(b.cells[1].innerText);
        return precioA - precioB;
    });

    filas.forEach(fila => tabla.appendChild(fila));
}

// Filtro en tiempo real
document.getElementById("filtro").addEventListener("keyup", function() {
    const filtro = this.value.toLowerCase();
    const filas = document.querySelectorAll("#tabla tbody tr");

    filas.forEach(fila => {
        const nombre = fila.cells[0].innerText.toLowerCase();
        fila.style.display = nombre.includes(filtro) ? "" : "none";
    });
});
</script>

</body>
</html>

</body>
</html>
