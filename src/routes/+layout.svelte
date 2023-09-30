<script>
import "../app.css";
</script>

<!-- Header -->
<nav class="bg-amber-900 p-4 text-white">
    <div class="container mx-auto">
        <div class="flex justify-between">
            <div>
                <a href="#" class="text-xl font-bold">Dice or Dead βtest</a>
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
        <h1 class="text-4xl mb-6">アイテムのアイデアやバグを投稿しよう！</h1>
        <div class="flex justify-center ...">
            <div><img src="octfest-logo.webp"></div>
        </div>
        <div class="flex justify-center ...">
            <div><img src="reward20k.webp"></div>
        </div>
        <div class="flex justify-center ...">
            <div><img src="invitebonus.webp"></div>
        </div>
          
        <p class="mb-6">2023/10/01 12:00(UTC) ～ before PreSale</p>
        <a href="#cta" class="bg-red-600 text-white py-2 px-6 rounded">Play Free Game</a>
    </div>
</section>

<!-- Features Section -->
<section id="features" class="py-20">
    <p class="flex justify-center text-xl mb-5">今回のβテストではウォレット作成の手順が省かれています。</p>
    <div class="container mx-auto grid md:grid-cols-3 gap-12">
        <div class="bg-blue-600 rounded pt-2">
            <h2 class="text-xl mb-4 flex justify-center text-white">Step 1</h2>
            <p class="mb-4 flex justify-center text-white">会員登録する</p>
            <p class="mb-4 flex justify-center text-white"><a href="https://beta-diceordead.six502.com/" target="game">https://beta-diceordead.six502.com/</a></p>
        </div>
        <div class="bg-blue-600 rounded pt-2">
            <h2 class="text-xl mb-4 flex justify-center text-white">Step 2</h2>
            <p class="mb-4 flex justify-center text-white">メールとSMSを認証する</p>
        </div>
        <div class="bg-blue-600 rounded pt-2">
            <h2 class="text-xl mb-4 flex justify-center text-white">Step 3</h2>
            <p class="mb-4 flex justify-center text-white">マルチプレイでゲームに参加！</p>
        </div>
    </div>
    <p class="flex justify-center text-xl mt-5">詳しい手順はこちら</p>
    <p class="flex justify-center text-xl"><a class="font-medium text-blue-600 underline dark:text-blue-500 hover:no-underline" href="https://six502.medium.com/how-to-participate-in-the-opne-beta-77caef8b82f6" target="medium">https://six502.medium.com/how-to-participate-in-the-opne-beta-77caef8b82f6</a></p>
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

