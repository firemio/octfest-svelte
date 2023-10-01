<script lang="ts">
  import { createAccordion, melt } from '@melt-ui/svelte';
  import { slide } from 'svelte/transition';
 
  const {
    elements: { root, content, item, trigger },
    helpers: { isSelected },
  } = createAccordion({
    multiple: true,
  });
 
  const items = [
    {
      id: 'item-1',
      title: 'Is it accessible?',
      description: 'Yes. It adheres to the WAI-ARIA design pattern.',
    },
    {
      id: 'item-2',
      title: 'Is it unstyled?',
      description:
        "Yes. It's unstyled by default, giving you freedom over the look and feel.",
    },
    {
      id: 'item-3',
      title: 'Can it be animated?',
      description:
        'Yes! You can use the transition prop to configure the animation.',
    },
  ];


  const bugs = [
    {
      title: '復帰時の同期処理中をなくしたい',
      description: 'タブを切り替えて戻ると、復帰時の同期処理が起こり、プレイ体験が悪化する。特に大会中にDiscordを開いたり、WEBサイトのマップを確認した後に同期が発生し、操作性が悪い。',
    },
    {
      title: '【ドクロの悪戯】後戻り',
      description:
        "後戻りで他のプレイヤーに擦り付けた場合、座標が狂う。",
    },
    {
      title: '勝手にオートになる',
      description:
        'オートモードに移行していないのに、勝手に操作される。',
    },
    {
      title: '【クイーンの悪戯】破産',
      description:
        '借金になっても、物件が売られない事がある。',
    },
    {
      title: '各プレイヤー毎イベントの表示タイミング',
      description:
        '各プレイヤー毎に発生するイベント（都市独占でアイテムが貰えるイベントや、お金が増えるイベント）の表示するタイミングを「あなたのターンです」の後にして欲しい。',
    },
    {
      title: 'アイテムを使ったらキャンセルできない',
      description:
        'stealer, take over',
    },
    {
      title: '周遊アイテムが壊れた時に鳴るタイミング',
      description:
        'アイテムを壊すタイミングが違います。使ったときにアイテムが壊れるのではなく、マスに着いた時に壊れる。',
    },
    {
      title: 'スゴミの大きさが統一されていない',
      description:
        '順番ルーレットと決算で大きさが違う',
    },
    {
      title: '経路選択',
      description:
        'ドクロが憑かない経路があるのに選択されない。',
    },
    {
      title: '会員登録',
      description:
        'メール認証をスマホで行うと、PC側はリロードするかリンクを踏まなくてはいけない。',
    },
    {
      title: 'JS dialog',
      description:
        'JS dialogを表示していると、待ち時間が長くなる事がある。',
    },
    {
      title: '全体マップ',
      description:
        '車やヘリポートが点滅するので判別しにくい。',
    },
    {
      title: '冬の福の神',
      description:
        'イベント発生のタイミングがマイナスマスのメッセージ前に起きるので、わかりにくい。',
    },
  ];

</script>


<!-- Features Section -->
<section id="features" class="py-20">
  <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">参加方法</h2>
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


<hr class="h-px my-8 bg-gray-200 border-0 dark:bg-gray-700">

<!-- Features Section -->
<section id="features" class="py-20">
  <div class="root" use:melt={$root}>
    {#each items as { id, title, description }}
      <div use:melt={$item(id)} class="item">
        <h2>
          <button use:melt={$trigger(id)} class="trigger">
            {title}
          </button>
        </h2>
        {#if $isSelected(id)}
          <div class="content" use:melt={$content(id)} transition:slide>
            <div>{description}</div>
          </div>
        {/if}
      </div>
    {/each}
  </div>
</section>




<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-2xl px-4 md:px-8">
    <!-- text - start -->
    <div class="mb-10 md:mb-16">
      <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">既知のバグ(2023/10/01)</h2>

      <p class="mx-auto max-w-screen-md text-center text-gray-500 md:text-lg">要望やバグの報告をお願い致します。採用された方にはリワード報酬をプレゼント！</p>
    </div>
    <!-- text - end -->

    <div class="grid gap-4 sm:grid-cols-2 md:gap-8 xl:grid-cols-3">
      <!-- feature - start -->
      {#each bugs as { title, description }}
      <div class="flex divide-x rounded-lg border bg-gray-50">
        <div class="flex items-center p-2 text-indigo-500 md:p-4">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
          </svg>
        </div>

        <div class="p-4 md:p-6">
          <h3 class="mb-2 text-lg font-semibold md:text-xl">{title}</h3>
          <p class="text-gray-500">{description}</p>
        </div>
      </div>
      {/each}
      <!-- feature - end -->

    </div>
  </div>
</div>










<style>
  .root {
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    max-width: 28rem;
    border-radius: 0.375rem;
    box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1),
      0 4px 6px -4px rgb(0 0 0 / 0.1);
  }
 
  .item {
    margin-top: 1px;
    overflow: hidden;
    transition-property: color, background-color, border-color,
      text-decoration-color, fill, stroke, -webkit-text-decoration-color;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
  }
 
  .item:first-child {
    margin-top: 0px;
 
    border-radius: 0.25rem 0.25rem 0 0;
  }
 
  .item:last-child {
    border-radius: 0 0 0.25rem 0.25rem;
  }
 
  .item:focus-within {
    position: relative;
    z-index: 10;
 
    box-shadow: 0 0 0 3px rgb(var(--color-magnum-400) / 1);
  }
 
  .item > h2 {
    display: flex;
  }
 
  .trigger {
    display: flex;
    height: 3rem;
    flex: 1 1 0%;
    cursor: pointer;
    align-items: center;
    justify-content: space-between;
 
    background-color: rgb(var(--color-white) / 1);
 
    padding: 0 1.25rem;
 
    font-size: 1rem;
    font-weight: 500;
    line-height: 1;
 
    color: rgb(var(--color-magnum-700) / 1);
 
    box-shadow: none;
 
    transition-property: color, background-color, border-color,
      text-decoration-color, fill, stroke, -webkit-text-decoration-color;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
  }
 
  .trigger:hover {
    background-color: rgb(var(--color-white) / 0.95);
  }
 
  .content {
    overflow: hidden;
    background-color: rgb(var(--color-neutral-100) / 1);
    font-size: 0.875rem;
    line-height: 1.25rem;
    color: rgb(var(--color-neutral-900) / 1);
  }
 
  .content > div {
    padding: 1rem 1.25rem;
  }
</style>