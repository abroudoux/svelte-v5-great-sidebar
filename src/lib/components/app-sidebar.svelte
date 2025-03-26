<script lang="ts">
    import type { Icon as IconType } from "@lucide/svelte";
    import PackageOpen from "@lucide/svelte/icons/package-open";
    import House from "@lucide/svelte/icons/house";
    import Palette from "@lucide/svelte/icons/palette";
    import Tags from "@lucide/svelte/icons/tags";
    import Unplug from "@lucide/svelte/icons/unplug";
    import BadgeCheck from "@lucide/svelte/icons/badge-check";
    import Bell from "@lucide/svelte/icons/bell";
    import ChevronsUpDown from "@lucide/svelte/icons/chevrons-up-down";
    import CreditCard from "@lucide/svelte/icons/credit-card";
    import LogOut from "@lucide/svelte/icons/log-out";
    import Sparkles from "@lucide/svelte/icons/sparkles";
    import Cloudy from "@lucide/svelte/icons/cloudy";

    import * as Sidebar from "$lib/components/ui/sidebar/index.js";
    import * as Avatar from "$lib/components/ui/avatar/index";
    import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index";

    import { useSidebar } from "$lib/components/ui/sidebar/index";

    interface SidebarItem {
        title: string;
        url: string;
        icon: typeof IconType;
    }

    const items: SidebarItem[] = [
        {
            title: "Home",
            url: "/",
            icon: House,
        },
        {
            title: "Design",
            url: "/design",
            icon: Palette,
        },
        {
            title: "Describe",
            url: "/describe",
            icon: Tags,
        },
        {
            title: "Package",
            url: "/package",
            icon: PackageOpen,
        },
        {
            title: "Connect",
            url: "/connect",
            icon: Unplug,
        },
    ];

    const user = {
        name: "abroudoux",
        email: "arthur.broudoux@example.com",
        avatar: "https://avatars.githubusercontent.com/u/115638259?v=4",
    };

    const sidebar = useSidebar();
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
        <Sidebar.Menu>
            <Sidebar.MenuItem>
                <DropdownMenu.Root>
                    <DropdownMenu.Trigger>
                        {#snippet child({ props })}
                            <Sidebar.MenuButton
                                size="lg"
                                class="data-[state=open]:bg-sidebar-accent data-[state=open]:text-sidebar-accent-foreground"
                                {...props}
                            >
                                <Avatar.Root class="h-8 w-8 rounded-lg">
                                    <Avatar.Image
                                        src={user.avatar}
                                        alt={user.name}
                                    />
                                    <Avatar.Fallback class="rounded-lg"
                                        >AB</Avatar.Fallback
                                    >
                                </Avatar.Root>
                                <div
                                    class="grid flex-1 text-left text-sm leading-tight"
                                >
                                    <span class="truncate font-semibold"
                                        >{user.name}</span
                                    >
                                    <span class="truncate text-xs"
                                        >{user.email}</span
                                    >
                                </div>
                                <ChevronsUpDown class="ml-auto size-4" />
                            </Sidebar.MenuButton>
                        {/snippet}
                    </DropdownMenu.Trigger>
                    <DropdownMenu.Content
                        class="w-[var(--bits-dropdown-menu-anchor-width)] min-w-56 rounded-lg"
                        side={sidebar.isMobile ? "bottom" : "right"}
                        align="end"
                        sideOffset={4}
                    >
                        <DropdownMenu.Label class="p-0 font-normal">
                            <div
                                class="flex items-center gap-2 px-1 py-1.5 text-left text-sm"
                            >
                                <Avatar.Root class="h-8 w-8 rounded-lg">
                                    <Avatar.Image
                                        src={user.avatar}
                                        alt={user.name}
                                    />
                                    <Avatar.Fallback class="rounded-lg"
                                        >CN</Avatar.Fallback
                                    >
                                </Avatar.Root>
                                <div
                                    class="grid flex-1 text-left text-sm leading-tight"
                                >
                                    <span class="truncate font-semibold"
                                        >{user.name}</span
                                    >
                                    <span class="truncate text-xs"
                                        >{user.email}</span
                                    >
                                </div>
                            </div>
                        </DropdownMenu.Label>
                        <DropdownMenu.Separator />
                        <DropdownMenu.Group>
                            <DropdownMenu.Item>
                                <Sparkles />
                                Upgrade to Pro
                            </DropdownMenu.Item>
                        </DropdownMenu.Group>
                        <DropdownMenu.Separator />
                        <DropdownMenu.Group>
                            <DropdownMenu.Item>
                                <BadgeCheck />
                                Account
                            </DropdownMenu.Item>
                            <DropdownMenu.Item>
                                <CreditCard />
                                Billing
                            </DropdownMenu.Item>
                            <DropdownMenu.Item>
                                <Bell />
                                Notifications
                            </DropdownMenu.Item>
                        </DropdownMenu.Group>
                        <DropdownMenu.Separator />
                        <DropdownMenu.Item>
                            <LogOut />
                            Log out
                        </DropdownMenu.Item>
                    </DropdownMenu.Content>
                </DropdownMenu.Root>
            </Sidebar.MenuItem>
        </Sidebar.Menu>
    </Sidebar.Footer>
</Sidebar.Root>
