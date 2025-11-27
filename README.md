            <!-- Instructions for the customer -->
            <p class="text-sm text-gray-600 font-medium">Click "Order Now" for instant WhatsApp chat.</p>
        </div># GiftsKenya
### Simple E-commerce Page

This is a single-page product listing website for GiftsKenya, using HTML, Tailwind CSS, and JavaScript.

**Features:**
* Display of current products, descriptions, and prices.
* "Order Now" buttons link directly to WhatsApp chat with a pre-filled message for instant ordering.

**Live Site:** https://giftskenya.github.io/GiftsKenya/
    </header>

    <!-- Product Listing Section: Main Content -->
    <section id="products" class="py-12 sm:py-16">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h3 class="text-3xl font-bold text-gray-900 mb-10 text-center">Available Items</h3>
            
            <!-- Grid where products will be injected by JavaScript -->
            <div id="product-list" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Products will be dynamically inserted here -->
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8 mt-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <p>&copy; <span id="year"></span> GiftsKenya. All rights reserved.</p>
            <p class="text-sm mt-2">To add new items, edit the JavaScript array at the bottom of this file.</p>
        </div>
    </footer>

    <!-- JavaScript for Product Rendering and Logic -->
    <script>
        // --- 1. CONFIGURATION (REQUIRED) ---
        // This is your WhatsApp number (0700678179) converted to international format (254700678179)
        const whatsappNumber = "254700678179"; 

        // --- 2. PRODUCT DATA (EDIT THIS ARRAY TO ADD/REMOVE ITEMS) ---
        const products = [
            {
                id: 1,
                name: "Handmade Leather Journal",
                description: "A beautifully crafted leather journal, perfect for daily notes or travel memories.",
                price: "KES 2,500",
                image: "https://placehold.co/400x300/6366f1/ffffff?text=Leather+Journal",
                // This is the message the customer will send to you
                whatsapp_message: "Hello, I am interested in ordering the Handmade Leather Journal (KES 2,500).",
            },
            {
                id: 2,
                name: "Maasai Beaded Bracelet Set",
                description: "Vibrant set of three beaded bracelets inspired by traditional Maasai designs. Adjustable size.",
                price: "KES 1,200",
                image: "https://placehold.co/400x300/f59e0b/ffffff?text=Beaded+Bracelet+Set",
                whatsapp_message: "Hello, I am interested in ordering the Maasai Beaded Bracelet Set (KES 1,200).",
            },
            {
                id: 3,
                name: "Kenyan Coffee Blend (250g)",
                description: "Premium medium-roast blend from Central Kenya. Notes of citrus and chocolate.",
                price: "KES 850",
                image: "https://placehold.co/400x300/10b981/ffffff?text=Kenyan+Coffee+Blend",
                whatsapp_message: "Hello, I am interested in ordering the Kenyan Coffee Blend (KES 850).",
            },
             {
                id: 4,
                name: "Wooden Carved Elephant",
                description: "Small, intricately carved wooden elephant figurine, ideal for office or home decor.",
                price: "KES 1,800",
                image: "https://placehold.co/400x300/ef4444/ffffff?text=Carved+Elephant",
                whatsapp_message: "Hello, I am interested in ordering the Wooden Carved Elephant (KES 1,800).",
            },
        ];

        // --- 3. RENDERING LOGIC ---
        const productList = document.getElementById('product-list');

        /**
         * Generates the HTML card for a single product.
         * @param {object} product - The product data object.
         */
        function createProductCard(product) {
            // Encode the message and create the direct WhatsApp link
            const encodedMessage = encodeURIComponent(product.whatsapp_message);
            const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;

            return `
                <div class="bg-white rounded-xl shadow-lg hover:shadow-xl transition duration-300 overflow-hidden transform hover:scale-[1.02]">
                    <!-- Product Image -->
                    <img src="${product.image}" alt="${product.name}" 
                         class="w-full h-48 object-cover object-center"
                         onerror="this.onerror=null;this.src='https://placehold.co/400x300/cccccc/333333?text=Image+Unavailable';"
                    >
                    
                    <div class="p-6">
                        <!-- Product Name -->
                        <h4 class="text-xl font-bold text-gray-900 mb-2">${product.name}</h4>
                        
                        <!-- Product Description -->
                        <p class="text-gray-600 text-sm mb-4 h-12 overflow-hidden">${product.description}</p>
                        
                        <!-- Price -->
                        <div class="text-2xl font-extrabold text-indigo-600 mb-4">${product.price}</div>
                        
                        <!-- Order Button: Links directly to WhatsApp chat -->
                        <a href="${whatsappLink}" target="_blank"
                            class="block w-full text-center py-3 bg-green-500 text-white font-semibold rounded-lg shadow-md hover:bg-green-600 transition duration-300"
                        >
                            Order Now (via WhatsApp)
                        </a>
                    </div>
                </div>
            `;
        }

        /**
         * Renders all products to the page.
         */
        function renderProducts() {
            if (productList) {
                productList.innerHTML = products.map(createProductCard).join('');
            }
        }
        
        // --- 4. INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => {
            renderProducts();
            // Set current year in footer
            document.getElementById('year').textContent = new Date().getFullYear();
        });
    </script>

</body>
</html>
