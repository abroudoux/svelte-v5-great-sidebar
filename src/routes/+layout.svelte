<script>
    import { ModeWatcher } from "mode-watcher";

    import "../app.css";
    import * as Sidebar from "$lib/components/ui/sidebar/index";
    import AppSidebar from "$lib/components/AppSidebar.svelte";

    let { children } = $props();
</script>

<Sidebar.Provider>
    <AppSidebar />
    <Sidebar.Inset>
        <main class="p-4">
            <!-- <Sidebar.Trigger /> -->
            {@render children?.()}
        </main>
    </Sidebar.Inset>
</Sidebar.Provider>

<ModeWatcher />
