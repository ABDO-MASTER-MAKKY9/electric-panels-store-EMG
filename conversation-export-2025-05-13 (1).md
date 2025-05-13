from.flask
اصنع موقع لبيع لوحات الكهرباء
### BLACKBOX.AI
from
You want me to create a website for selling electrical panels. I will create a modern, mobile-responsive single-page HTML file with inline CSS and JavaScript. The site will have a homepage showcasing different electrical panels with images, descriptions, and prices. It will have a clean, professional design with a header, featured products, and a contact or order section with a form. UI must be modern, visually appealing, and fit nicely for mobile screens (max 600px height and 350px width) without scrolling. I will add interactive elements for usability on mobile. I will embed all CSS and JS inline.


`electric_panels_store.html`
```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no" />
<title>متجر لوحات الكهرباء</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cairo&display=swap');
  body {
    margin: 0;
    font-family: 'Cairo', sans-serif;
    background: #f5f7fa;
    color: #333;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #005f73;
    color: #fff;
    padding: 1rem 1.5rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1px;
  }
  main {
    padding: 15px;
    max-width: 350px;
    margin: 0 auto;
  }
  h2.section-title {
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 10px;
    border-bottom: 2px solid #0a9396;
    padding-bottom: 5px;
  }
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  .product-card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    overflow: hidden;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 5px 15px rgb(0 0 0 / 0.15);
  }
  .product-img {
    width: 100%;
    height: 200px;
    object-fit: contain;
    background: #e0f2f1;
  }
  .product-info {
    padding: 10px 15px;
    text-align: right;
  }
  .product-info h3 {
    font-size: 1rem;
    margin: 0 0 6px;
    color: #005f73;
  }
  .product-info p {
    font-size: 0.85rem;
    color: #666;
    margin: 0 0 8px;
  }
  .product-info .price {
    font-weight: 700;
    color: #ee6c4d;
    font-size: 1rem;
  }
  button.order-btn {
    display: block;
    width: 100%;
    background: #ee6c4d;
    color: #fff;
    border: none;
    padding: 10px 0;
    border-radius: 0 0 8px 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button.order-btn:hover {
    background: #d94e30;
  }
  form#order-form {
    background: #fff;
    margin-top: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    padding: 15px;
  }
  form#order-form h2 {
    margin-top: 0;
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: center;
  }
  label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9rem;
    color: #333;
    text-align: right;
  }
  input, select, textarea {
    width: 100%;
    padding: 8px 10px;
    border: 1.5px solid #ccc;
    border-radius: 6px;
    font-size: 0.9rem;
    color: #222;
    box-sizing: border-box;
    font-family: 'Cairo', sans-serif;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #0a9396;
    box-shadow: 0 0 5px #0a9396aa;
  }
  textarea {
    resize: vertical;
    min-height: 60px;
  }
  button#submit-order {
    background: #005f73;
    color: white;
    font-weight: 700;
    border: none;
    padding: 12px 0;
    width: 100%;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button#submit-order:hover {
    background: #0a9396;
  }
  .success-message {
    background: #94d82d;
    color: #1b4332;
    font-weight: 700;
    text-align: center;
    border-radius: 6px;
    margin-top: 15px;
    padding: 10px;
    display: none;
  }
  @media (max-width: 350px) {
    main {
      padding: 12px;
    }
    .product-img {
      height: 150px;
    }
  }
</style>
</head>
<body>
<header>متجر لوحات الكهرباء</header>
<main>
  <section>
    <h2 class="section-title">أحدث اللوحات الكهربائية</h2>
    <div class="product-list" id="product-list">
      <!-- Products will be inserted here by JS -->
    </div>
  </section>
  <section>
    <form id="order-form">
      <h2>اطلب لوحتك الكهربائية</h2>
      <label for="product-select">اختر اللوحة</label>
      <select id="product-select" required>
        <option value="">-- اختر اللوحة --</option>
      </select>
      <label for="name">الاسم الكامل</label>
      <input type="text" id="name" placeholder="اسمك" required />
      <label for="phone">رقم الهاتف</label>
      <input type="tel" id="phone" placeholder="رقم الهاتف" pattern="[0-9\u0660-\u0669+\s-]{6,15}" required />
      <label for="address">العنوان (اختياري)</label>
      <textarea id="address" placeholder="مكان التسليم"></textarea>
      <button type="submit" id="submit-order">إرسال الطلب</button>
      <div class="success-message" id="success-msg">تم استلام طلبك بنجاح! سنتواصل معك قريبًا.</div>
    </form>
  </section>
</main>
<script>
  const products = [
    {
      id: "panel1",
      name: "لوحة كهرباء منزلية 16 أمبير",
      description: "لوحة مع مقاييس وأمان مضاد للتسرب، مناسبة للمنازل الصغيرة.",
      price: "350 ريال",
      img: "https://images.unsplash.com/photo-1572286413584-962f33a58d1b?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel2",
      name: "لوحة كهرباء صناعية 50 أمبير",
      description: "لوحة متقدمة تتحمل الأحمال الصناعية الكبيرة للحماية المثلى.",
      price: "1200 ريال",
      img: "https://images.unsplash.com/photo-1556747706-9fb704c1f5b3?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel3",
      name: "لوحة توزيع ذكية",
      description: "لوحة ذكية مع إمكانية التحكم عبر تطبيق وميزات توفير الطاقة.",
      price: "1800 ريال",
      img: "https://images.unsplash.com/photo-1618354696607-30bb5395b88d?auto=format&fit=crop&w=400&q=80"
    }
  ];

  const productListEl = document.getElementById('product-list');
  const productSelectEl = document.getElementById('product-select');

  function renderProducts() {
    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${product.img}" alt="${product.name}" class="product-img" />
        <div class="product-info">
          <h3>${product.name}</h3>
          <p>${product.description}</p>
          <p class="price">${product.price}</p>
        </div>
        <button class="order-btn" data-product-id="${product.id}">اطلب الآن</button>
      `;
      productListEl.appendChild(card);

      // Add option to select dropdown
      const option = document.createElement('option');
      option.value = product.id;
      option.textContent = product.name + " - " + product.price;
      productSelectEl.appendChild(option);
    });
  }

  // Handle order form submission
  const orderForm = document.getElementById('order-form');
  const successMsg = document.getElementById('success-msg');
  orderForm.addEventListener('submit', function(e) {
    e.preventDefault();
    if (!orderForm.checkValidity()) {
      orderForm.reportValidity();
      return;
    }
    const productId = productSelectEl.value;
    const product = products.find(p => p.id === productId);
    if (!product) {
      alert('الرجاء اختيار لوحة');
      return;
    }
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const address = document.getElementById('address').value.trim();

    // For demonstration: simulate sending order
    successMsg.style.display = 'block';
    orderForm.reset();
    productSelectEl.value = "";
    setTimeout(() => {
      successMsg.style.display = 'none';
    }, 5000);
  });

  // Handle "اطلب الآن" buttons on product cards
  productListEl.addEventListener('click', function(e) {
    if (e.target.classList.contains('order-btn')) {
      const productId = e.target.getAttribute('data-product-id');
      productSelectEl.value = productId;
      document.getElementById('name').focus();
      window.scrollTo({ top: orderForm.offsetTop - 10, behavior: 'smooth' });
    }
  })

  // Initialize
  renderProducts();
