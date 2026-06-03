<script lang="ts">
	import { Brain, Zap, Smartphone, Globe, Code, Wrench, ArrowRight } from 'lucide-svelte';

	interface ServicesProps {
		navigate: (page: string) => void;
	}

	let { navigate }: ServicesProps = $props();


	const services = [
		{
			title: "Lighthouse Acceleration",
			description: "Refactoring resource-heavy JavaScript and implementing strict memory handling to boost native performance from 40 to near 100.",
			icon: Zap,
			category: "Performance"
		},
		{
			title: "AI & NLP Integration",
			description: "Developing custom NLP models (like RoBERTa) for data classification and integrating lightweight, edge-native AI solutions directly into the browser.",
			icon: Brain,
			category: "Machine Learning"
		},
		{
			title: "Mobile-First UI/UX",
			description: "Executing comprehensive architectural redesigns specifically targeted at mobile views to guarantee intuitive cross-device experiences.",
			icon: Smartphone,
			category: "Design"
		},
		{
			title: "WordPress Architectures",
			description: "Building dynamic, high-performing websites utilizing deep expertise in Yootheme Pro, Elementor, and custom implementations.",
			icon: Globe,
			category: "Web Dev"
		},
		{
			title: "Advanced Code Refactoring",
			description: "Diving into core code to optimize time complexity, resolve bottlenecks, and stabilize heavy legacy web applications.",
			icon: Code,
			category: "Engineering"
		},
		{
			title: "Maintenance & Debugging",
			description: "Active debugging of critical site errors and ongoing technical retainers to ensure continuous high-availability for local businesses.",
			icon: Wrench,
			category: "Support"
		}
	];
</script>

<div class="space-y-12 animate-reveal pb-24 pt-24">
	<div class="max-w-2xl">
		<h2 class="text-5xl md:text-6xl font-bold text-white tracking-tighter leading-[0.9] mb-6">Capabilities.</h2>
		<p class="text-xl text-zinc-400 font-light leading-relaxed">
			A hybrid offering of high-performance web engineering and applied artificial intelligence.
		</p>
	</div>

	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 pt-8">
		{#each services as service, i}
			<div 
				class="bg-[#0a0a0a] border border-white/5 hover:border-white/20 rounded-3xl p-8 transition-all duration-500 group flex flex-col justify-between animate-reveal"
				style="animation-delay: {i * 100}ms;"
			>
				<div>
					<div class="flex justify-between items-start mb-8">
						<div class="w-12 h-12 rounded-full bg-white/5 border border-white/10 flex items-center justify-center group-hover:scale-110 group-hover:bg-white/10 transition-all duration-500">
							<svelte:component this={service.icon} size={20} class="text-zinc-300 group-hover:text-white transition-colors" />
						</div>
						<span class="text-[10px] font-mono text-zinc-600 uppercase tracking-widest">{service.category}</span>
					</div>
					
					<h3 class="text-2xl font-bold text-white tracking-tighter mb-4">{service.title}</h3>
					<p class="text-zinc-400 font-light leading-relaxed text-sm">
						{service.description}
					</p>
				</div>

				<div class="mt-8 pt-6 border-t border-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500">
					<button onclick={() => navigate('contact')} class="text-xs font-mono text-white flex items-center gap-2 uppercase tracking-widest hover:text-zinc-300 transition-colors">
						Initiate Request <ArrowRight size={14} />
					</button>
				</div>
			</div>
		{/each}
	</div>
</div>