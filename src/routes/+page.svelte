<script lang="ts">
	// Import icons
	import { Menu, X, Code, Mail } from 'lucide-svelte';
	
	// Import components
	import Home from '$lib/components/Home.svelte';
	import Projects from '$lib/components/Projects.svelte';
    import Services from '$lib/components/Services.svelte';
	import About from '$lib/components/About.svelte';
	import Contact from '$lib/components/Contact.svelte';
	import Button from '$lib/components/Button.svelte';	

	// Define reactive state using Svelte 5 Runes
	let currentPage = $state('home');
	let isMobileMenuOpen = $state(false);

	// Navigation function passed down to components
	const navigate = (page: string) => {
		currentPage = page;
		isMobileMenuOpen = false;
		window.scrollTo({ top: 0, behavior: 'smooth' });
	};

	const navItems = [
		{ id: 'home', label: 'Index' },
		{ id: 'projects', label: 'Work' },
        { id: 'services', label: 'Services' },
		{ id: 'about', label: 'Profile' },
	];
</script>

<svelte:head>
	<title>High Performance Developer & AI Integrator | Philippines</title>
	<meta name="description" content="Freelance Hybrid Developer and AI Engineer in the Philippines. Specializing in zero-cost edge architecture, mobile-first development, and Performance Optimization" />
	<meta name="robots" content="index, follow" />

	<script type="application/ld+json">
		{
			"@content": "https://schema.org",
			"@type": "ProfessionalService",
			"name": "High-Performance Developer",
			"image": "./developer-profile.jpg",
			"description": "Hybrid Developer & AI Engineer specializing in strict memory handling, custom NLP solutions, and mobile-first UI/UX.",
			"address": {
				"@type": "PostalAddress",
				"addressCountry": "PH"
			}
			"priceRange": "$$"
		}
	</script>
</svelte:head>

<div class="min-h-screen bg-[#050505] text-zinc-50 font-sans selection:bg-white selection:text-black flex flex-col relative overflow-x-hidden">
	
	<div class="bg-noise"></div>
	<div class="fixed inset-0 pointer-events-none z-0 flex items-center justify-center overflow-hidden">
		<div class="w-[150vw] h-[150vh] opacity-30 bg-[radial-gradient(ellipse_at_center,_var(--tw-gradient-stops))] from-zinc-900 via-[#050505] to-[#050505]"></div>
	</div>

	<nav class="fixed top-6 left-0 right-0 z-50 flex justify-center px-4 pointer-events-none">
		<div class="pointer-events-auto glass-pill px-2 py-2 rounded-full flex items-center justify-between w-auto md:gap-4 gap-12 shadow-2xl transition-all duration-300">
			
			<a href="#home" aria-label="Return to homepage" onclick={(e) => {e.preventDefault(); navigate('home'); }} class="w-10 h-10 rounded-full bg-white text-black flex items-center justify-center hover:scale-95 transition-transform shrink-0">
				<Code size={18} strokeWidth={2.5} />
			</a>

			<div class="hidden md:flex items-center space-x-1">
				{#each navItems as item}
					<a href="#{item.id}" onclick={(e) => {e.preventDefault(); navigate(item.id);}} class="px-4 py-2 rounded-full text-sm font-medium transition-colors {currentPage === item.id ? 'text-white bg-white/10' : 'text-zinc-400 hover:text-white'}">
						{item.label}
					</a>
				{/each}
			</div>

			<div class="flex items-center gap-2 shrink-0">
				<a href="#contact" onclick={(e) => {e.preventDefault();navigate('contact');}} class="hidden md:flex px-5 py-2.5 rounded-full text-sm font-medium text-white bg-white/10 hover:bg-white hover:text-black transition-colors whitespace-nowrap">
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


	<!-- Mobile Menu -->

	<div class="fixed inset-0 bg-[#050505]/95 backdrop-blur-2xl z-40 flex flex-col justify-center items-center transition-opacity duration-500 {isMobileMenuOpen ? 'opacity-100 pointer-events-auto' : 'opacity-0 pointer-events-none'}">
		<div class="flex flex-col items-center space-y-8">
			{#each navItems as item}
				<a
					href="{item.id}"
					onclick={(e) => {e.preventDefault();navigate(item.id);}}
					class="text-4xl font-bold tracking-tighter transition-all {currentPage === item.id ? 'text-white scale-110' : 'text-zinc-600 hover:text-white'}"
				>
					{item.label}
				</a>
			{/each}
			<div class="pt-8 w-full max-w-xs">
				<Button onclick={(e) => {e.preventDefault();navigate('contact');}} className="w-full text-lg py-4">
					Start Project
				</Button>
			</div>
		</div>
	</div>

	<main class="flex-grow w-full max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 pt-20 relative z-10">
		{#if currentPage === 'home'}
			<Home {navigate} />
		{:else if currentPage === 'services'}
			<Services {navigate} /> 
		{:else if currentPage === 'projects'}
			<Projects />
		{:else if currentPage === 'about'}
			<About />
		{:else if currentPage === 'contact'}
			<Contact />
		{/if}
	</main>

	<footer class="border-t border-white/10 bg-transparent relative z-10 mt-auto">
		<div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
			<div class="flex flex-col md:flex-row justify-between items-center gap-4">
				<span class="font-mono text-xs uppercase tracking-widest text-zinc-500">
					© 2026. Engineered for the Edge.
				</span>
				
				<a 
					href="#contact" aria-label="Send an email" onclick={(e) => {e.preventDefault();navigate('contact');}} class="text-zinc-500 hover:text-white transition-colors">
					<Mail size={18} />
				</a>
			</div>
		</div>
	</footer>
</div>