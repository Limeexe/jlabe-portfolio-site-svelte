<script lang="ts">
    import {Zap, ArrowUpRight, ArrowRight} from 'lucide-svelte';
    import BentoCard from '$lib/components/BentoCard.svelte';

    interface HomeProps{
        navigate: (page:string) => void;
    }

    let {navigate}: HomeProps = $props();

    const techStack: string[] = [
        'React', 'Svelte', 'TypeScript', 'Tailwinds', 'WordPress', 'Python', 'C', 'C++'
    ];
</script>

<div class="space-y-6 md:space-y-8 animate-reveal pb-24">
    <!-- Hero Section -->
	<section class="pt-24 md:pt-36 pb-12 md:pb-20 flex flex-col items-center text-center px-4 relative z-10">
		<div class="inline-flex items-center gap-2 px-4 py-2 rounded-full border border-white/10 bg-white/[0.03] text-xs font-mono text-zinc-400 uppercase tracking-widest mb-10 animate-reveal">
			<span class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse"></span>
			Available for new projects
		</div>
		
		<div class="space-y-6 max-w-5xl mx-auto animate-reveal delay-100">
			<h1 class="text-5xl sm:text-7xl md:text-[6rem] font-bold tracking-tighter text-white leading-[0.9] text-balance">
				Engineering <span class="text-zinc-500">digital</span><br />
				experiences.
			</h1>
			<p class="text-lg md:text-xl text-zinc-400 max-w-2xl mx-auto font-light leading-relaxed mt-8">
				Hybrid Web Developer & AI Engineer. Specializing in zero-cost edge architectures, mobile-first design, and deep technical optimizations.
			</p>
		</div>
	</section>

    <!-- The Bento Box Grid -->
	<sections class="grid grid-cols-1 md:grid-cols-3 md:grid-rows-[auto_auto] gap-4 md:gap-6 z-10 relative">
		
		<!-- Massive featured card -->
		<BentoCard className="md:col-span-2 md:row-span-2 min-h-[400px] flex flex-col justify-between animate-reveal delay-200" hover={true}>
			<div class="flex justify-between items-start mb-8">
				<div class="w-12 h-12 rounded-full bg-white/5 border border-white/10 flex items-center justify-center">
					<Zap size={20} class="text-white" />
				</div>
				<!-- Svelte 5 uses standard HTML onclick instead of on:click -->
				<button onclick={() => navigate('projects')} class="w-10 h-10 rounded-full border border-white/10 flex items-center justify-center group-hover:bg-white group-hover:text-black transition-colors">
					<ArrowUpRight size={18} />
				</button>
			</div>
			
			<div>
				<span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-4">Featured Capability</span>
				<h2 class="text-3xl md:text-5xl font-bold text-white tracking-tighter leading-[1.1] mb-4">
					Lighthouse <br class="hidden md:block"/> Acceleration.
				</h2>
				<p class="text-zinc-400 font-light max-w-md">
					Refactoring resource-heavy JavaScript and implementing strict memory handling to boost native performance from 40 to 100.
				</p>
			</div>
		</BentoCard>

        <!-- About/Stack Card -->
		<BentoCard className="md:col-span-1 animate-reveal delay-400">
			<span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-6">Arsenal</span>
			<div class="flex flex-wrap gap-2">
				{#each techStack as tech}
					<span class="px-3 py-1.5 rounded-full border border-white/10 text-xs text-zinc-300 bg-white/[0.02]">
						{tech}
					</span>
				{/each}
			</div>
			<div class="mt-8 pt-8 border-t border-white/5">
				 <button onclick={() => navigate('about')} class="text-sm text-white flex items-center gap-2 group-hover:gap-3 transition-all">
					 Read the story <ArrowRight size={16} class="text-zinc-500 group-hover:text-white transition-colors" />
				 </button>
			</div>
		</BentoCard>

    </sections>

</div>