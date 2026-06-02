<script lang="ts">
	import { User } from 'lucide-svelte';

	import profilePic from '$lib/assets/developer-profile.jpg'

	let imageUrl: string = profilePic;
</script>

<div itemscope itemtype="https://schema.org/Person" class="space-y-12 animate-reveal pb-24 pt-24 max-w-4xl mx-auto">

	<div class="text-center md:text-left">
		<h2 class="text-5xl md:text-[5rem] font-bold text-white tracking-tighter leading-[0.9] mb-6">The Man Behind.</h2>
	</div>

	<div class="border-t border-white/10 pt-12">
		<div class="grid grid-cols-1 md:grid-cols-12 gap-8 md:gap-16">
			
			<div class="md:col-span-4 space-y-6">
				<div class="aspect-square rounded-3xl bg-zinc-900 border border-white/10 flex items-center justify-center overflow-hidden relative group">
					<div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500 z-10 pointer-events-none"></div>
					
					{#if imageUrl}
						<img src={imageUrl} alt="Freelance Full-Stack Developer and AI-Engineer" itemprop="image" loading="lazy" decoding="async" class="w-full h-full object-cover object-top group-hover:scale-105 transition-transform duration-700"/>
					{:else}
						<User size={64} class="text-zinc-600 group-hover:scale-110 transition-transform duration-700"/>
					{/if}
				</div>
				<div class="space-y-1">
					<h3 class="text-white font-bold text-lg">The Developer</h3>
					<p class="text-zinc-500 font-mono text-xs uppercase tracking-widest">Web | Software | AI Developer/Integrator</p>
				</div>
			</div>
			
			<div class="md:col-span-8 space-y-8">
				<h3 class="text-2xl md:text-3xl font-light text-white leading-snug text-balance">
					I don't just build things; <br/> <span class="font-bold">I engineer high-performance solutions.</span>
				</h3>
				
				<div class="space-y-6 text-zinc-400 text-lg font-light leading-relaxed">
					<p>
						With a formal background in Computer Science, my approach goes far beyond dropping elements or installing simple plugins to mask deeper architectural issues.
					</p>
					<p>
						When faced with performance bottlenecks, I prefer diving directly into the core code. I refactor heavy scripts, optimize time complexity, and implement strict memory handling. I research, debug, and solve problems at their root—an ethic honed while creating complex AI models like my RoBERTa NLP Classifier.
					</p>
					<p>
						Operating on a highly disciplined schedule, I maintain strict focus and deliver high-yield results efficiently. Whether executing a mobile-first UI redesign or architecting a zero-cost Edge-Native application, I build robust systems that respect both your budget and your users' time.
					</p>
				</div>
			</div>

		</div>
	</div>
</div>