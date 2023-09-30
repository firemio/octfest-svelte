<script>
import "../app.css";
</script>

<!-- Header -->
<nav class="bg-amber-900 p-4 text-white">
    <div class="container mx-auto">
        <div class="flex justify-between">
            <div>
                <a href="#" class="text-xl font-bold">Dice or Dead</a>
            </div>
            <div>
                <a href="#features" class="mr-4">Features</a>
                <a href="#testimonials">Testimonials</a>
            </div>
        </div>
    </div>
</nav>

<!-- Hero Section -->
<section class="bg-amber-600 text-white text-center py-20">
    <div class="container mx-auto">
        <h1 class="text-4xl mb-6"></h1>
        <div class="flex justify-center ...">
            <div><img src="octfest-logo.webp"></div>
        </div>
          
        <p class="mb-6">Some catchy tagline or introduction here.</p>
        <a href="#cta" class="bg-red-600 text-white py-2 px-6 rounded">Get Started</a>
    </div>
</section>

<!-- Features Section -->
<section id="features" class="py-20">
    <div class="container mx-auto grid md:grid-cols-3 gap-12">
        <div>
            <h2 class="text-xl mb-4">Feature 1</h2>
            <p>Description about this feature.</p>
        </div>
        <div>
            <h2 class="text-xl mb-4">Feature 2</h2>
            <p>Description about this feature.</p>
        </div>
        <div>
            <h2 class="text-xl mb-4">Feature 3</h2>
            <p>Description about this feature.</p>
        </div>
    </div>
</section>

<slot />

<!-- Testimonials Section -->
<section id="testimonials" class="bg-gray-100 py-20">
    <div class="container mx-auto">
        <h2 class="text-2xl mb-8">What our users say:</h2>
        <!-- Example testimonial; you can add more -->
        <div class="p-4 bg-white shadow rounded">
            <p>"This product is amazing!"</p>
            <p>- Happy Customer</p>
        </div>
    </div>
</section>

<!-- Footer -->
<footer class="bg-amber-900 text-white p-4">
    <div class="container mx-auto text-center">
        <p>&copy; 2023 six502.com</p>
    </div>
</footer>