</script>
</body>
</html>

```
### YOU
شيل اختر لوحه وخليه اكتب نوع اللوح والمقاست اسم المصنعEMG
### BLACKBOX.AI


The request is to remove the dropdown with "اختر اللوحة" in the order form and instead have a free text input where the user can write the type and size of the panel. The form label should show "اكتب نوع اللوح والمقاس" and also have a field for "اسم المصنع" with label "اسم المصنع EMG". So I will remove the select dropdown and replace it with two text input fields for these.

I will update the form accordingly and the JS validation to match the new inputs.


`electric_panels_store.html`
```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no" />
<title>متجر لوحات الكهرباء</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cairo&display=swap');
  body {
    margin: 0;
    font-family: 'Cairo', sans-serif;
    background: #f5f7fa;
    color: #333;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #005f73;
    color: #fff;
    padding: 1rem 1.5rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1px;
  }
  main {
    padding: 15px;
    max-width: 350px;
    margin: 0 auto;
  }
  h2.section-title {
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 10px;
    border-bottom: 2px solid #0a9396;
    padding-bottom: 5px;
  }
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  .product-card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    overflow: hidden;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 5px 15px rgb(0 0 0 / 0.15);
  }
  .product-img {
    width: 100%;
    height: 200px;
    object-fit: contain;
    background: #e0f2f1;
  }
  .product-info {
    padding: 10px 15px;
    text-align: right;
  }
  .product-info h3 {
    font-size: 1rem;
    margin: 0 0 6px;
    color: #005f73;
  }
  .product-info p {
    font-size: 0.85rem;
    color: #666;
    margin: 0 0 8px;
  }
  .product-info .price {
    font-weight: 700;
    color: #ee6c4d;
    font-size: 1rem;
  }
  button.order-btn {
    display: block;
    width: 100%;
    background: #ee6c4d;
    color: #fff;
    border: none;
    padding: 10px 0;
    border-radius: 0 0 8px 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button.order-btn:hover {
    background: #d94e30;
  }
  form#order-form {
    background: #fff;
    margin-top: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    padding: 15px;
  }
  form#order-form h2 {
    margin-top: 0;
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: center;
  }
  label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9rem;
    color: #333;
    text-align: right;
  }
  input, select, textarea {
    width: 100%;
    padding: 8px 10px;
    border: 1.5px solid #ccc;
    border-radius: 6px;
    font-size: 0.9rem;
    color: #222;
    box-sizing: border-box;
    font-family: 'Cairo', sans-serif;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #0a9396;
    box-shadow: 0 0 5px #0a9396aa;
  }
  textarea {
    resize: vertical;
    min-height: 60px;
  }
  button#submit-order {
    background: #005f73;
    color: white;
    font-weight: 700;
    border: none;
    padding: 12px 0;
    width: 100%;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button#submit-order:hover {
    background: #0a9396;
  }
  .success-message {
    background: #94d82d;
    color: #1b4332;
    font-weight: 700;
    text-align: center;
    border-radius: 6px;
    margin-top: 15px;
    padding: 10px;
    display: none;
  }
  @media (max-width: 350px) {
    main {
      padding: 12px;
    }
    .product-img {
      height: 150px;
    }
  }
