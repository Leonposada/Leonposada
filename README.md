<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>El Jicaro</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        nav {
            display: flex;
            justify-content: center;
            background-color: #444;
            flex-wrap: wrap;
        }
        nav a {
            color: white;
            padding: 14px 20px;
            text-decoration: none;
            text-align: center;
            flex: 1 1 calc(12.5% - 20px);
        }
        nav a:hover {
            background-color: #ddd;
            color: black;
        }
        .container {
            width: 90%;
            margin: 20px auto;
            padding: 20px;
            background-color: #ffffff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            overflow: auto;
        }
        .products {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
        .product {
            flex: 1 1 calc(25% - 20px);
            box-sizing: border-box;
            margin: 10px;
            padding: 20px;
            border: 1px solid #ddd;
            background-color: #fafafa;
            text-align: center;
        }
        .product img {
            max-width: 100%;
            height: auto;
            cursor: pointer;
            display: block;
            margin: 0 auto;
        }
        footer {
            text-align: center;
            margin-top: 20px;
            padding: 10px;
            background-color: #333;
            color: #ffffff;
        }
        /* Estilos para las pestañas */
        .tab {
            display: none;
        }
        .tab.active {
            display: block;
        }
        .tab-links {
            display: flex;
            justify-content: center;
            background-color: #444;
            margin-bottom: 20px;
        }
        .tab-links a {
            color: white;
            padding: 14px 20px;
            text-decoration: none;
            text-align: center;
        }
        .tab-links a:hover {
            background-color: #ddd;
            color: black;
        }
        /* Estilos para el buscador */
        #searchResults {
            display: none;
            margin-top: 20px;
        }
        /* Ocultar la pestaña de búsqueda en el menú de navegación */
        #searchTabLink {
            display: none;
        }
    </style>
    <script>
        function showTab(tabId) {
            var tabs = document.getElementsByClassName('tab');
            for (var i = 0; i < tabs.length; i++) {
                tabs[i].classList.remove('active');
            }
            document.getElementById(tabId).classList.add('active');
        }

        function searchProducts() {
            var input = document.getElementById('searchInput').value.toLowerCase();
            var productElements = document.getElementsByClassName('product');
            var searchResultsContainer = document.getElementById('searchResults');
            var foundProducts = [];

            searchResultsContainer.innerHTML = ''; // Limpiar resultados anteriores
            searchResultsContainer.style.display = 'none';

            for (var i = 0; i < productElements.length; i++) {
                var productName = productElements[i].getElementsByTagName('h3')[0].innerText.toLowerCase();
                if (productName.includes(input)) {
                    foundProducts.push(productElements[i].cloneNode(true));
                }
            }

            if (foundProducts.length > 0) {
                showTab('searchResults');
                var resultsInnerHTML = '<h2>Resultados de la búsqueda</h2><div class="products">';
                for (var i = 0; i < foundProducts.length; i++) {
                    resultsInnerHTML += foundProducts[i].outerHTML;
                }
                resultsInnerHTML += '</div>';
                searchResultsContainer.innerHTML = resultsInnerHTML;
                searchResultsContainer.style.display = 'block';
            } else {
                searchResultsContainer.innerHTML = '<h2>No se encontraron resultados</h2>';
                searchResultsContainer.style.display = 'block';
            }
        }

        function clearSearch() {
            document.getElementById('searchInput').value = '';
            showTab('productos1'); // Volver a la primera pestaña
        }
    </script>
</head>
<body>
    <header>
        <h1>Bienvenido a Nuestra Tienda en Línea</h1>
        <!-- Buscador -->
        <input type="text" id="searchInput" onkeyup="searchProducts()" placeholder="Buscar productos...">
    </header>
    <nav>
        <a href="#productos1" onclick="showTab('productos1')">Botellas</a>
        <a href="#productos2" onclick="showTab('productos2')">Categoría 2</a>
        <a href="#productos3" onclick="showTab('productos3')">Categoría 3</a>
        <a href="#productos4" onclick="showTab('productos4')">Categoría 4</a>
        <a href="#productos5" onclick="showTab('productos5')">Categoría 5</a>
        <a href="#productos6" onclick="showTab('productos6')">Categoría 6</a>
        <a href="#productos7" onclick="showTab('productos7')">Categoría 7</a>
        <a href="#productos8" onclick="showTab('productos8')">Categoría 8</a>
        <!-- Enlace a la pestaña de búsqueda, oculto en el menú -->
        <a id="searchTabLink" href="#searchResults" onclick="searchProducts()">Buscar Resultados</a>
    </nav>
    <div class="container">
        <!-- Resultados de la búsqueda -->
        <div id="searchResults" class="tab">
            <!-- Aquí se mostrarán los productos que coincidan con la búsqueda -->
        </div>

        <!-- Productos de Botellas (Categoría 1) -->
        <div id="productos1" class="tab active">
            <h2>Productos - Categoría 1</h2>
            <div class="products">
                <div class="product">
                    <button onclick="window.location.href='https://www.ejemplo.com/producto1.1'">
                        <img src="ruta_de_tu_imagen1.jpg" alt="Producto 1.1">
                        <h3>Vientre</h3>
                        <p>Es para cristes, fibromas, fluido blanco, dolores menstruales y principios de cáncer</p>
                        <p>Precio: $3.00</p>
                    </button>
                </div>
                <div class="product">
                    <button onclick="window.location.href='https://wa.link/lkqacf'">
                        <img src="ruta_de_tu_imagen2.jpg" alt="Producto 1.2">
                        <h3>Limpria Matris</h3>
                        <p>Es para cristes, fibromas, fluido blanco, dolores menstruales.</p>
                        <p>Precio: $2.00</p>
                    </button>
                </div>
            </div>
        </div>

        <!-- Productos de Categoría 2 -->
        <div id="productos2" class="tab">
            <h2>Productos - Categoría 2</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 2 -->
            </div>
        </div>

        <!-- Productos de Categoría 3 -->
        <div id="productos3" class="tab">
            <h2>Productos - Categoría 3</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 3 -->
            </div>
        </div>

        <!-- Productos de Categoría 4 -->
        <div id="productos4" class="tab">
            <h2>Productos - Categoría 4</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 4 -->
            </div>
        </div>

        <!-- Productos de Categoría 5 -->
        <div id="productos5" class="tab">
            <h2>Productos - Categoría 5</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 5 -->
            </div>
        </div>

        <!-- Productos de Categoría 6 -->
        <div id="productos6" class="tab">
            <h2>Productos - Categoría 6</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 6 -->
            </div>
        </div>

        <!-- Productos de Categoría 7 -->
        <div id="productos7" class="tab">
            <h2>Productos - Categoría 7</h2>
            <div class="products">
                <div class="product">
                    <button onclick="window.location.href='https://www.ejemplo.com/producto7.1'">
                        <img src="ruta_de_tu_imagen3.jpg" alt="Producto 7.1">
                        <h3>Te de Viente</h3>
                        <p>Es para cristes, fibromas, fluido blanco, dolores menstruales.</p>
                        <p>Precio: $2.50</p>
                    </button>
                </div>
            </div>
        </div>

        <!-- Productos de Categoría 8 -->
        <div id="productos8" class="tab">
            <h2>Productos - Categoría 8</h2>
            <div class="products">
                <!-- Coloca aquí los productos de la Categoría 8 -->
            </div>
        </div>
    </div>
    <footer>
        <p>&copy; 2024 El Jicaro. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
