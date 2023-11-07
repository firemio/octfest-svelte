<script lang="ts">
  import { createAccordion, melt } from '@melt-ui/svelte';
  import { slide } from 'svelte/transition';
 
  import { t, locale, locales } from "../i18n";
	// Create a locale specific timestamp
  $: time = new Date().toLocaleDateString($locale, {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
  });

  const {
    elements: { root, content, item, trigger },
    helpers: { isSelected },
  } = createAccordion({
    multiple: true,
  });

  const items = [
    {
      id: 'item-1',
      title: 'リワードはどうやって貰えますか？',
      description: 'アイデアやバグの報告が採用されると貰えます。',
    },
    {
      id: 'item-2',
      title: 'リワードはいつ貰えますか？',
      description:
        '上場した後に配布されます。',
    },
    {
      id: 'item-3',
      title: '紹介者ボーナスとは？',
      description:
        "ゲーム内のプロフィールページに紹介リンクがあります。紹介リンクから入ったユーザーの数に応じてトークンが貰えます。",
    },
    {
      id: 'item-4',
      title: '紹介者ボーナスはいつ貰えますか？',
      description:
        '上場時にエアドロップされます。',
    },
  ];
  const items_ja = [
    {
      id: 'item-1',
      title: 'asdasd',
      description: 'ertert',
    },
    {
      id: 'item-2',
      title: 'リワードはいつ貰えますか？',
      description:
        '上場した後に配布されます。',
    },
    {
      id: 'item-3',
      title: '紹介者ボーナスとは？',
      description:
        "ゲーム内のプロフィールページに紹介リンクがあります。紹介リンクから入ったユーザーの数に応じてトークンが貰えます。",
    },
    {
      id: 'item-4',
      title: '紹介者ボーナスはいつ貰えますか？',
      description:
        '上場時にエアドロップされます。',
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


  const bugs_en = [
    {
      title: 'I want to eliminate the synchronization process on return.',
      description: 'Switching back and forth between tabs causes a synchronization process when returning, which worsens the playing experience. Synchronization occurs especially after opening Discord or checking the map on the website during a tournament, which is not easy to operate.',
    },
    {
      title: "[Skull's pranks] Backtracking.",
      description:
        "If you backtrack and rub against another player, the coordinates will be off.",
    },
    {
      title: 'It goes into auto on its own.',
      description:
        'It operates on its own even though it is not shifted to auto mode.',
    },
    {
      title: "[Queen's prank] Bankruptcy",
      description:
        'Sometimes properties are not sold when they are in debt.',
    },
    {
      title: 'Display timing of events for each player',
      description:
        "I would like the timing of the events that occur for each player (events that give items for city monopoly or more money) to be displayed after It's your turn.",
    },
    {
      title: 'Once an item is used, it cannot be canceled.',
      description:
        'stealer, take over',
    },
    {
      title: 'When to ring when a lapsed item is broken.',
      description:
        'The timing of breaking items is different. Instead of the item breaking when you use it, it breaks when you reach the square.',
    },
    {
      title: 'The size of the sugomi is not standardized.',
      description:
        'Different size in order roulette and financial statement.',
    },
    {
      title: 'routing',
      description:
        'There are pathways that are not possessed by skulls, but they are not selected.',
    },
    {
      title: 'Member Registration',
      description:
        'If the email authentication is done on a smartphone, the PC side has to reload or step on the link.',
    },
    {
      title: 'JS dialog',
      description:
        'When displaying JS dialog, the waiting time can be long.',
    },
    {
      title: 'Overall Map',
      description:
        'Cars and heliports are difficult to identify because of the flashing lights.',
    },
    {
      title: 'god of fortune in winter',
      description:
        'The timing of the event is difficult to understand because it occurs before the minus square message.',
    },
  ];



</script>


<!-- Features Section -->
<section id="features" class="py-20">
  <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">{@html $t("sect1.msg1")}</h2>
  
  <p class="flex justify-center text-xl mb-5">{@html $t("sect1.msg2")}</p>
  <div class="container mx-auto grid md:grid-cols-3 gap-12">
      <div class="bg-blue-600 rounded pt-2 m-3">
          <h2 class="text-xl mb-4 flex justify-center text-white">Step 1</h2>
          <p class="mb-4 flex justify-center text-white">{@html $t("sect1.box1")}</p>
          <p class="mb-4 flex justify-center text-white"><a href="https://beta-diceordead.six502.com/" target="game">https://beta-diceordead.six502.com/</a></p>
      </div>
      <div class="bg-blue-600 rounded pt-2 m-3">
          <h2 class="text-xl mb-4 flex justify-center text-white">Step 2</h2>
          <p class="mb-4 flex justify-center text-white">{@html $t("sect1.box2")}</p>
      </div>
      <div class="bg-blue-600 rounded pt-2 m-3">
          <h2 class="text-xl mb-4 flex justify-center text-white">Step 3</h2>
          <p class="mb-4 flex justify-center text-white">{@html $t("sect1.box3")}</p>
      </div>
  </div>
  <p class="flex justify-center text-xl mt-5">{@html $t("sect1.msg3")}</p>
  <p class="flex justify-center text-xl"><a class="font-medium text-blue-600 underline dark:text-blue-500 hover:no-underline" href="https://six502.medium.com/how-to-participate-in-the-opne-beta-77caef8b82f6" target="medium">https://six502.medium.com/how-to-participate-in-the-opne-beta-77caef8b82f6</a></p>
</section>


<hr class="h-px my-8 bg-gray-200 border-0 dark:bg-gray-300">

<!-- Reward Section -->
<section id="features" class="py-20 flex flex-col items-center">
    <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">{@html $t("reward.title")}</h2>    
    <p class="flex justify-center text-xl mb-5">{@html $t("reward.msg1")}</p>
<!--    <a href="#" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Read more</a>  -->
    
    <a href="https://forms.gle/v4pftv5pUiwYjxwp7" target="_blank" class="inline-flex items-center justify-center p-5 text-base font-medium text-white-100 rounded-lg bg-green-500 hover:text-white-900 hover:bg-green-300 text-white-400 dark:bg-green-500 dark:hover:bg-green-700 dark:hover:text-white">
      <span class="w-full">{@html $t("reward.btn1")}</span>
      <svg class="w-4 h-4 ml-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
          <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
      </svg>
    </a> 

  
  <!---
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
-->

<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-2xl px-4 md:px-8">

    <div class="grid gap-8 sm:grid-cols-2 sm:gap-y-10 xl:grid-cols-3">
      <!-- question - start -->
      <div class="relative rounded-lg bg-gray-100 p-5 pt-8">
        <span class="absolute -top-4 left-4 inline-flex h-8 w-8 items-center justify-center rounded-full bg-indigo-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
          </svg>
        </span>

        <h3 class="mb-3 text-lg font-semibold text-indigo-500 md:text-xl">{@html $t("faq.q1")}</h3>
        <p class="text-gray-500">{@html $t("faq.a1")}</p>
      </div>
      <!-- question - end -->

      <!-- question - start -->
      <div class="relative rounded-lg bg-gray-100 p-5 pt-8">
        <span class="absolute -top-4 left-4 inline-flex h-8 w-8 items-center justify-center rounded-full bg-indigo-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
          </svg>
        </span>

        <h3 class="mb-3 text-lg font-semibold text-indigo-500 md:text-xl">{@html $t("faq.q2")}</h3>
        <p class="text-gray-500">{@html $t("faq.a2")}</p>
      </div>
      <!-- question - end -->

      <!-- question - start -->
      <div class="relative rounded-lg bg-gray-100 p-5 pt-8">
        <span class="absolute -top-4 left-4 inline-flex h-8 w-8 items-center justify-center rounded-full bg-indigo-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
          </svg>
        </span>

        <h3 class="mb-3 text-lg font-semibold text-indigo-500 md:text-xl">{@html $t("faq.q3")}</h3>
        <p class="text-gray-500">{@html $t("faq.a3")}</p>
      </div>
      <!-- question - end -->

      <!-- question - start -->
      <div class="relative rounded-lg bg-gray-100 p-5 pt-8">
        <span class="absolute -top-4 left-4 inline-flex h-8 w-8 items-center justify-center rounded-full bg-indigo-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
          </svg>
        </span>

        <h3 class="mb-3 text-lg font-semibold text-indigo-500 md:text-xl">{@html $t("faq.q4")}</h3>
        <p class="text-gray-500">{@html $t("faq.a4")}</p>
      </div>
      <!-- question - end -->

      <!-- question - start -->
      <div class="relative rounded-lg bg-gray-100 p-5 pt-8">
        <span class="absolute -top-4 left-4 inline-flex h-8 w-8 items-center justify-center rounded-full bg-indigo-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-8-3a1 1 0 00-.867.5 1 1 0 11-1.731-1A3 3 0 0113 8a3.001 3.001 0 01-2 2.83V11a1 1 0 11-2 0v-1a1 1 0 011-1 1 1 0 100-2zm0 8a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
          </svg>
        </span>

        <h3 class="mb-3 text-lg font-semibold text-indigo-500 md:text-xl">{@html $t("faq.q5")}</h3>
        <p class="text-gray-500">{@html $t("faq.a5")}</p>
      </div>
      <!-- question - end -->

	</div>
</div>



</section>



<hr class="h-px my-8 bg-gray-200 border-0 dark:bg-gray-300">


<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-2xl px-4 md:px-8">

    <div class="mb-10 md:mb-16">
      <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">{@html $t("bugs.head")}(2023/10/01)</h2>

      <p class="mx-auto max-w-screen-md text-center text-gray-500 md:text-lg"></p>
    </div>

    <div class="grid gap-4 sm:grid-cols-2 md:gap-8 xl:grid-cols-3">
<!---
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
-->

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title1")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description1")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title2")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description2")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title3")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description3")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title4")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description4")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title5")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description5")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title6")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description6")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title7")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description7")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title8")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description8")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title9")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description9")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title10")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description10")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title11")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description11")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title12")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description12")}</p>
  </div>