</style>
</head>
<body>
<header>متجر لوحات الكهرباء</header>
<main>
  <section>
    <h2 class="section-title">أحدث اللوحات الكهربائية</h2>
    <div class="product-list" id="product-list">
      <!-- Products will be inserted here by JS -->
    </div>
  </section>
  <section>
    <form id="order-form">
      <h2>اطلب لوحتك الكهربائية</h2>
      <label for="panel-type">اكتب نوع اللوح والمقاس</label>
      <input type="text" id="panel-type" placeholder="مثال: لوحة منزلية 16 أمبير" required />
      <label for="factory-name">اسم المصنع EMG</label>
      <input type="text" id="factory-name" placeholder="اكتب اسم المصنع" required />
      <label for="name">الاسم الكامل</label>
      <input type="text" id="name" placeholder="اسمك" required />
      <label for="phone">رقم الهاتف</label>
      <input type="tel" id="phone" placeholder="رقم الهاتف" pattern="[0-9\u0660-\u0669+\s-]{6,15}" required />
      <label for="address">العنوان (اختياري)</label>
      <textarea id="address" placeholder="مكان التسليم"></textarea>
      <button type="submit" id="submit-order">إرسال الطلب</button>
      <div class="success-message" id="success-msg">تم استلام طلبك بنجاح! سنتواصل معك قريبًا.</div>
    </form>
  </section>
