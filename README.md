<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pizzaria Marcondes Ferreira</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #fff8f0;
      color: #333;
    }
    header {
      background-color: #b22222;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 1rem;
      background-color: #8b0000;
      padding: 0.5rem;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
    }
    .hero {
      background: url('https://images.unsplash.com/photo-1601924572561-c9ad5b6a9b31') center/cover no-repeat;
      color: white;
      text-align: center;
      padding: 4rem 1rem;
    }
    .hero h1 {
      font-size: 2.5rem;
    }
    .menu {
      padding: 2rem;
      text-align: center;
    }
    .menu h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
    }
    .pizza {
      background: #fff;
      border: 1px solid #ccc;
      border-radius: 8px;
      padding: 1rem;
      margin: 1rem auto;
      max-width: 400px;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    .pizza h3 {
      margin: 0.5rem 0;
    }
    .pizza button {
      background-color: #b22222;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
    }
    .carrinho {
      padding: 2rem;
      background: #f9f9f9;
      text-align: center;
    }
    .carrinho ul {
      list-style: none;
      padding: 0;
    }
    .carrinho li {
      margin: 0.5rem 0;
    }
    footer {
      background: #333;
      color: white;
      text-align: center;
      padding: 1rem;
      margin-top: 2rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Pizzaria Marcondes Ferreira</h1>
  </header>
  <nav>
    <a href="#menu">Cardápio</a>
    <a href="#carrinho">Carrinho</a>
    <a href="#contato">Contato</a>
  </nav>
  <section class="hero">
    <h1>Peça sua pizza favorita agora!</h1>
    <p>Entrega e retirada disponíveis</p>
  </section>
  <section class="menu" id="menu">
    <h2>Nosso Cardápio</h2>
    <div class="pizza">
      <h3>Frango com Catupiry - R$25,00</h3>
      <button onclick="adicionar('Frango com Catupiry', 25)">Adicionar ao carrinho</button>
    </div>
    <div class="pizza">
      <h3>Quatro Queijos - R$40,00</h3>
      <button onclick="adicionar('Quatro Queijos', 40)">Adicionar ao carrinho</button>
    </div>
    <div class="pizza">
      <h3>Bacon - R$25,00</h3>
      <button onclick="adicionar('Bacon', 25)">Adicionar ao carrinho</button>
    </div>
  </section>
  <section class="carrinho" id="carrinho">
    <h2>Seu Carrinho</h2>
    <ul id="lista-carrinho"></ul>
    <p id="total"></p>
    <a id="whatsapp-link" href="#" target="_blank">
      <button>Finalizar pedido via WhatsApp</button>
    </a>
  </section>
  <footer id="contato">
    <p>Rua da Pizza, 123 - Centro - Atendimento via WhatsApp</p>
    <p>&copy; 2025 Pizzaria Marcondes Ferreira</p>
  </footer>  <script>
    let carrinho = [];
    function adicionar(nome, preco) {
      carrinho.push({ nome, preco });
      atualizarCarrinho();
    }

    function atualizarCarrinho() {
      const lista = document.getElementById('lista-carrinho');
      const totalEl = document.getElementById('total');
      const whatsappLink = document.getElementById('whatsapp-link');

      lista.innerHTML = '';
      let total = 0;
      let textoPedido = 'Olá! Gostaria de pedir:%0A';

      carrinho.forEach((item) => {
        const li = document.createElement('li');
        li.textContent = `${item.nome} - R$${item.preco},00`;
        lista.appendChild(li);
        total += item.preco;
        textoPedido += `- ${item.nome} (R$${item.preco},00)%0A`;
      });

      totalEl.textContent = `Total: R$${total},00`;
      textoPedido += `Total: R$${total},00`;

      whatsappLink.href = `https://wa.me/45999818129?text=${textoPedido}`;
    }
  </script></body>
</html>