</div>

<div class="flex divide-x rounded-lg border bg-gray-50">
  <div class="flex items-center p-2 text-indigo-500 md:p-4">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 md:h-8 md:w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
    </svg>
  </div>
  <div class="p-4 md:p-6">
    <h3 class="mb-2 text-lg font-semibold md:text-xl">{@html $t("bugs.title13")}</h3>
    <p class="text-gray-500">{@html $t("bugs.description13")}</p>
  </div>
</div>


    </div>
  </div>
</div>


<!-- Note Section -->
<section id="testimonials" class="bg-gray-100 py-20">
  <div class="container mx-auto">
      <h2 class="text-2xl mb-3">{@html $t("note.precautions.title")}</h2>
      <!-- Example testimonial; you can add more -->
      <div class="p-4 mb-8 bg-white shadow rounded">
        <p>{@html $t("note.precautions.msg1")}</p>
        <p>{@html $t("note.precautions.msg2")}</p>
        <p>{@html $t("note.precautions.msg4")}</p>
        <p>{@html $t("note.precautions.msg3")}</p>
      </div>
  </div>
  <div class="container mx-auto">
    <h2 class="text-2xl mb-3">{@html $t("note.policy.title")}</h2>
    <!-- Example testimonial; you can add more -->
    <div class="p-4 mb-8 bg-white shadow rounded">
      <p>{@html $t("note.policy.msg1")}</p>
      <p>{@html $t("note.policy.msg2")}</p>
    </div>
</div>
</section>







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