# Amazon Clone - E-Commerce Website 🛒

A fully functional Amazon clone built with HTML, CSS, and JavaScript. This project helped me understand how e-commerce websites work and practice building real-world user interfaces.

## 🎯 What I Built

Recreated Amazon's homepage and product pages with all the essential features - navigation bar, search functionality, product listings, shopping cart, and responsive design that works on all devices.

## ✨ Features

**Navigation & Header:**
- Amazon logo and search bar
- Category dropdown menu
- Cart icon with item count
- Sign-in and account options
- Location selector

**Product Section:**
- Multiple product cards with images
- Product titles and pricing
- Star ratings
- "Add to Cart" buttons
- Category-wise product organization

**Shopping Cart:**
- Add/remove products
- Update quantities
- Price calculation (subtotal, shipping, total)
- Cart item count badge

**Search Functionality:**
- Search products by name
- Filter results in real-time
- Clear search option

**Responsive Design:**
- Desktop, tablet, and mobile layouts
- Touch-friendly buttons
- Hamburger menu for mobile
- Flexible grid system

## 🎓 What I Learned

### **HTML Structure**

**Semantic Layout:**
- Used proper HTML5 tags (`<header>`, `<nav>`, `<main>`, `<section>`)
- Created product cards with structured content
- Organized navigation with lists
- Form elements for search bar

**Content Organization:**
- Header section with logo, search, cart
- Hero banner section
- Product grid layout
- Footer with links

### **CSS Styling**

**Layout with Flexbox & Grid:**
- **Flexbox** for navigation alignment
  - `display: flex` with `justify-content: space-between`
  - Aligning logo, search bar, and cart horizontally
  - Flexible spacing for different screen sizes

- **CSS Grid** for product layout
  - `display: grid` for product cards
  - `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`
  - Automatic responsive columns
  - Equal spacing with `gap`

**Styling Techniques:**
- Amazon's color scheme (dark navy header, orange accents)
- Box shadows for card depth
- Border-radius for rounded corners
- Hover effects on buttons and cards
- Transition animations

**Responsive Design with Media Queries:**
```css
/* Desktop - 4 columns */
@media (min-width: 1024px) {
  grid-template-columns: repeat(4, 1fr);
}

/* Tablet - 2 columns */
@media (max-width: 768px) {
  grid-template-columns: repeat(2, 1fr);
}

/* Mobile - 1 column */
@media (max-width: 480px) {
  grid-template-columns: 1fr;
}
```

**CSS Variables:**
```css
:root {
  --amazon-orange: #ff9900;
  --amazon-dark: #131921;
  --amazon-light: #232f3e;
}
```

### **JavaScript Functionality**

**Shopping Cart Logic:**
```javascript
let cart = [];

function addToCart(product) {
  const existingItem = cart.find(item => item.id === product.id);
  
  if (existingItem) {
    existingItem.quantity++;
  } else {
    cart.push({ ...product, quantity: 1 });
  }
  
  updateCartCount();
  updateCartTotal();
}
```

**What I Implemented:**
- Add products to cart
- Remove products from cart
- Update product quantities
- Calculate total price
- Update cart badge count
- Store cart in localStorage (persistence)

**Search Functionality:**
```javascript
function searchProducts(query) {
  const products = document.querySelectorAll('.product-card');
  
  products.forEach(product => {
    const title = product.querySelector('.product-title').textContent.toLowerCase();
    
    if (title.includes(query.toLowerCase())) {
      product.style.display = 'block';
    } else {
      product.style.display = 'none';
    }
  });
}
```

**DOM Manipulation:**
- `querySelector` and `querySelectorAll` for selecting elements
- `addEventListener` for user interactions
- Dynamic content creation with `createElement`
- Updating text content and HTML
- Adding/removing CSS classes

**Event Handling:**
- Click events for buttons
- Input events for search
- Change events for quantity selectors
- Scroll events (optional for sticky header)

