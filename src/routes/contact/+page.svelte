<script lang="ts">
	import { CheckCircle } from 'lucide-svelte';
	import Button from '$lib/components/Button.svelte';

	// Svelte 5 Runes for reactive state variables
	let name = $state('');
	let email = $state('');
	let message = $state('');
	let submitted = $state(false);

	// Standard event handling (Svelte 5 removed the |preventDefault modifier)
	const handleSubmit = (e: Event) => {
		e.preventDefault(); 
		
		if (name && email && message) {
			submitted = true;
			setTimeout(() => {
				submitted = false;
				name = '';
				email = '';
				message = '';
			}, 4000);
		}
	};
</script>

<div class="animate-reveal pb-24 pt-24 max-w-3xl mx-auto">
	<div class="mb-16">
		<h2 class="text-5xl md:text-[5rem] font-bold text-white tracking-tighter leading-[0.9] mb-6">Initiate.</h2>
		<p class="text-xl text-zinc-400 font-light">
			Ready to optimize your site or integrate AI? Let's engineer something exceptional.
		</p>
	</div>

	<div class="bg-[#0a0a0a] border border-white/10 p-8 md:p-12 rounded-3xl relative overflow-hidden">
		{#if submitted}
			<div class="flex flex-col items-center justify-center py-16 text-center animate-reveal">
				<div class="w-20 h-20 bg-white rounded-full flex items-center justify-center mb-6 text-black">
					<CheckCircle size={32} />
				</div>
				<h3 class="text-3xl font-bold text-white tracking-tighter mb-2">Transmission Received</h3>
				<p class="text-zinc-400 font-light text-lg">Thank you, <span class="text-white font-medium">{name}</span>. I'll respond within 24 hours.</p>
			</div>
		{:else}
			<form onsubmit={handleSubmit} class="space-y-8">
				<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
					<div class="space-y-3 relative group">
						<label for="name" class="text-xs font-mono text-zinc-500 uppercase tracking-widest">Name</label>
						<input 
							type="text" id="name" required
							bind:value={name}
							class="w-full bg-transparent border-b border-white/20 py-2 text-white placeholder-zinc-700 focus:outline-none focus:border-white transition-colors rounded-none"
							placeholder="John Doe"
						/>
					</div>
					<div class="space-y-3 relative group">
						<label for="email" class="text-xs font-mono text-zinc-500 uppercase tracking-widest">Email</label>
						<input 
							type="email" id="email" required
							bind:value={email}
							class="w-full bg-transparent border-b border-white/20 py-2 text-white placeholder-zinc-700 focus:outline-none focus:border-white transition-colors rounded-none"
							placeholder="john@example.com"
						/>
					</div>
				</div>
				<div class="space-y-3 relative group">
					<label for="message" class="text-xs font-mono text-zinc-500 uppercase tracking-widest">Project Details</label>
					<textarea 
						id="message" required rows="4"
						bind:value={message}
						class="w-full bg-transparent border-b border-white/20 py-2 text-white placeholder-zinc-700 focus:outline-none focus:border-white transition-colors resize-none rounded-none"
						placeholder="Describe your technical needs..."
					></textarea>
				</div>
				<div class="pt-6 flex justify-end">
					<Button type="submit" className="w-full md:w-auto">
						Submit Request
					</Button>
				</div>
			</form>
		{/if}
	</div>
</div>