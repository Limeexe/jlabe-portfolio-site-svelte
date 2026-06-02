<script lang="ts">
    import { User } from 'lucide-svelte';

    import profilePic from '$lib/assets/developer-profile.jpg';

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
                        With a background in Computer Science and a journey from nursing to tech, I’ve learned one thing: real problems don’t come with ready-made fixes. They come with root causes — and I’m not afraid to dig deep.
                    </p>
                    <p>
                        I spent years refining my ability to locate issues at the core of a system — not just on the surface. Whether it’s optimizing a sluggish WordPress site or integrating AI into a user workflow, I focus on performance, scalability, and long-term stability. I’ve built custom AI models, refactored legacy code, and redesigned UIs with mobile-first thinking — all with precision and clarity.
                    </p>
                    <p>
                        Driven by a simple ethic: <strong>deliver what matters</strong>. I work with focus, discipline, and a clear sense of purpose. Whether I’m setting up a clean WordPress stack with Yoostheme Pro or building a zero-cost Edge-Native app using Svelte, I build systems that respect your time, budget, and users’ experience.
                    </p>
                    <p>
                        I believe technology should serve people — not the other way around. That’s why I’m committed to making a real impact, especially through the <strong>UN’s Sustainable Development Goals</strong>. I want to help organizations and individuals turn their visions into reality — even if it takes time, effort, and a little patience.
                    </p>
                    <p>
                        And if you're looking for a developer who doesn’t just deliver features — but <strong>delivers results</strong> — I’m here.  
                        <br /><em>Because I am me. And I can help turn your vision into a reality — even if it takes a while to get there.</em>
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>