</main>
<script>
  const products = [
    {
      id: "panel1",
      name: "لوحة كهرباء منزلية 16 أمبير",
      description: "لوحة مع مقاييس وأمان مضاد للتسرب، مناسبة للمنازل الصغيرة.",
      price: "350 ريال",
      img: "https://images.unsplash.com/photo-1572286413584-962f33a58d1b?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel2",
      name: "لوحة كهرباء صناعية 50 أمبير",
      description: "لوحة متقدمة تتحمل الأحمال الصناعية الكبيرة للحماية المثلى.",
      price: "1200 ريال",
      img: "https://images.unsplash.com/photo-1556747706-9fb704c1f5b3?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel3",
      name: "لوحة توزيع ذكية",
      description: "لوحة ذكية مع إمكانية التحكم عبر تطبيق وميزات توفير الطاقة.",
      price: "1800 ريال",
      img: "https://images.unsplash.com/photo-1618354696607-30bb5395b88d?auto=format&fit=crop&w=400&q=80"
    }
  ];

  const productListEl = document.getElementById('product-list');

  function renderProducts() {
    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${product.img}" alt="${product.name}" class="product-img" />
        <div class="product-info">
          <h3>${product.name}</h3>
          <p>${product.description}</p>
          <p class="price">${product.price}</p>
        </div>
        <button class="order-btn" data-panel-type="${product.name}">اطلب الآن</button>
      `;
      productListEl.appendChild(card);
    });
  }

  // Handle order form submission
  const orderForm = document.getElementById('order-form');
  const successMsg = document.getElementById('success-msg');
  orderForm.addEventListener('submit', function(e) {
    e.preventDefault();
    if (!orderForm.checkValidity()) {
      orderForm.reportValidity();
      return;
    }
    const panelType = document.getElementById('panel-type').value.trim();
    const factoryName = document.getElementById('factory-name').value.trim();
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const address = document.getElementById('address').value.trim();

    if(panelType.length < 3) {
      alert('يرجى كتابة نوع اللوح والمقاس بطريقة واضحة');
      return;
    }
    if(factoryName.length < 2) {
      alert('يرجى كتابة اسم المصنع');
      return;
    }
    if(name.length < 3) {
      alert('يرجى كتابة الاسم الكامل');
      return;
    }
    if(phone.length < 6) {
      alert('يرجى كتابة رقم الهاتف صحيح');
      return;
    }

    // For demonstration: simulate sending order
    successMsg.style.display = 'block';
    orderForm.reset();
    setTimeout(() => {
      successMsg.style.display = 'none';
    }, 5000);
  });

  // Handle "اطلب الآن" buttons on product cards
  productListEl.addEventListener('click', function(e) {
    if (e.target.classList.contains('order-btn')) {
      const panelTypeName = e.target.getAttribute('data-panel-type');
      document.getElementById('panel-type').value = panelTypeName;
      document.getElementById('factory-name').focus();
      window.scrollTo({ top: orderForm.offsetTop - 10, behavior: 'smooth' });
    }
  })

  // Initialize
  renderProducts();
</script>
</body>
</html>

```
### YOU
شيل اسم المصنع
### BLACKBOX.AI

I will remove the "اسم المصنع EMG" field from the order form entirely as requested. The input and its label will be removed, and the script will be updated accordingly to remove validation and usage of that field.

I will now prepare the full updated HTML file for you.


`electric_panels_store.html`
```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no" />
<title>متجر لوحات الكهرباء</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cairo&display=swap');
  body {
    margin: 0;
    font-family: 'Cairo', sans-serif;
    background: #f5f7fa;
    color: #333;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #005f73;
    color: #fff;
    padding: 1rem 1.5rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1px;
  }
  main {
    padding: 15px;
    max-width: 350px;
    margin: 0 auto;
  }
  h2.section-title {
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 10px;
    border-bottom: 2px solid #0a9396;
    padding-bottom: 5px;
  }
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  .product-card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    overflow: hidden;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 5px 15px rgb(0 0 0 / 0.15);
  }
  .product-img {
    width: 100%;
    height: 200px;
    object-fit: contain;
    background: #e0f2f1;
  }
  .product-info {
    padding: 10px 15px;
    text-align: right;
  }
  .product-info h3 {
    font-size: 1rem;
    margin: 0 0 6px;
    color: #005f73;
  }
  .product-info p {
    font-size: 0.85rem;
    color: #666;
    margin: 0 0 8px;
  }
  .product-info .price {
    font-weight: 700;
    color: #ee6c4d;
    font-size: 1rem;
  }
  button.order-btn {
    display: block;
    width: 100%;
    background: #ee6c4d;
    color: #fff;
    border: none;
    padding: 10px 0;
    border-radius: 0 0 8px 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button.order-btn:hover {
    background: #d94e30;
  }
  form#order-form {
    background: #fff;
    margin-top: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    padding: 15px;
  }
  form#order-form h2 {
    margin-top: 0;
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: center;
  }
  label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9rem;
    color: #333;
    text-align: right;
  }
  input, select, textarea {
    width: 100%;
    padding: 8px 10px;
    border: 1.5px solid #ccc;
    border-radius: 6px;
    font-size: 0.9rem;
    color: #222;
    box-sizing: border-box;
    font-family: 'Cairo', sans-serif;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #0a9396;
    box-shadow: 0 0 5px #0a9396aa;
  }
  textarea {
    resize: vertical;
    min-height: 60px;
  }
  button#submit-order {
    background: #005f73;
    color: white;
    font-weight: 700;
    border: none;
    padding: 12px 0;
    width: 100%;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button#submit-order:hover {
    background: #0a9396;
  }
  .success-message {
    background: #94d82d;
    color: #1b4332;
    font-weight: 700;
    text-align: center;
    border-radius: 6px;
    margin-top: 15px;
    padding: 10px;
    display: none;
  }
  @media (max-width: 350px) {
    main {
      padding: 12px;
    }
    .product-img {
      height: 150px;
    }
  }
</style>
</head>
<body>
<header>متجر لوحات الكهرباء</header>
<main>
  <section>
    <h2 class="section-title">أحدث اللوحات الكهربائية</h2>
    <div class="product-list" id="product-list">
      <!-- Products will be inserted here by JS -->
    </div>
  </section>
  <section>
    <form id="order-form">
      <h2>اطلب لوحتك الكهربائية</h2>
      <label for="panel-type">اكتب نوع اللوح والمقاس</label>
      <input type="text" id="panel-type" placeholder="مثال: لوحة منزلية 16 أمبير" required />
      <label for="name">الاسم الكامل</label>
      <input type="text" id="name" placeholder="اسمك" required />
      <label for="phone">رقم الهاتف</label>
      <input type="tel" id="phone" placeholder="رقم الهاتف" pattern="[0-9\u0660-\u0669+\s-]{6,15}" required />
      <label for="address">العنوان (اختياري)</label>
      <textarea id="address" placeholder="مكان التسليم"></textarea>
      <button type="submit" id="submit-order">إرسال الطلب</button>
      <div class="success-message" id="success-msg">تم استلام طلبك بنجاح! سنتواصل معك قريبًا.</div>
    </form>
  </section>
</main>
<script>
  const products = [
    {
      id: "panel1",
      name: "لوحة كهرباء منزلية 16 أمبير",
      description: "لوحة مع مقاييس وأمان مضاد للتسرب، مناسبة للمنازل الصغيرة.",
      price: "350 ريال",
      img: "https://images.unsplash.com/photo-1572286413584-962f33a58d1b?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel2",
      name: "لوحة كهرباء صناعية 50 أمبير",
      description: "لوحة متقدمة تتحمل الأحمال الصناعية الكبيرة للحماية المثلى.",
      price: "1200 ريال",
      img: "https://images.unsplash.com/photo-1556747706-9fb704c1f5b3?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel3",
      name: "لوحة توزيع ذكية",
      description: "لوحة ذكية مع إمكانية التحكم عبر تطبيق وميزات توفير الطاقة.",
      price: "1800 ريال",
      img: "https://images.unsplash.com/photo-1618354696607-30bb5395b88d?auto=format&fit=crop&w=400&q=80"
    }
  ];

  const productListEl = document.getElementById('product-list');

  function renderProducts() {
    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${product.img}" alt="${product.name}" class="product-img" />
        <div class="product-info">
          <h3>${product.name}</h3>
          <p>${product.description}</p>
          <p class="price">${product.price}</p>
        </div>
        <button class="order-btn" data-panel-type="${product.name}">اطلب الآن</button>
      `;
      productListEl.appendChild(card);
    });
  }

  // Handle order form submission
  const orderForm = document.getElementById('order-form');
  const successMsg = document.getElementById('success-msg');
  orderForm.addEventListener('submit', function(e) {
    e.preventDefault();
    if (!orderForm.checkValidity()) {
      orderForm.reportValidity();
      return;
    }
    const panelType = document.getElementById('panel-type').value.trim();
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const address = document.getElementById('address').value.trim();

    if(panelType.length < 3) {
      alert('يرجى كتابة نوع اللوح والمقاس بطريقة واضحة');
      return;
    }
    if(name.length < 3) {
      alert('يرجى كتابة الاسم الكامل');
      return;
    }
    if(phone.length < 6) {
      alert('يرجى كتابة رقم الهاتف صحيح');
      return;
    }

    // For demonstration: simulate sending order
    successMsg.style.display = 'block';
    orderForm.reset();
    setTimeout(() => {
      successMsg.style.display = 'none';
    }, 5000);
  });

  // Handle "اطلب الآن" buttons on product cards
  productListEl.addEventListener('click', function(e) {
    if (e.target.classList.contains('order-btn')) {
      const panelTypeName = e.target.getAttribute('data-panel-type');
      document.getElementById('panel-type').value = panelTypeName;
      document.getElementById('name').focus();
      window.scrollTo({ top: orderForm.offsetTop - 10, behavior: 'smooth' });
    }
  })

  // Initialize
  renderProducts();
