<script lang="ts">
    import PackageOpen from "@lucide/svelte/icons/package-open";
    import House from "@lucide/svelte/icons/house";
    import Palette from "@lucide/svelte/icons/palette";
    import Tags from "@lucide/svelte/icons/tags";
    import Unplug from "@lucide/svelte/icons/unplug";
    import * as Sidebar from "$lib/components/ui/sidebar/index.js";
    import Cloudy from "@lucide/svelte/icons/cloudy";
    import NavUser from "./NavUser.svelte";
    import ModeToggle from "./ModeToggle.svelte";

    // Menu items.
    const items = [
        {
            title: "Home",
            url: "#",
            icon: House,
        },
        {
            title: "Design",
            url: "#",
            icon: Palette,
        },
        {
            title: "Describe",
            url: "#",
            icon: Tags,
        },
        {
            title: "Package",
            url: "#",
            icon: PackageOpen,
        },
        {
            title: "Connect",
            url: "#",
            icon: Unplug,
        },
    ];

    const user = {
        name: "abroudoux",
        email: "arthur.broudoux@example.com",
        avatar: "https://avatars.githubusercontent.com/u/115638259?v=4",
    };
</script>

<Sidebar.Root variant="inset" collapsible="icon">
    <Sidebar.Header>
        <Sidebar.Menu>
            <Sidebar.MenuItem>
                <Sidebar.MenuButton size="lg">
                    {#snippet child({ props })}
                        <a href="##" {...props}>
                            <div
                                class="bg-sidebar-primary text-sidebar-primary-foreground flex aspect-square size-8 items-center justify-center rounded-lg"
                            >
                                <Cloudy class="size-4" />
                            </div>
                            <div class="flex flex-col gap-0.5 leading-none">
                                <span class="font-semibold"
                                    >Microcks Studio</span
                                >
                                <span class="">v1.0.0</span>
                            </div>
                        </a>
                    {/snippet}
                </Sidebar.MenuButton>
            </Sidebar.MenuItem>
        </Sidebar.Menu>
    </Sidebar.Header>
    <Sidebar.Content>
        <Sidebar.Group>
            <Sidebar.GroupLabel>Application</Sidebar.GroupLabel>
            <Sidebar.GroupContent>
                <Sidebar.Menu>
                    {#each items as item (item.title)}
                        <Sidebar.MenuItem>
                            <Sidebar.MenuButton>
                                {#snippet child({ props })}
                                    <a href={item.url} {...props}>
                                        <item.icon />
                                        <span>{item.title}</span>
                                    </a>
                                {/snippet}
                            </Sidebar.MenuButton>
                        </Sidebar.MenuItem>
                    {/each}
                </Sidebar.Menu>
            </Sidebar.GroupContent>
        </Sidebar.Group>
    </Sidebar.Content>
    <Sidebar.Footer>
        <NavUser {user} />
    </Sidebar.Footer>
</Sidebar.Root>
