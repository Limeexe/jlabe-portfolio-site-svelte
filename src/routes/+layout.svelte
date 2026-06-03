<script lang="ts">
	import './layout.css';
	import {page} from '$app/state';
	import {Mail} from 'lucide-svelte';

	// UI Components
	import favicon from '$lib/assets/JLAbe-logo-darkmode.svg';
	import NavBar from '$lib/components/NavBar.svelte';
	import Button from '$lib/components/Button.svelte';

	let {children} = $props();

	// Layout level management for mobile menu
	let isMobileMenuOpen = $state(false);

	const navItems = [
		{ id: '/', label: 'Index' },
		{ id: '/projects', label: 'Work' },
        { id: '/services', label: 'Services' },
		{ id: '/about', label: 'Profile' },
	];
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>


<div class="min-h-screen bg-[#050505] text-zinc-50 font-sans selection:bg-white selection:text-black flex flex-col relative overflow-x-hidden">

	<div class="bg-noise"></div>
	<div class="fixed inset-0 pointer-events-none z-0 flex items-center justify-center overflow-hidden">
		<div class="w-[150vw] h-[150vh] opacity-30 bg-[radial-gradient(ellipse_at_center,var(--tw-gradient-stops))] from-zinc-900 via-[#050505] to-[#050505]"></div>
	</div>

	<NavBar bind:isMobileMenuOpen />

	<div class="fixed inset-0 bg-[#050505]/95 backdrop-blur-2xl z-40 flex flex-col justify-center items-center transition-opacity duration-500 {isMobileMenuOpen ? 'opacity-100 pointer-events-auto' : 'opacity-0 pointer-events-none'}">
		<div class="flex flex-col items-center space-y-8">
			{#each navItems as item}
				<a
					href={item.id}
					onclick={() => isMobileMenuOpen = false}
					class="text-4xl font-bold tracking-tighter transition-all {page.url.pathname === item.id ? 'text-white scale-110' : 'text-zinc-600 hover:text-white'}"
				>
					{item.label}
				</a>
			{/each}
			<div class="pt-8 w-full max-w-xs">
				<a href="/contact" onclick={() => isMobileMenuOpen = false} class="block w-full">
					<Button className="w-full text-lg py-4">
						Start Project
					</Button>
				</a>
			</div>
		</div>
	</div>

	<main class="grow w-full max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 pt-20 relative z-10">
		{@render children()}
	</main>
	
	<footer class="border-t border-white/10 bg-transparent relative z-10 mt-auto">
		<div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
			<div class="flex flex-col md:flex-row justify-between items-center gap-4">
				<span class="font-mono text-xs uppercase tracking-widest text-zinc-500">
					© 2026. Engineered for the Edge.
				</span>
				
				<a href="/contact" aria-label="Send an email" class="text-zinc-500 hover:text-white transition-colors">
					<Mail size={18} />
				</a>
			</div>
		</div>
	</footer>
</div>
