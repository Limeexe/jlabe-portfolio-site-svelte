<script lang="ts">
    import {Zap, ArrowUpRight, ArrowRight, ShieldCheck, User} from 'lucide-svelte';
    import BentoCard from '$lib/components/BentoCard.svelte';
	import Button from '$lib/components/Button.svelte';

	import {PUBLIC_WEB3FORMS_KEY} from '$env/static/public';

    const techStack: string[] = ['React', 'Svelte', 'TypeScript', 'Tailwinds', 'WordPress', 'Python', 'C', 'C++', 'SQL'];

	let isSubmitting = $state(false);

	const handleFormSubmit = async (e: SubmitEvent) => {
		e.preventDefault();
		isSubmitting = true;

		const form = e.target as HTMLFormElement;
		const formData = new FormData(form);

		formData.set("access_key", PUBLIC_WEB3FORMS_KEY);

		try {
			const response = await fetch('https://api.web3forms.com/submit', {method: 'POST', body: formData});

			const data = await response.json();

			if (response.ok) {
				alert("Success! Your message has been sent.");
				form.reset();
			} else {
				alert("Error: " + data.message);
			}
		} catch {
			alert("Something went wrong. Please try again.");
		} finally {
			isSubmitting = false;
		}
	};
</script>

<svelte:head>
	<title>JLAbe High Performance Development & AI | Philippines</title>
	<meta name="description" content="Freelance Hybrid Developer and AI Engineer in the Philippines. Specializing in zero-cost edge architecture, mobile-first development, and Performance Optimization" />
	<meta name="robots" content="index, follow" />

	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "ProfessionalService",
			"name": "JLAbe's Digital Essentials",
			"image": "https://jlabe-ph-freelance-developer.pages.dev/developer-profile.jpg",
			"description": "Enterprise-grade web application development, AI integration, software architecture, and technical consulting services.",
			"address": {
                "@type": "PostalAddress",
                "addressRegion": "Bicol",
                "addressCountry": "Philippines"
            }
			"priceRange": "$$"
		}
	</script>
</svelte:head>

