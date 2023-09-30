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
      title: 'Is it unstyled?',
      description:
        "Yes. It's unstyled by default, giving you freedom over the look and feel.",
    },
    {
      title: 'Can it be animated?',
      description:
        'Yes! You can use the transition prop to configure the animation.',
    },
  ];



</script>

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











<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-2xl px-4 md:px-8">
    <!-- text - start -->
    <div class="mb-10 md:mb-16">
      <h2 class="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-6 lg:text-3xl">既知のバグ(2023/10/01)</h2>

      <p class="mx-auto max-w-screen-md text-center text-gray-500 md:text-lg">要望やバグの報告をお願いします。報告者にはリワードを配ります。</p>
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