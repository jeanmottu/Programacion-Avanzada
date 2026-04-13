Ejercicio 1 de php

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

Ejercicio 2 de php

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

Ejercicio 3 con jquery

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        .resaltado{ background: red;}
        .grande{font-size: 32px;}
    </style>
</head>
<body> 

<h1>Demo Jquery</h1>
<h2> hide() - show() - taggle()</h2>
<button id="btn-ocultar">Ocultar</button>
<button id="btn-mostrar">Mostrar</button>
<button id="btn-toggle">Toggle</button>

<p id="parrafo"> este parrafo se va a manipular con jquery</p>
<script>
        $("#btn-ocultar").click(function(){
            $("#parrafo").hide();
        });
        $("#btn-mostrar").click(function(){
            $("#parrafo").show();
        });
        $("#btn-toggle").click(function(){
            $("#parrafo").toggle();
        });
       </script>

       <h2> 2 text () - html - val()</h2>
       <p id="parrafo2"> este parrafo se va a manipular con jquery</p>
    <button id="btn-text">Cambiar texto</button>
    <button id="btn-html">Cambiar html</button>
    <br></br>
    <input type="text" id="mi-input">
    <input type="text" id="input-text" placeholder="Escribe algo">
    <p id="output-input"></p>

    <script>
        $("#btn-text").click(function(){
            $("#parrafo2").text("El texto ha sido cambiado");
        });
        $("#btn-html").click(function(){
            $(selector).html(<strong> ahora esta en negrita con jquery </strong>);
        });
        $("#btn-leer").click(function(){
          const valor=$("#mi-input").val(); 
          $('#output-input').text("Escribiste:" + valor); 
        });

        <h2> Evento - output-input </h2>
<button id="btn contador">
<p id="output-contador">Clics: 0 </p>
<br>
<input type="text" id="input-tiempo-real">
<p id="output-tiempo real"></p>

<script>
let clics=0
$

</script>

<h2> addClass()- removeClass() toggle()</h2>
<h3 id="mi-titulo"> titulo para cambiar la letra </h3>
<button id="btn-agrandar"> Agrandar</button>
<button id="btn-achicar"> Achicar</button>
<br></br>
<p> Hace click en cada item</p>
<ul id="mi-lista" style="list-style:none; padding:0">
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item1</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item2</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item3</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item4</li>
</ul>;
<script>
$(selector).click(function (e){
    e.preventDefault();
});
</script>

<script>
$('#btn-agrandar').click(function(){
$('#mi-titulo').addClass('grande');;
});

$('#btn-achicar').click(function(){
$('#mi-titulo').removeClass('grande');;
});

$('#mi-lista li').click(function(){
$(this).toggleClass('resaltado');

});
  </script>      
</body>
</html>

Ejercicio 3 25 de marzo
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        .resaltado{ background: red;}
        .grande{font-size: 32px;}
    </style>
</head>
<body> 

<h1>Demo Jquery</h1>
<h2> hide() - show() - taggle()</h2>
<button id="btn-ocultar">Ocultar</button>
<button id="btn-mostrar">Mostrar</button>
<button id="btn-toggle">Toggle</button>

<p id="parrafo"> este parrafo se va a manipular con jquery</p>
<script>
        $("#btn-ocultar").click(function(){
            $("#parrafo").hide();
        });
        $("#btn-mostrar").click(function(){
            $("#parrafo").show();
        });
        $("#btn-toggle").click(function(){
            $("#parrafo").toggle();
        });
       </script>

       <h2> 2 text () - html - val()</h2>
       <p id="parrafo2"> este parrafo se va a manipular con jquery</p>
    <button id="btn-text">Cambiar texto</button>
    <button id="btn-html">Cambiar html</button>
    <br></br>
    <input type="text" id="mi-input">
    <input type="text" id="input-text" placeholder="Escribe algo">
    <p id="output-input"></p>

    <script>
        $("#btn-text").click(function(){
            $("#parrafo2").text("El texto ha sido cambiado");
        });
        $("#btn-html").click(function(){
            $(selector).html(<strong> ahora esta en negrita con jquery </strong>);
        });
        $("#btn-leer").click(function(){
          const valor=$("#mi-input").val(); 
          $('#output-input').text("Escribiste:" + valor); 
        });

        <h2> Evento - output-input </h2>
<button id="btn contador">
<p id="output-contador">Clics: 0 </p>
<br>
<input type="text" id="input-tiempo-real">
<p id="output-tiempo real"></p>

<script>
let clics=0
$

</script>

<h2> addClass()- removeClass() toggle()</h2>
<h3 id="mi-titulo"> titulo para cambiar la letra </h3>
<button id="btn-agrandar"> Agrandar</button>
<button id="btn-achicar"> Achicar</button>
<br></br>
<p> Hace click en cada item</p>
<ul id="mi-lista" style="list-style:none; padding:0">
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item1</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item2</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item3</li>
    <li style="padding:6px; border-button:1px solid #eee; curspr:ointer;">item4</li>
</ul>;
<script>
$(selector).click(function (e){
    e.preventDefault();
});
</script>

<script>
$('#btn-agrandar').click(function(){
$('#mi-titulo').addClass('grande');;
});

$('#btn-achicar').click(function(){
$('#mi-titulo').removeClass('grande');;
});

$('#mi-lista li').click(function(){
$(this).toggleClass('resaltado');

});
  </script>      
</body>
</html>

Ejercicio 5 usando laravel, php y jquery
