<script lang="ts">
	import { ArrowUpRight } from 'lucide-svelte';
</script>

<div class="space-y-12 animate-reveal pb-24 pt-24">
	<div class="max-w-2xl">
		<h2 class="text-5xl md:text-6xl font-bold text-white tracking-tighter leading-[0.9] mb-6">Proof of Work.</h2>
		<p class="text-xl text-zinc-400 font-light leading-relaxed">
			I focus on engineering depth over sheer quantity. Case studies demonstrating complex problem-solving.
		</p>
	</div>

	<div class="grid grid-cols-1 gap-6">
		
		<div class="group cursor-pointer">
			<div class="bg-[#0a0a0a] border border-white/10 rounded-3xl overflow-hidden relative min-h-[400px] flex flex-col justify-end p-8 md:p-12 transition-all duration-700 hover:border-white/30">
				<div class="absolute inset-0 bg-gradient-to-tr from-indigo-900/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-700"></div>
				
				<div class="relative z-10 flex flex-col md:flex-row md:items-end justify-between gap-8">
					<div class="max-w-2xl">
						<div class="flex items-center gap-3 mb-6">
							<span class="px-3 py-1 rounded-full border border-white/20 text-xs font-mono text-zinc-300 backdrop-blur-md">Performance</span>
							<span class="px-3 py-1 rounded-full border border-white/20 text-xs font-mono text-zinc-300 backdrop-blur-md">WP</span>
						</div>
						<h3 class="text-4xl md:text-5xl font-bold text-white tracking-tighter mb-4 group-hover:translate-x-2 transition-transform duration-500">
							Equity Track Optimization
						</h3>
						<p class="text-lg text-zinc-400 font-light">
							Deep code refactoring and memory handling to boost native Google Lighthouse scores from 40 to 100 for Peninsula Plumbing & Twin Home Buyer.
						</p>
					</div>
					
					<div class="w-14 h-14 rounded-full bg-white text-black flex items-center justify-center shrink-0 opacity-0 -translate-x-4 group-hover:opacity-100 group-hover:translate-x-0 transition-all duration-500 ease-out">
						<ArrowUpRight size={24} />
					</div>
				</div>
			</div>
		</div>

		<div class="group cursor-pointer">
			<div class="bg-[#0a0a0a] border border-white/10 rounded-3xl overflow-hidden relative min-h-[400px] flex flex-col justify-end p-8 md:p-12 transition-all duration-700 hover:border-white/30">
				<div class="absolute inset-0 bg-gradient-to-tr from-purple-900/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-700"></div>
				
				<div class="relative z-10 flex flex-col md:flex-row md:items-end justify-between gap-8">
					<div class="max-w-2xl">
						<div class="flex items-center gap-3 mb-6">
							<span class="px-3 py-1 rounded-full border border-white/20 text-xs font-mono text-zinc-300 backdrop-blur-md">AI / ML</span>
							<span class="px-3 py-1 rounded-full border border-white/20 text-xs font-mono text-zinc-300 backdrop-blur-md">Python</span>
						</div>
						<h3 class="text-4xl md:text-5xl font-bold text-white tracking-tighter mb-4 group-hover:translate-x-2 transition-transform duration-500">
							NLP Fake News Classifier
						</h3>
						<p class="text-lg text-zinc-400 font-light">
							Developed and pre-trained a complex classification model using the RoBERTa architecture specifically engineered for deep contextual semantic analysis.
						</p>
					</div>
					
					<div class="w-14 h-14 rounded-full bg-white text-black flex items-center justify-center shrink-0 opacity-0 -translate-x-4 group-hover:opacity-100 group-hover:translate-x-0 transition-all duration-500 ease-out">
						<ArrowUpRight size={24} />
					</div>
				</div>
			</div>
		</div>

	</div>
</div>