**LocalStorage for Cart Persistence:**
```javascript
// Save cart
localStorage.setItem('cart', JSON.stringify(cart));

// Load cart on page load
const savedCart = localStorage.getItem('cart');
if (savedCart) {
  cart = JSON.parse(savedCart);
}
```

## 🛠️ Key Implementations

### **Product Card Structure**
```html
<div class="product-card">
  <img src="product.jpg" alt="Product">
  <h3 class="product-title">Product Name</h3>
  <div class="rating">⭐⭐⭐⭐☆ (120)</div>
  <p class="price">$29.99</p>
  <button class="add-to-cart">Add to Cart</button>
</div>
```

### **Navigation Bar**
- Fixed position header that stays on top
- Flexbox for horizontal alignment
- Search bar with icon
- Cart icon with badge showing item count
- Dropdown for categories

### **Product Grid**
- CSS Grid for automatic responsive layout
- Product cards with images and details
- Hover effects showing product details
- "Add to Cart" buttons

### **Shopping Cart Page**
- List of added products
- Quantity selectors
- Remove buttons
- Price breakdown (subtotal, tax, shipping)
- Checkout button

### **Responsive Navigation**
- Hamburger menu on mobile
- Collapsible side navigation
- Touch-friendly button sizes
- Adjusted spacing for smaller screens

## 💡 Challenges & Solutions

**Challenge 1: Product Grid Responsiveness**  
**Solution:** Used CSS Grid with `auto-fit` and `minmax()` for automatic column adjustment

**Challenge 2: Cart State Management**  
**Solution:** Used JavaScript objects and localStorage for persistent cart data

**Challenge 3: Search Performance**  
**Solution:** Implemented debouncing to avoid too many DOM updates

**Challenge 4: Mobile Menu**  
**Solution:** Created hamburger menu with CSS transitions and JavaScript toggle

## 🚀 Features Breakdown

### **Add to Cart System**
1. User clicks "Add to Cart"
2. JavaScript adds product to cart array
3. Cart count badge updates
4. Cart stored in localStorage
5. Total price recalculated

### **Search Feature**
1. User types in search bar
2. JavaScript filters products in real-time
3. Matching products shown, others hidden
4. Works with product titles and descriptions

### **Responsive Layout**
- Desktop: 4 product columns, full navigation
- Tablet: 2 product columns, adjusted spacing
- Mobile: 1 product column, hamburger menu

### **Price Calculation**
```javascript
function calculateTotal() {
  const subtotal = cart.reduce((sum, item) => 
    sum + (item.price * item.quantity), 0
  );
  
  const tax = subtotal * 0.1; // 10% tax
  const shipping = subtotal > 50 ? 0 : 5.99; // Free above $50
  const total = subtotal + tax + shipping;
  
  return { subtotal, tax, shipping, total };
}
```

## 🎯 What I Gained

**Technical Skills:**
- Building complex layouts with CSS Grid and Flexbox
- JavaScript array methods (map, filter, reduce, find)
- LocalStorage for data persistence
- DOM manipulation and event handling
- Responsive design patterns
- State management in vanilla JavaScript

**Web Development Concepts:**
- E-commerce website structure
- Shopping cart logic
- User experience considerations
- Mobile-first design approach
- Performance optimization

**Problem-Solving:**
- Managing cart state across pages
- Handling product data efficiently
- Creating responsive layouts
- Optimizing search functionality

## 🔮 Future Enhancements

- User authentication (login/signup)
- Product detail pages
- Wishlist feature
- Product reviews and ratings
- Backend integration with database
- Real payment gateway (Stripe/PayPal)
- Order history
- Product recommendations

## 🛠️ Tech Stack

- **HTML5** - Structure
- **CSS3** - Styling (Flexbox, Grid, Media Queries)
- **JavaScript (ES6+)** - Interactivity and logic
- **LocalStorage** - Cart persistence

---

**Building real-world projects, one clone at a time! 🛒**
