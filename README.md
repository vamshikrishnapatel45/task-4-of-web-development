<!DOCTYPE html>
<html>
<head>
  <title>Product List</title>
  <style>
    body { font-family: sans-serif; padding: 20px; }
    .product { border: 1px solid #ccc; padding: 10px; margin: 5px; border-radius: 5px; }
  </style>
</head>
<body>
  <h2>Product Listing</h2>
  <select id="filter" onchange="filterProducts()">
    <option value="all">All</option>
    <option value="electronics">Electronics</option>
    <option value="clothing">Clothing</option>
  </select>

  <select id="sort" onchange="sortProducts()">
    <option value="asc">Price: Low to High</option>
    <option value="desc">Price: High to Low</option>
  </select>

  <div id="products"></div>

  <script>
    const data = [
      { name: "T-Shirt", category: "clothing", price: 20, rating: 4.2 },
      { name: "Phone", category: "electronics", price: 499, rating: 4.7 },
      { name: "Headphones", category: "electronics", price: 99, rating: 4.3 },
      { name: "Jeans", category: "clothing", price: 40, rating: 4.0 },
    ];

    let products = [...data];

    function display(list) {
      document.getElementById("products").innerHTML = list
        .map(p => `<div class="product">
                    <h3>${p.name}</h3>
                    <p>Category: ${p.category}</p>
                    <p>Price: $${p.price}</p>
                    <p>Rating: ${p.rating}</p>
                   </div>`).join('');
    }

    function filterProducts() {
      const filter = document.getElementById("filter").value;
      products = filter === "all" ? data : data.filter(p => p.category === filter);
      display(products);
    }

    function sortProducts() {
      const sort = document.getElementById("sort").value;
      products.sort((a, b) => sort === "asc" ? a.price - b.price : b.price - a.price);
      display(products);
    }

    display(products);
  </script>
</body>
</html>
