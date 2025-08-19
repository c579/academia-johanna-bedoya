<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ACADEMIA APRENDIZAJE JOHANNA BEDOYA</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f9fbff;
      color: #333;
    }
    header {
      background: #0077cc;
      color: white;
      padding: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    header h1 { margin: 0; }
    nav a {
      margin: 0 10px;
      text-decoration: none;
      color: white;
      font-weight: bold;
    }
    .hero {
      background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
                  url("https://via.placeholder.com/1200x400.png?text=Academia+Johanna+Bedoya");
      background-size: cover;
      background-position: center;
      color: white;
      text-align: center;
      padding: 80px 20px;
    }
    .hero h2 { font-size: 2em; margin-bottom: 10px; }
    .container { padding: 20px; max-width: 1100px; margin: auto; }
    .productos {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
    .producto {
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      padding: 15px;
      text-align: center;
    }
    .producto img { max-width: 100%; border-radius: 10px; }
    button {
      margin-top: 10px;
      padding: 10px;
      background: #0077cc;
      border: none;
      color: white;
      font-weight: bold;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover { background: #005fa3; }
    #carrito {
      margin-top: 30px;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    #carrito h2 { margin-top: 0; }
    .carrito-item {
      display: flex;
      justify-content: space-between;
      margin: 10px 0;
      border-bottom: 1px solid #eee;
      padding-bottom: 5px;
    }
    .pago { margin-top: 20px; display: flex; flex-direction: column; gap: 10px; }
    .whatsapp { background: #25d366; }
    .whatsapp:hover { background: #1ebc59; }
    .nequi { background: #ff006e; }
    .nequi:hover { background: #cc0058; }
    footer {
      background: #0077cc;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 30px;
    }
    footer a {
      color: #ffd700;
      text-decoration: none;
      font-weight: bold;
    }
    @media (max-width: 600px) {
      header { flex-direction: column; text-align: center; }
      nav { margin-top: 10px; }
    }
  </style>
</head>
<body>
  <header>
    <h1>📘 ACADEMIA APRENDIZAJE JOHANNA BEDOYA</h1>
    <nav>
      <a href="#inicio">Inicio</a>
      <a href="#productos">Inventario</a>
      <a href="#carrito">Carrito</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>

  <section class="hero" id="inicio">
    <h2>Bienvenidos a la Academia</h2>
    <p>Formamos tu futuro con programas y productos de calidad.</p>
  </section>

  <div class="container">
    <h2 id="productos">🛍️ Inventario de Productos</h2>
    <div class="productos">
      <div class="producto">
        <img src="https://via.placeholder.com/250x150.png?text=Kit+Uñas" alt="Kit de Uñas">
        <h3>Kit Profesional de Uñas</h3>
        <p>$120.000</p>
        <button onclick="agregarAlCarrito('Kit Profesional de Uñas', 120000)">Agregar</button>
      </div>
      <div class="producto">
        <img src="https://via.placeholder.com/250x150.png?text=Esmaltes" alt="Esmaltes">
        <h3>Set de Esmaltes</h3>
        <p>$80.000</p>
        <button onclick="agregarAlCarrito('Set de Esmaltes', 80000)">Agregar</button>
      </div>
      <div class="producto">
        <img src="https://via.placeholder.com/250x150.png?text=Lámpara+UV" alt="Lámpara UV">
        <h3>Lámpara UV</h3>
        <p>$95.000</p>
        <button onclick="agregarAlCarrito('Lámpara UV', 95000)">Agregar</button>
      </div>
      <div class="producto">
        <img src="https://via.placeholder.com/250x150.png?text=Acrílicos" alt="Acrílicos">
        <h3>Acrílicos</h3>
        <p>$60.000</p>
        <button onclick="agregarAlCarrito('Acrílicos', 60000)">Agregar</button>
      </div>
    </div>

    <div id="carrito">
      <h2>🛒 Carrito de Compras</h2>
      <div id="items"></div>
      <h3>Total: $<span id="total">0</span></h3>

      <div class="pago">
        <!-- Botón WhatsApp -->
        <button class="whatsapp" onclick="enviarWhatsApp()">📲 Finalizar compra por WhatsApp</button>

        <!-- Botón Nequi (informativo) -->
        <button class="nequi" onclick="alert('Realiza tu pago Nequi al número 3104950830')">💳 Pagar con Nequi</button>
      </div>
    </div>
  </div>

  <footer id="contacto">
    <p>📍 Medellín, Colombia</p>
    <p>📞 WhatsApp: <a href="https://wa.me/573104950830" target="_blank" rel="noopener noreferrer">3104950830</a></p>
    <p>📲 Instagram:
      <a href="https://instagram.com/johannabedoyajb?igshid=YmMyMTA2M2Y=" target="_blank" rel="noopener noreferrer">@johannabedoyajb</a>
    </p>
    <p>&copy; 2025 ACADEMIA APRENDIZAJE JOHANNA BEDOYA</p>
  </footer>

  <script>
    let carrito = [];

    function agregarAlCarrito(nombre, precio) {
      carrito.push({ nombre, precio });
      mostrarCarrito();
    }

    function mostrarCarrito() {
      let items = document.getElementById("items");
      let total = 0;
      items.innerHTML = "";
      carrito.forEach((item, index) => {
        total += item.precio;
        items.innerHTML += `
          <div class="carrito-item">
            <span>${item.nombre} - $${item.precio.toLocaleString()}</span>
            <button onclick="eliminarItem(${index})">❌</button>
          </div>
        `;
      });
      document.getElementById("total").innerText = total.toLocaleString();
    }

    function eliminarItem(index) {
      carrito.splice(index, 1);
      mostrarCarrito();
    }

    // Enviar pedido por WhatsApp
    function enviarWhatsApp() {
      if (carrito.length === 0) {
        alert("No has agregado ningún producto.");
        return;
      }
      let telefono = "573104950830"; // Número real en formato internacional
      let mensaje = "Hola, quiero comprar los siguientes productos:\n\n";
      let total = 0;
      carrito.forEach(item => {
        mensaje += `- ${item.nombre}: $${item.precio.toLocaleString()}\n`;
        total += item.precio;
      });
      mensaje += `\nTotal: $${total.toLocaleString()}\n\nMétodo de pago: Nequi (3104950830).`;
      let url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
      window.open(url, "_blank");
    }
  </script>
</body>
</html>
