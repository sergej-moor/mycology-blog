<script lang="ts">
	import { goto } from '$app/navigation';
	import 'iconify-icon';
	let navbarLinks = [
		{
			name: 'Home',
			url: '/'
		},
		{
			name: 'Posts',
			url: '/posts'
		},
		{
			name: 'Contact',
			url: '/contact'
		}
	];
	let navbarMenuActive = false;

	function navigate(url: string) {
		goto(url);
		navbarMenuActive = false;
	}
</script>

<nav
	class="fixed z-50 h-12 w-full border-b-2 border-black bg-white backdrop-blur-lg backgrop-opacity-100"
>
	<ul class="flex h-full w-full items-center justify-between px-4">
		<li>
			<a
				href="/"
				class="font-heading font-bold hover:font-extrabold hover:transition-all duration-1000"
				>Shrooom</a
			>
		</li>
		<li class="sm:hidden">
			<button
				class=" flex items-center text-2xl"
				on:click={() => (navbarMenuActive = !navbarMenuActive)}
			>
				{#if !navbarMenuActive}
					<iconify-icon icon="ic:baseline-menu" />
				{:else}
					<iconify-icon icon="mdi:close" />
				{/if}
			</button>
		</li>
		<span class="hidden gap-x-8 sm:flex">
			{#each navbarLinks as link}
				<li class="transition-all hover:font-semibold hover:underline">
					<a href={link.url}>{link.name}</a>
				</li>
			{/each}
		</span>
	</ul>
</nav>
{#if navbarMenuActive}
	<div class="fixed z-50 h-full w-full bg-white">
		<div class="h-12 border-b-2 border-black">
			<ul class="flex h-full w-full items-center justify-between px-4">
				<li>
					<button
						on:click={() => navigate('/')}
						class="font-heading font-bold hover:font-extrabold hover:transition-all duration-1000"
						>Shrooom</button
					>
				</li>
				<li class="sm:hidden">
					<button
						class=" flex items-center text-2xl"
						on:click={() => (navbarMenuActive = !navbarMenuActive)}
					>
						{#if !navbarMenuActive}
							<iconify-icon icon="ic:baseline-menu" />
						{:else}
							<iconify-icon icon="mdi:close" />
						{/if}
					</button>
				</li>
			</ul>
		</div>
		<ul>
			{#each navbarLinks as link}
				<li class="border-b-2 border-black">
					<button on:click={() => navigate(link.url)} class="flex w-full p-4 text-3xl font-semibold"
						>{link.name}</button
					>
				</li>
			{/each}
		</ul>
	</div>
{/if}
