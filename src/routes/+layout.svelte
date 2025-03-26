<script>
    import { ModeWatcher } from "mode-watcher";

    import "../app.css";
    import * as Sidebar from "$lib/components/ui/sidebar/index";
    import AppSidebar from "$lib/components/app-sidebar.svelte";

    let { children } = $props();
</script>

<Sidebar.Provider>
    <AppSidebar />
    <Sidebar.Inset>
        <!-- <Sidebar.Trigger class="m-2" /> -->
        <main class="p-4">
            {@render children?.()}
        </main>
    </Sidebar.Inset>
</Sidebar.Provider>

<ModeWatcher />
