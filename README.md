# Ex.07 Restaurant Website
## Date:30.09.2025

## AIM:
To develop a static Restaurant website to display the food items and services provided by them.

## DESIGN STEPS:

### Step 1:
Requirement collection.

### Step 2:
Creating the layout using HTML and CSS.

### Step 3:
Updating the sample content.

### Step 4:
Choose the appropriate style and color scheme.

### Step 5:
Validate the layout in various browsers.

### Step 6:
Validate the HTML code.

### Step 7:
Publish the website in the given URL.

## PROGRAM:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Honey Restaurant - Fine Dining</title>
    <style>
        /* --- General Styles & Color Scheme --- */
        /* * Color Scheme based on sample:
         * Background: #F8F8F8 (Off-white)
         * Main Text/Headers: #333333 (Dark Gray)
         * Navigation Background: #333333 (Dark Gray)
         * Card Background: #FFF9F0 (Light Beige/Cream)
         * Accent/Link: #4A90E2 (Blue for links in sample)
        */
        :root {
            --bg-color: #F8F8F8;
            --text-color: #333333;
            --nav-bg: #333333;
            --card-bg: #FFF9F0;
            --footer-text-color: #4A90E2;
        }

        body {
            font-family: 'Helvetica', 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
        }

        /* --- Header & Navigation --- */
        .header {
            background-color: #FFFFFF;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            border-bottom: 1px solid #ddd;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .logo-container svg {
            width: 50px;
            height: 50px;
        }

        .header h1 {
            margin: 0;
            color: var(--text-color);
            font-size: 2.5rem;
            font-weight: 300;
            letter-spacing: 2px;
        }
        
        .main-nav {
            background-color: var(--nav-bg);
            width: 100%;
            margin-top: 1.5rem;
        }

        .nav {
            list-style-type: none;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
        }

        .nav li {
            margin: 0;
        }

        .nav a {
            text-decoration: none;
            color: #FFFFFF;
            font-weight: bold;
            font-size: 1.1rem;
            padding: 1rem 2rem;
            display: block;
            transition: background-color 0.3s;
        }

        .nav a:hover, .nav a.active {
            background-color: #555555;
        }
        
        /* --- Page Container --- */
        main {
            padding: 2rem;
        }

        .page {
            display: none;
            animation: fadeIn 0.5s ease-in-out;
        }
        
        .page.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- Home Page Specific Styles --- */
        #home .promo-banner {
            background-image: url('https://images.unsplash.com/photo-1504674900247-0877df9cc836?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80');
            background-size: cover;
            background-position: center;
            padding: 3rem 2rem;
            border-radius: 8px;
            color: white;
            margin-bottom: 3rem;
            text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.6);
        }

        #home .promo-banner h2 {
            font-size: 2.5rem;
            margin-top: 0;
            margin-bottom: 1rem;
        }
        
        #home .promo-banner p {
            max-width: 600px;
            font-size: 1.1rem;
        }

        .home-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .home-card {
            background-color: var(--card-bg);
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .home-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 4px;
            margin-bottom: 1rem;
        }
        
        .home-card h3 {
            font-size: 1.5rem;
            margin-top: 0;
            margin-bottom: 1rem;
        }
        
        .home-card .info-link {
            display: inline-block;
            margin-top: 1rem;
            font-weight: bold;
            text-decoration: none;
            color: var(--footer-text-color);
        }
        
        .home-card .hours {
            list-style: none;
            padding: 0;
            margin-top: 1rem;
        }
        .home-card .hours li {
            margin-bottom: 0.5rem;
        }

        /* --- Menu Page Specific Styles --- */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .menu-item {
            background-color: #FFFFFF;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .menu-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }

        .menu-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .menu-item-content {
            padding: 1.5rem;
        }
        
        .menu-item-content h3 {
            margin-top: 0;
            color: #D2691E; /* Keeping some old accent color for menu variety */
        }
        
        .menu-item-content .price {
            display: block;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 1rem;
        }

        /* --- Administration Page Specific Styles --- */
        .admin-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            text-align: center;
        }
        
        .admin-member {
            background: #FFFFFF;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }
        
        .admin-member:hover {
             transform: scale(1.05);
        }
        
        .admin-member img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid #D2691E;
        }
        
        .admin-member h3 {
             margin: 1rem 0 0.5rem 0;
        }
        
        .admin-member p {
            font-style: italic;
            color: #555;
            margin: 0;
        }

        /* --- Contact Page Specific Styles --- */
        .contact-container {
            max-width: 800px;
            margin: 2rem auto;
            padding: 2rem;
            background: #FFFFFF;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .contact-container h2 {
            text-align: center;
            margin-bottom: 2rem;
        }
        
        .contact-info p {
            font-size: 1.1rem;
            margin: 1rem 0;
            display: flex;
            align-items: center;
        }

        .contact-info p strong {
            display: inline-block;
            width: 80px;
        }

        /* --- Footer --- */
        .footer {
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
            font-size: 0.9rem;
        }
        
        .footer p {
            margin: 0;
            color: var(--footer-text-color);
        }

        /* --- Responsive Design --- */
        @media (max-width: 768px) {
            .header {
                padding: 1rem;
            }
            .nav a {
                padding: 1rem;
                font-size: 1rem;
            }
            #home .promo-banner h2 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>

    <header class="header">
        <div class="logo-container">
            <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                <path d="M50,10 C70,10 90,30 90,50 C90,70 70,90 50,90 C30,90 10,70 10,50 C10,30 30,10 50,10 Z" fill="#5F6F52"/>
                <path d="M50,10 C50,10 60,0 70,10 C75,15 70,20 65,20 C60,20 55,15 50,10 Z" fill="#5F6F52"/>
            </svg>
            <h1>HONEY RESTAURANT</h1>
        </div>
        <nav class="main-nav">
            <ul class="nav">
                <li><a href="#home" class="nav-link active">Home</a></li>
                <li><a href="#menu" class="nav-link">Menu</a></li>
                <li><a href="#administration" class="nav-link">Administration</a></li>
                <li><a href="#contact" class="nav-link">Contact Us</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <!-- Home Page -->
        <section id="home" class="page active">
            <div class="promo-banner">
                <h2>30% Off This Weekend</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse et congue massa, eu fringilla mauris. Fusce dapibus vehicula ex at ultrices. Duis at varius ligula.</p>
            </div>
            <div class="home-grid">
                <div class="home-card">
                    <h3>Our New Menu</h3>
                    <img src="https://images.unsplash.com/photo-1598515213692-5f282348df1d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="New Menu">
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse et congue massa, eu fringilla mauris. Fusce dapibus vehicula ex at ultrices.</p>
                    <a href="#" class="info-link">See our new menu</a>
                </div>
                <div class="home-card">
                    <h3>Book a table</h3>
                    <img src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80" alt="Book a table">
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse et congue massa, eu fringilla mauris. Fusce dapibus vehicula ex at ultrices.</p>
                    <a href="#" class="info-link">Book your table now</a>
                </div>
                <div class="home-card">
                    <h3>Opening Hours</h3>
                    <img src="https://images.unsplash.com/photo-1556911220-bff31c812dba?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=953&q=80" alt="Opening Hours">
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse et congue massa, eu fringilla mauris.</p>
                    <ul class="hours">
                        <li>Mon - Fri: 2pm - 10pm</li>
                        <li>Sat: 2pm - 11pm</li>
                        <li>Sun: 2pm - 9pm</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Menu Page -->
        <section id="menu" class="page">
             <div class="menu-grid">
                <!-- Item 1 -->
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1572441713132-c542fc4fe282?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=880&q=80" alt="Bruschetta">
                    <div class="menu-item-content">
                        <h3>Classic Bruschetta</h3>
                        <p>Grilled bread topped with fresh tomatoes, garlic, basil, and a hint of balsamic glaze.</p>
                        <span class="price">$12.00</span>
                    </div>
                </div>
                <!-- ... other menu items ... -->
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1519708227418-c8fd9a32b7a2?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Salmon">
                    <div class="menu-item-content">
                        <h3>Pan-Seared Salmon</h3>
                        <p>Crispy-skin salmon served with asparagus and a lemon-dill sauce.</p>
                        <span class="price">$26.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1628840042765-356cda07504e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=580&q=80" alt="Steak">
                    <div class="menu-item-content">
                        <h3>Ribeye Steak</h3>
                        <p>12oz Ribeye cooked to perfection, served with garlic mashed potatoes.</p>
                        <span class="price">$35.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1595908129742-08575a643e06?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Pasta">
                    <div class="menu-item-content">
                        <h3>Mushroom Risotto</h3>
                        <p>Creamy Arborio rice with wild mushrooms, parmesan, and truffle oil.</p>
                        <span class="price">$22.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1550304943-4f24f54ddde9?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Caesar Salad">
                    <div class="menu-item-content">
                        <h3>Gourmet Caesar Salad</h3>
                        <p>Crisp romaine, homemade croutons, parmesan cheese, and our signature Caesar dressing.</p>
                        <span class="price">$14.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1606041934244-043b1c1d3a4b?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Chicken">
                    <div class="menu-item-content">
                        <h3>Roasted Herb Chicken</h3>
                        <p>Half a chicken roasted with herbs, served with seasonal root vegetables.</p>
                        <span class="price">$24.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1619895092473-b5a02e4f0122?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Lasagna">
                    <div class="menu-item-content">
                        <h3>Beef Lasagna</h3>
                        <p>Layers of pasta, rich bolognese sauce, béchamel, and melted mozzarella.</p>
                        <span class="price">$20.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1571680322279-a226e6a4b493?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Tiramisu">
                    <div class="menu-item-content">
                        <h3>Classic Tiramisu</h3>
                        <p>Coffee-soaked ladyfingers layered with mascarpone cream and dusted with cocoa powder.</p>
                        <span class="price">$10.00</span>
                    </div>
                </div>
                 <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1626202454936-76a0a8f79133?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Scallops">
                    <div class="menu-item-content">
                        <h3>Seared Scallops</h3>
                        <p>Jumbo scallops seared golden, served on a bed of corn purée.</p>
                        <span class="price">$28.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=699&q=80" alt="Burger">
                    <div class="menu-item-content">
                        <h3>The Grove Burger</h3>
                        <p>Wagyu beef patty, cheddar cheese, caramelized onions, and secret sauce on a brioche bun.</p>
                        <span class="price">$19.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1625944026252-9a5c2f01f0c5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80" alt="Soup">
                    <div class="menu-item-content">
                        <h3>Lobster Bisque</h3>
                        <p>A rich and creamy soup with chunks of fresh lobster meat.</p>
                        <span class="price">$16.00</span>
                    </div>
                </div>
                <div class="menu-item">
                    <img src="https://images.unsplash.com/photo-1542826438-c32144d6b5e0?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=580&q=80" alt="Cheesecake">
                    <div class="menu-item-content">
                        <h3>New York Cheesecake</h3>
                        <p>A classic creamy cheesecake with a graham cracker crust and a strawberry coulis.</p>
                        <span class="price">$11.00</span>
                    </div>
                </div>
             </div>
        </section>

        <!-- Administration Page -->
        <section id="administration" class="page">
            <div class="admin-grid">
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80" alt="CEO">
                    <h3>Olivia Chen</h3>
                    <p>Founder & CEO</p>
                </div>
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1577219491135-ce391730fb2c?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80" alt="Executive Chef">
                    <h3>Marco Bianchi</h3>
                    <p>Executive Chef</p>
                </div>
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80" alt="General Manager">
                    <h3>Samuel Jones</h3>
                    <p>General Manager</p>
                </div>
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1581382575275-97901c2635b7?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80" alt="Sous Chef">
                    <h3>Isabella Rossi</h3>
                    <p>Sous Chef</p>
                </div>
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80" alt="HR Manager">
                    <h3>David Lee</h3>
                    <p>HR & Operations</p>
                </div>
                <div class="admin-member">
                    <img src="https://images.unsplash.com/photo-1580489944761-15a19d654956?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=461&q=80" alt="Events Coordinator">
                    <h3>Aisha Khan</h3>
                    <p>Events Coordinator</p>
                </div>
            </div>
        </section>

        <!-- Contact Us Page -->
        <section id="contact" class="page">
            <div class="contact-container">
                <h2>Get In Touch</h2>
                <div class="contact-info">
                    <p><strong>Address:</strong> 123 Culinary Lane, Foodie City, FS 45678</p>
                    <p><strong>Phone:</strong> (555) 123-4567</p>
                    <p><strong>E-mail:</strong> contact@littlelemon.com</p>
                    <p><strong>Hours:</strong> Tue-Sun, 5:00 PM - 11:00 PM</p>
                </div>
            </div>
        </section>
    </main>

    <footer class="footer">
        <p>Designed and Developed by Aniruth S</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const navLinks = document.querySelectorAll('.nav-link');
            const pages = document.querySelectorAll('.page');

            function showPage(pageId) {
                pages.forEach(page => {
                    page.classList.remove('active');
                });
                const newPage = document.getElementById(pageId);
                if (newPage) {
                    newPage.classList.add('active');
                }
            }

            navLinks.forEach(link => {
                link.addEventListener('click', function(event) {
                    event.preventDefault();
                    
                    navLinks.forEach(nav => nav.classList.remove('active'));
                    this.classList.add('active');
                    
                    const pageId = this.getAttribute('href').substring(1);
                    showPage(pageId);
                });
            });

            const initialPageId = window.location.hash ? window.location.hash.substring(1) : 'home';
            showPage(initialPageId);
            
            const activeLink = document.querySelector(`.nav-link[href="#${initialPageId}"]`);
            if (activeLink) {
                 navLinks.forEach(nav => nav.classList.remove('active'));
                 activeLink.classList.add('active');
            }
        });
    </script>

</body>
</html>





```
## OUTPUT:
![alt text](<Screenshot (36).png>)
![alt text](<Screenshot (37).png>)

## RESULT:
The program for designing software company website using HTML and CSS is completed successfully.
