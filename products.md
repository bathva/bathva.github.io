---
layout: page
title: Our Products
permalink: /products/
---

<div class="product-filters">
  <button class="filter-btn active" data-filter="all">All Products</button>
  <button class="filter-btn" data-filter="vanity">Bathroom Vanities</button>
  <button class="filter-btn" data-filter="shower">Shower Enclosures</button>
  <button class="filter-btn" data-filter="faucet">Faucets & Hardware</button>
</div>

<div class="product-grid">
  <!-- Product 1 -->
  <div class="product-card" data-category="vanity">
    <img src="https://example.com/vanity-1.jpg" alt="Modern Bathroom Vanity">
    <h3>Athena Series Vanity</h3>
    <ul class="product-specs">
      <li><strong>Material:</strong> Solid Wood + Marble Top</li>
      <li><strong>Size:</strong> 1200×480×850mm</li>
      <li><strong>MOQ:</strong> 50 units</li>
    </ul>
    <button class="inquiry-btn" data-product="Athena Vanity">Request Quote</button>
  </div>
  
  <!-- Product 2 -->
  <div class="product-card" data-category="shower">
    <img src="https://example.com/shower-1.jpg" alt="Frameless Shower">
    <h3>Frameless Shower Enclosure</h3>
    <ul class="product-specs">
      <li><strong>Glass:</strong> 8mm Tempered</li>
      <li><strong>Hardware:</strong> 304 Stainless Steel</li>
      <li><strong>MOQ:</strong> 100 units</li>
    </ul>
    <button class="inquiry-btn" data-product="Frameless Shower">Request Quote</button>
  </div>
</div>

<style>
  .product-filters {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin: 30px 0;
    justify-content: center;
  }
  .filter-btn {
    background: #f0f0f0;
    border: 1px solid #ddd;
    padding: 8px 20px;
    cursor: pointer;
  }
  .filter-btn.active {
    background: #1e88e5;
    color: white;
  }
  
  .product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 30px;
    margin-top: 30px;
  }
  .product-card {
    border: 1px solid #eee;
    padding: 20px;
    border-radius: 8px;
    transition: transform 0.3s;
  }
  .product-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  }
  .product-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    border-radius: 4px;
  }
  .product-specs {
    margin: 15px 0;
    padding-left: 20px;
    font-size: 14px;
  }
  .inquiry-btn {
    background: #1e88e5;
    color: white;
    border: none;
    padding: 10px 15px;
    width: 100%;
    cursor: pointer;
  }
</style>

<script>
  // Product filtering
  document.querySelectorAll('.filter-btn').forEach(button => {
    button.addEventListener('click', () => {
      // Update active button
      document.querySelectorAll('.filter-btn').forEach(btn => {
        btn.classList.remove('active');
      });
      button.classList.add('active');
      
      // Filter products
      const category = button.dataset.filter;
      document.querySelectorAll('.product-card').forEach(product => {
        if (category === 'all' || product.dataset.category === category) {
          product.style.display = 'block';
        } else {
          product.style.display = 'none';
        }
      });
    });
  });
  
  // Inquiry buttons
  document.querySelectorAll('.inquiry-btn').forEach(button => {
    button.addEventListener('click', () => {
      const productName = button.dataset.product;
      window.location.href = `/contact?product=${encodeURIComponent(productName)}`;
    });
  });
</script>
