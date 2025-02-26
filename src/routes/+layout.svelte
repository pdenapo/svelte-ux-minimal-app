<script lang="ts">
  import "../app.css";
  let { children } = $props();
  import {
    AppBar,
    AppLayout,
    Button,
    Icon,
    NavItem,
    settings,
    ThemeSelect,
    Tooltip,
  } from "svelte-ux";
  import { page } from "$app/stores";
  import { mdiPrinter, mdiBookOpenVariant } from "@mdi/js";

  settings({
    components: {
      AppBar: {
        classes: "bg-primary text-white shadow-md",
      },
      AppLayout: {
        classes: {
          nav: "bg-neutral-800 py-2",
        },
      },
      NavItem: {
        classes: {
          root: "text-sm text-gray-400 pl-6 py-2 hover:text-white hover:bg-gray-300/10 [&:where(.is-active)]:text-sky-400 [&:where(.is-active)]:bg-gray-500/10",
        },
      },
    },
  });
</script>

<AppLayout navWidth={200}>
  <!-- Nav menu 
  <svelte:fragment slot="nav">
    <NavItem
      path="/"
      text="Home"
      icon="M10,20V14H14V20H19V12H22L12,3L2,12H5V20H10Z"
      currentUrl={$page.url}
    />

    <NavItem path="/about" text="About" currentUrl={$page.url} />
  </svelte:fragment>
-->

  <AppBar title="Svelte-ux-App" class="bg-primary text-primary-content p-3">
    <div slot="actions" class="flex gap-3 p-4">
      <!-- App actions -->
      <Tooltip title="Svelte-ux documentation" placement="bottom" offset={2}>
        <Button
          class="p-2"
          target="_blank"
          href="https://svelte-ux.techniq.dev/"
        >
          <Icon data={mdiBookOpenVariant} size="2em" />
        </Button>
      </Tooltip>

      <Tooltip title="Print" placement="bottom" offset={2}>
        <Button on:click={() => window.print()} class="p-2" target="_blank"
          ><Icon data={mdiPrinter} size="2em" /></Button
        >
      </Tooltip>

      <Tooltip title="Elegir modo" placement="bottom" offset={2}>
        <ThemeSelect />
      </Tooltip>
    </div>
  </AppBar>
  <main>
    <div class="flex justify-center max-w-lg flex-col mx-auto p-4">
      <slot />
      <!--{@render children()}-->
    </div>
  </main>
</AppLayout>
