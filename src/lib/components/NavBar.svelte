<script lang="ts">
	import { Menu, X, Code } from 'lucide-svelte';
	import { page } from '$app/state';
	import logo from '$lib/assets/JLAbe-Logo.svg';

	let {isMobileMenuOpen = $bindable(false)}=$props();

	const navItems = [
		{id:'/', label:'Index'},
		{id:'/projects',label:'Work'},
		{id:'/services',label:'Services'},
		{id:'/about',label:'Profile'},
	];

	//interface NavbarProps {
	//	currentPage: string;
	//	isMobileMenuOpen: boolean;
	//	navigate: (page: string) => void;
	//	navItems: { id: string; label: string }[];
	//}

	// Use $bindable() so the mobile menu state syncs with the parent +page.svelte
	//let { 
	//	currentPage, 
	//	isMobileMenuOpen = $bindable(), 
	//	navigate, 
	//	navItems 
	//}: NavbarProps = $props();
</script>

<nav class="fixed top-6 left-0 right-0 z-50 flex justify-center px-4 pointer-events-none">
	<div class="pointer-events-auto glass-pill px-2 py-2 rounded-full flex items-center justify-between w-full max-w-sm md:max-w-xl shadow-2xl transition-all duration-300">
		
		<a href="/" aria-label="Return to homepage" class="w-10 h-10 rounded-full bg-white text-black flex items-center justify-center hover:scale-95 transition-transform shrink-0">
			<Code size={18} strokeWidth={2.5} aria-hidden="true" />
			<img src={logo} alt="JLAbe Logo" class="object-contain rounded-full" />
		</a>

		<div class="hidden md:flex items-center space-x-1 px-4">
			{#each navItems as item}
				<a
					href="{item.id}"
					class="px-4 py-2 rounded-full text-sm font-medium transition-colors {page.url.pathname === item.id ? 'text-white bg-white/10' : 'text-zinc-400 hover:text-white'}"
				>
					{item.label}
				</a>
			{/each}
		</div>

		<div class="flex items-center gap-2">
			<a href="/contact" class="hidden md:flex px-5 py-2.5 rounded-full text-sm font-medium text-white bg-white/10 hover:bg-white hover:text-black transition-colors">
				Contact
			</a>
			
			<button aria-label="Toggle mobile menu" aria-expanded={isMobileMenuOpen} onclick={() => isMobileMenuOpen = !isMobileMenuOpen} class="md:hidden w-10 h-10 rounded-full bg-white/10 text-white flex items-center justify-center hover:bg-white/20 transition-colors">
				{#if isMobileMenuOpen}
					<X size={20} />
				{:else}
					<Menu size={20} />
				{/if}
			</button>
		</div>
	</div>
</nav>