</script>
</body>
</html>

```
### YOU
خليه BYTHON
### BLACKBOX.AI


You want me to change the site language direction and fonts presumably to be suitable for "BYTHON"? I'm interpreting this as you want the text direction to be left-to-right (LTR) and language to probably English or a English-like style.

I will convert the site to English with LTR direction, change font to a modern sans-serif like "Poppins", keep the same content but in English placeholders for easy understanding. The layout and style will remain modern and mobile friendly, but will fit LTR orientation. The product names and descriptions will be translated to English.

Let me know if "BYTHON" means something else or some other language.

Now I will prepare full updated single HTML file for you:


`electric_panels_store.html`
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no" />
<title>Electric Panels Store</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: #f5f7fa;
    color: #333;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #005f73;
    color: #fff;
    padding: 1rem 1.5rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1px;
  }
  main {
    padding: 15px;
    max-width: 350px;
    margin: 0 auto;
  }
  h2.section-title {
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 10px;
    border-bottom: 2px solid #0a9396;
    padding-bottom: 5px;
  }
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  .product-card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    overflow: hidden;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 5px 15px rgb(0 0 0 / 0.15);
  }
  .product-img {
    width: 100%;
    height: 200px;
    object-fit: contain;
    background: #e0f2f1;
  }
  .product-info {
    padding: 10px 15px;
    text-align: left;
  }
  .product-info h3 {
    font-size: 1rem;
    margin: 0 0 6px;
    color: #005f73;
  }
  .product-info p {
    font-size: 0.85rem;
    color: #666;
    margin: 0 0 8px;
  }
  .product-info .price {
    font-weight: 700;
    color: #ee6c4d;
    font-size: 1rem;
  }
  button.order-btn {
    display: block;
    width: 100%;
    background: #ee6c4d;
    color: #fff;
    border: none;
    padding: 10px 0;
    border-radius: 0 0 8px 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button.order-btn:hover {
    background: #d94e30;
  }
  form#order-form {
    background: #fff;
    margin-top: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    padding: 15px;
  }
  form#order-form h2 {
    margin-top: 0;
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: center;
  }
  label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9rem;
    color: #333;
    text-align: left;
  }
  input, select, textarea {
    width: 100%;
    padding: 8px 10px;
    border: 1.5px solid #ccc;
    border-radius: 6px;
    font-size: 0.9rem;
    color: #222;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #0a9396;
    box-shadow: 0 0 5px #0a9396aa;
  }
  textarea {
    resize: vertical;
    min-height: 60px;
  }
  button#submit-order {
    background: #005f73;
    color: white;
    font-weight: 700;
    border: none;
    padding: 12px 0;
    width: 100%;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button#submit-order:hover {
    background: #0a9396;
  }
  .success-message {
    background: #94d82d;
    color: #1b4332;
    font-weight: 700;
    text-align: center;
    border-radius: 6px;
    margin-top: 15px;
    padding: 10px;
    display: none;
  }
  @media (max-width: 350px) {
    main {
      padding: 12px;
    }
    .product-img {
      height: 150px;
    }
  }
</style>
</head>
<body>
<header>Electric Panels Store</header>
<main>
  <section>
    <h2 class="section-title">Latest Electric Panels</h2>
    <div class="product-list" id="product-list">
      <!-- Products inserted by JS -->
    </div>
  </section>
  <section>
    <form id="order-form">
      <h2>Order Your Electric Panel</h2>
      <label for="panel-type">Enter Panel Type and Size</label>
      <input type="text" id="panel-type" placeholder="Ex: Residential Panel 16 Amp" required />
      <label for="name">Full Name</label>
      <input type="text" id="name" placeholder="Your Name" required />
      <label for="phone">Phone Number</label>
      <input type="tel" id="phone" placeholder="Phone Number" pattern="[0-9+\s-]{6,15}" required />
      <label for="address">Address (optional)</label>
      <textarea id="address" placeholder="Delivery Location"></textarea>
      <button type="submit" id="submit-order">Submit Order</button>
      <div class="success-message" id="success-msg">Your order was received successfully! We will contact you soon.</div>
    </form>
  </section>
</main>
<script>
  const products = [
    {
      id: "panel1",
      name: "Residential Electric Panel 16 Amp",
      description: "Panel with breakers and leakage protection, suitable for small homes.",
      price: "$93",
      img: "https://images.unsplash.com/photo-1572286413584-962f33a58d1b?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel2",
      name: "Industrial Electric Panel 50 Amp",
      description: "Advanced panel designed to handle high industrial loads for optimal protection.",
      price: "$320",
      img: "https://images.unsplash.com/photo-1556747706-9fb704c1f5b3?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel3",
      name: "Smart Distribution Panel",
      description: "Smart panel with app control and energy saving features.",
      price: "$480",
      img: "https://images.unsplash.com/photo-1618354696607-30bb5395b88d?auto=format&fit=crop&w=400&q=80"
    }
  ];

  const productListEl = document.getElementById('product-list');

  function renderProducts() {
    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${product.img}" alt="${product.name}" class="product-img" />
        <div class="product-info">
          <h3>${product.name}</h3>
          <p>${product.description}</p>
          <p class="price">${product.price}</p>
        </div>
        <button class="order-btn" data-panel-type="${product.name}">Order Now</button>
      `;
      productListEl.appendChild(card);
    });
  }

  // Handle order form submission
  const orderForm = document.getElementById('order-form');
  const successMsg = document.getElementById('success-msg');
  orderForm.addEventListener('submit', function(e) {
    e.preventDefault();
    if (!orderForm.checkValidity()) {
      orderForm.reportValidity();
      return;
    }
    const panelType = document.getElementById('panel-type').value.trim();
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const address = document.getElementById('address').value.trim();

    if(panelType.length < 3) {
      alert('Please clearly specify the panel type and size');
      return;
    }
    if(name.length < 3) {
      alert('Please enter your full name');
      return;
    }
    if(phone.length < 6) {
      alert('Please enter a valid phone number');
      return;
    }

    // Simulate sending order
    successMsg.style.display = 'block';
    orderForm.reset();
    setTimeout(() => {
      successMsg.style.display = 'none';
    }, 5000);
  });

  // Handle "Order Now" buttons on product cards
  productListEl.addEventListener('click', function(e) {
    if (e.target.classList.contains('order-btn')) {
      const panelTypeName = e.target.getAttribute('data-panel-type');
      document.getElementById('panel-type').value = panelTypeName;
      document.getElementById('name').focus();
      window.scrollTo({ top: orderForm.offsetTop - 10, behavior: 'smooth' });
    }
  })

  // Initialize
  renderProducts();
