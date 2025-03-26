<script>
    import { ModeWatcher } from "mode-watcher";

    import "../app.css";
    import * as Sidebar from "$lib/components/ui/sidebar/index";
    import AppSidebar from "$lib/components/app-sidebar.svelte";
    import * as Breadcrumb from "$lib/components/ui/breadcrumb";
    import { Separator } from "$lib/components/ui/separator";
    import ModeToggle from "$lib/components/mode-toggle.svelte";

    let { children } = $props();
</script>

<Sidebar.Provider>
    <AppSidebar />
    <Sidebar.Inset>
        <header
            class="bg-background sticky top-0 flex h-16 shrink-0 items-center justify-between gap-2 border-b px-4 rounded-t-xl flex-row"
        >
            <div class="flex flex-row items-center gap-1">
                <Sidebar.Trigger class="-ml-1" />
                <Separator orientation="vertical" class="mr-2 h-4" />
                <Breadcrumb.Root>
                    <Breadcrumb.List>
                        <Breadcrumb.Item>
                            <Breadcrumb.Page>Dashboard</Breadcrumb.Page>
                        </Breadcrumb.Item>
                    </Breadcrumb.List>
                </Breadcrumb.Root>
            </div>
            <ModeToggle />
        </header>
        <main class="p-4">
            {@render children?.()}
        </main>
    </Sidebar.Inset>
</Sidebar.Provider>

<ModeWatcher />
