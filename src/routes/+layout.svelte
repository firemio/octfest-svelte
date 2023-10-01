<script lang="ts">
import "../app.css";

import { t, locale, locales } from "../i18n";
	// Create a locale specific timestamp
  $: time = new Date().toLocaleDateString($locale, {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
  });

</script>

<!-- Header -->
<nav class="bg-amber-900 p-4 text-white">
    <div class="container mx-auto">
        <div class="flex justify-between">
            <div>
                <a href="#" class="text-xl font-bold">Dice or Dead βtest</a>
            </div>
            <div>
                <span class="text-black">
                    <select bind:value={$locale}>
                      {#each locales as l}
                        <option value={l}>{l}</option>
                      {/each}
                    </select>
                </span>
                <a href="https://dod-event-openbeta.six502.com/celebration.html" class="mr-4">Old Event Page</a>
                
            </div>
        </div>
    </div>
</nav>
<!-- Hero Section -->
<section class="bg-amber-600 text-white text-center py-20">
    <div class="container mx-auto">
        <h1 class="text-4xl mb-6">{@html $t("homepage.catchcopy")}</h1>
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
        <a href="https://beta-diceordead.six502.com/" target="game_dod" class="bg-red-600 text-white py-2 px-6 rounded">{@html $t("homepage.btn1")}</a>
    </div>
</section>


<slot />


<!-- Footer -->
<footer class="bg-amber-900 text-white p-4">
    <div class="container mx-auto text-center">
        <p>&copy; 2023 six502.com</p>
    </div>
</footer>