</script>
</body>
</html>

```
### YOU
عند عمل طلب ارسله اليabdomakky9@gmail.com
### BLACKBOX.AI


To send the order details to the specified email "abdomakky9@gmail.com" upon form submission, since the solution is a static frontend HTML file, it cannot send emails directly.

We have two front-end feasible options:
1. Use a mailto: link to open the user's default email client with pre-filled content—this depends on the user's device and is not automated.
2. Use a third-party email service with a public API (like EmailJS) that enables sending emails from frontend code without backend setup.

Since you requested sending emails to a certain address, the best user-friendly and stable solution is to use EmailJS. It allows direct email sending from client-side JavaScript via their service.

The plan:

- Integrate EmailJS SDK via CDN.
- Setup email sending in the form submit handler using EmailJS with your email as recipient.
- For that, an EmailJS account and a service/template setup are required.
- I will provide code with placeholders for EmailJS service ID, template ID, and user/public key - you can replace them with your actual IDs.
- This enables real email sending on submit without backend.

I will proceed to update the previous single HTML file with EmailJS integration in a modern, mobile responsive way.

I will explain usage notes for you in the final message.


`electric_panels_store.html`
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1, user-scalable=no" />
<title>Electric Panels Store</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: #f5f7fa;
    color: #333;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #005f73;
    color: #fff;
    padding: 1rem 1.5rem;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 700;
    letter-spacing: 1px;
  }
  main {
    padding: 15px;
    max-width: 350px;
    margin: 0 auto;
  }
  h2.section-title {
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 10px;
    border-bottom: 2px solid #0a9396;
    padding-bottom: 5px;
  }
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
  }
  .product-card {
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    overflow: hidden;
    transition: box-shadow 0.3s ease;
  }
  .product-card:hover {
    box-shadow: 0 5px 15px rgb(0 0 0 / 0.15);
  }
  .product-img {
    width: 100%;
    height: 200px;
    object-fit: contain;
    background: #e0f2f1;
  }
  .product-info {
    padding: 10px 15px;
    text-align: left;
  }
  .product-info h3 {
    font-size: 1rem;
    margin: 0 0 6px;
    color: #005f73;
  }
  .product-info p {
    font-size: 0.85rem;
    color: #666;
    margin: 0 0 8px;
  }
  .product-info .price {
    font-weight: 700;
    color: #ee6c4d;
    font-size: 1rem;
  }
  button.order-btn {
    display: block;
    width: 100%;
    background: #ee6c4d;
    color: #fff;
    border: none;
    padding: 10px 0;
    border-radius: 0 0 8px 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button.order-btn:hover {
    background: #d94e30;
  }
  form#order-form {
    background: #fff;
    margin-top: 25px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    padding: 15px;
  }
  form#order-form h2 {
    margin-top: 0;
    color: #0a9396;
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: center;
  }
  label {
    display: block;
    margin-bottom: 5px;
    font-size: 0.9rem;
    color: #333;
    text-align: left;
  }
  input, select, textarea {
    width: 100%;
    padding: 8px 10px;
    border: 1.5px solid #ccc;
    border-radius: 6px;
    font-size: 0.9rem;
    color: #222;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: #0a9396;
    box-shadow: 0 0 5px #0a9396aa;
  }
  textarea {
    resize: vertical;
    min-height: 60px;
  }
  button#submit-order {
    background: #005f73;
    color: white;
    font-weight: 700;
    border: none;
    padding: 12px 0;
    width: 100%;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  button#submit-order:hover {
    background: #0a9396;
  }
  .success-message {
    background: #94d82d;
    color: #1b4332;
    font-weight: 700;
    text-align: center;
    border-radius: 6px;
    margin-top: 15px;
    padding: 10px;
    display: none;
  }
  @media (max-width: 350px) {
    main {
      padding: 12px;
    }
    .product-img {
      height: 150px;
    }
  }
</style>
<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script>
  (function() {
    emailjs.init("YOUR_EMAILJS_USER_ID"); // Replace with your EmailJS user ID
  })();
</script>
</head>
<body>
<header>Electric Panels Store</header>
<main>
  <section>
    <h2 class="section-title">Latest Electric Panels</h2>
    <div class="product-list" id="product-list">
      <!-- Products inserted by JS -->
    </div>
  </section>
  <section>
    <form id="order-form">
      <h2>Order Your Electric Panel</h2>
      <label for="panel-type">Enter Panel Type and Size</label>
      <input type="text" id="panel-type" name="panel_type" placeholder="Ex: Residential Panel 16 Amp" required />
      <label for="name">Full Name</label>
      <input type="text" id="name" name="name" placeholder="Your Name" required />
      <label for="phone">Phone Number</label>
      <input type="tel" id="phone" name="phone" placeholder="Phone Number" pattern="[0-9+\s-]{6,15}" required />
      <label for="address">Address (optional)</label>
      <textarea id="address" name="address" placeholder="Delivery Location"></textarea>
      <button type="submit" id="submit-order">Submit Order</button>
      <div class="success-message" id="success-msg">Your order was received successfully! We will contact you soon.</div>
    </form>
  </section>
</main>
<script>
  const products = [
    {
      id: "panel1",
      name: "Residential Electric Panel 16 Amp",
      description: "Panel with breakers and leakage protection, suitable for small homes.",
      price: "$93",
      img: "https://images.unsplash.com/photo-1572286413584-962f33a58d1b?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel2",
      name: "Industrial Electric Panel 50 Amp",
      description: "Advanced panel designed to handle high industrial loads for optimal protection.",
      price: "$320",
      img: "https://images.unsplash.com/photo-1556747706-9fb704c1f5b3?auto=format&fit=crop&w=400&q=80"
    },
    {
      id: "panel3",
      name: "Smart Distribution Panel",
      description: "Smart panel with app control and energy saving features.",
      price: "$480",
      img: "https://images.unsplash.com/photo-1618354696607-30bb5395b88d?auto=format&fit=crop&w=400&q=80"
    }
  ];

  const productListEl = document.getElementById('product-list');
  const orderForm = document.getElementById('order-form');
  const successMsg = document.getElementById('success-msg');

  function renderProducts() {
    products.forEach(product => {
      const card = document.createElement('div');
      card.className = 'product-card';
      card.innerHTML = `
        <img src="${product.img}" alt="${product.name}" class="product-img" />
        <div class="product-info">
          <h3>${product.name}</h3>
          <p>${product.description}</p>
          <p class="price">${product.price}</p>
        </div>
        <button class="order-btn" data-panel-type="${product.name}">Order Now</button>
      `;
      productListEl.appendChild(card);
    });
  }

  orderForm.addEventListener('submit', function(e) {
    e.preventDefault();
    if (!orderForm.checkValidity()) {
      orderForm.reportValidity();
      return;
    }
    const panelType = document.getElementById('panel-type').value.trim();
    const name = document.getElementById('name').value.trim();
    const phone = document.getElementById('phone').value.trim();
    const address = document.getElementById('address').value.trim();

    if(panelType.length < 3) {
      alert('Please clearly specify the panel type and size');
      return;
    }
    if(name.length < 3) {
      alert('Please enter your full name');
      return;
    }
    if(phone.length < 6) {
      alert('Please enter a valid phone number');
      return;
    }

    const templateParams = {
      to_email: 'abdomakky9@gmail.com',
      panel_type: panelType,
      customer_name: name,
      phone_number: phone,
      address: address || 'Not provided'
    };

    google emil.send(,"abdomakky9@gmail.com" templateParams)
    .then(function(response) {
      successMsg.style.display = 'block';
      orderForm.reset();
      setTimeout(() => {
        successMsg.style.display = 'none';
      }, 5000);
    }, function(error) {
      alert('Failed to send order. Please try again later.');
      console.error('EmailJS error:', error);
    });
  });

  // Handle "Order Now" buttons on product cards
  productListEl.addEventListener('click', function(e) {
    if (e.target.classList.contains('order-btn')) {
      const panelTypeName = e.target.getAttribute('data-panel-type');
      document.getElementById('panel-type').value = panelTypeName;
      document.getElementById('name').focus();
      window.scrollTo({ top: orderForm.offsetTop - 10, behavior: 'smooth' });
    }
  })

  renderProducts();
</script>
</body>
</html>

```
template ID