<div class="space-y-12 md:space-y-16 pb-24">
	
	<section class="pt-28 md:pt-20 pb-12 md:pb-20 flex flex-col items-center text-center px-4 relative z-10">
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full border border-white/10 bg-white/3 text-xs font-mono text-zinc-400 uppercase tracking-widest mb-10">
            <span class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse" aria-hidden="true"></span>
            Available for freelance projects
        </div>
        
        <div class="space-y-8 max-w-5xl mx-auto">
            <h1 class="text-6xl sm:text-7xl md:text-[7rem] font-bold tracking-tighter text-white leading-[0.85] text-balance">
                Enterprise-Grade Engineering. <br class="hidden md:block"/>
                <span class="text-zinc-600">Performance Guaranteed.</span>
            </h1>
            <p class="text-lg md:text-xl text-zinc-400 max-w-2xl mx-auto font-light leading-relaxed mt-8 text-balance">
                I build lightning-fast, highly secure, and reliable websites tailored exactly to your vision—without the bloated agency price tag.
            </p>
            
            <div class="flex flex-col sm:flex-row items-center justify-center gap-4 pt-8">
                <a href="#quick-contact" class="w-full sm:w-auto">
                    <Button variant="primary" className="w-full sm:w-auto">Start Your Project</Button>
                </a>
                <a href="/services" class="w-full sm:w-auto">
                    <Button variant="secondary" className="w-full sm:w-auto">View Capabilities</Button>
                </a>
            </div>
        </div>
    </section>

    <section class="grid grid-cols-1 md:grid-cols-3 md:grid-rows-[auto_auto] gap-4 md:gap-6 z-10 relative">
        
        <BentoCard className="md:col-span-2 md:row-span-2 min-h-[400px] flex flex-col justify-between" hover={true}>
            <div class="flex justify-between items-start mb-8">
                <div class="w-12 h-12 rounded-full bg-white/5 border border-white/10 flex items-center justify-center">
                    <Zap size={20} class="text-white" aria-hidden="true" />
                </div>
                <a href="/projects" aria-label="View technical case studies" class="w-10 h-10 rounded-full border border-white/10 flex items-center justify-center hover:bg-white hover:text-black transition-colors">
                    <ArrowUpRight size={18} aria-hidden="true" />
                </a>
            </div>
            
            <div>
                <span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-4">Performance Optimization</span>
                <h2 class="text-3xl md:text-5xl font-bold text-white tracking-tighter leading-[1.1] mb-4">
                    From Sluggish to <br class="hidden md:block"/> Lightning Fast.
                </h2>
                <p class="text-zinc-400 font-light max-w-md leading-relaxed">
                    Speed is SEO. I specialize in diving into messy, heavy codebases and refactoring them for maximum efficiency—taking a client's native Google Lighthouse score from a failing 40 to a near-perfect 100.
                </p>
            </div>
        </BentoCard>

        <BentoCard className="md:col-span-1">
            <div class="w-10 h-10 rounded-full bg-white/5 border border-white/10 flex items-center justify-center mb-6">
                <ShieldCheck size={18} class="text-zinc-300" aria-hidden="true" />
            </div>
            <span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-4">Client Success</span>
            <h3 class="text-2xl font-bold text-white tracking-tighter mb-3">Trustworthy Services.</h3>
            <p class="text-zinc-400 font-light text-sm leading-relaxed mb-6">
                Whether executing massive technical overhauls for an E-commerce website or building complex templates for a Business Portfolio Website, I deliver architectures that help businesses scale.
            </p>
            <a href="/projects" class="text-sm font-medium text-white flex items-center gap-2 hover:gap-3 transition-all">
                View case studies <ArrowRight size={16} class="text-zinc-500" aria-hidden="true" />
            </a>
        </BentoCard>

        <BentoCard className="md:col-span-1">
            <span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-4">The Developer</span>
            <h3 class="text-2xl font-bold text-white tracking-tighter mb-3">Hi, I'm John.</h3>
            <p class="text-zinc-400 font-light text-sm leading-relaxed mb-6">
                I'm a hybrid web developer and AI engineer. I believe that top-tier web engineering shouldn't be locked behind massive corporate budgets. Let's translate your complex problems into simple digital solutions.
            </p>
            <a href="/about" class="text-sm font-medium text-white flex items-center gap-2 hover:gap-3 transition-all">
                Read my story <ArrowRight size={16} class="text-zinc-500" aria-hidden="true" />
            </a>
        </BentoCard>

    </section>

    <section id="quick-contact" class="max-w-2xl mx-auto pt-24 z-10 relative">
        <div class="text-center mb-10">
            <h2 class="text-4xl md:text-5xl font-bold text-white tracking-tighter mb-4">Let's build something great.</h2>
            <p class="text-zinc-400 font-light">Tell me about your vision. I'll get back to you within 24 hours with a transparent, accessible plan.</p>
        </div>

        <form onsubmit={handleFormSubmit} class="space-y-6">
            <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
            <input type="checkbox" name="botcheck" class="hidden" style="display: none;">

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="space-y-2">
                    <label for="name" class="text-xs font-mono text-zinc-500 uppercase tracking-widest block">Name</label>
                    <input type="text" id="name" name="name" required class="w-full bg-transparent border-b border-white/20 pb-2 text-white focus:outline-none focus:border-white transition-colors rounded-none placeholder:text-zinc-700" placeholder="Enter Your Name">
                </div>
                <div class="space-y-2">
                    <label for="email" class="text-xs font-mono text-zinc-500 uppercase tracking-widest block">Email</label>
                    <input type="email" id="email" name="email" required class="w-full bg-transparent border-b border-white/20 pb-2 text-white focus:outline-none focus:border-white transition-colors rounded-none placeholder:text-zinc-700" placeholder="Enter Your E-mail">
                </div>
            </div>

            <div class="space-y-2">
                <label for="message" class="text-xs font-mono text-zinc-500 uppercase tracking-widest block">How can I help you?</label>
                <textarea id="message" name="message" required rows="3" class="w-full bg-transparent border-b border-white/20 pb-2 text-white focus:outline-none focus:border-white transition-colors rounded-none resize-none placeholder:text-zinc-700" placeholder="I need a blazing fast WordPress site..."></textarea>
            </div>

            <div class="pt-4 flex items-center justify-between">
                <Button type="submit" variant="primary" className="w-full md:w-auto">
                    {isSubmitting ? 'Sending...' : 'Initiate Request'}
                </Button>
            </div>
        </form>
    </section>

</div>