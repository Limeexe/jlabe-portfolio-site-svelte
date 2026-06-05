<script lang="ts">
    import { User } from 'lucide-svelte';
    import profilePic from '$lib/assets/developer-profile.jpg';

    let imageUrl: string = profilePic;

    // --- Timeline Data Structure ---
    // Breaking your bio into semantic timeline events for high SEO readability
    const timelineEvents = [
        {
            period: "The Foundation",
            title: "From Nursing to Tech",
            content: "With a background in Computer Science and a journey from nursing to tech, I’ve learned one thing: real problems don’t come with ready-made fixes. They come with root causes — and I’m not afraid to dig deep.",
            color: "#09090b" // bg-zinc-950
        },
        {
            period: "The Engineering",
            title: "Root Cause Optimization",
            content: "I spent years refining my ability to locate issues at the core of a system — not just on the surface. Whether it’s optimizing a sluggish WordPress site or integrating AI into a user workflow, I focus on performance, scalability, and long-term stability. I’ve built custom AI models, refactored legacy code, and redesigned UIs with mobile-first thinking.",
            color: "#0f172a" // bg-slate-900
        },
        {
            period: "The Ethic",
            title: "Deliver What Matters",
            content: "Driven by a simple ethic: deliver what matters. I work with focus, discipline, and a clear sense of purpose. Whether I’m setting up a clean WordPress stack with Yootheme Pro or building a zero-cost Edge-Native app using Svelte, I build systems that respect your time, budget, and users’ experience.",
            color: "#171717" // bg-neutral-900
        },
        {
            period: "The Vision",
            title: "Technology for Impact",
            content: "I believe technology should serve people — not the other way around. That’s why I’m committed to making a real impact, especially through the UN’s Sustainable Development Goals. I want to help organizations and individuals turn their visions into reality — even if it takes time, effort, and a little patience.",
            color: "#052e16" // bg-green-950 (Subtle shift to represent sustainability/UN SDGs)
        }
    ];

    // Reactive state for the dynamic background color
    let activeColor = $state(timelineEvents[0].color);

    // --- High-Performance Intersection Observer ---
    // This Svelte action watches elements and changes the color only when they cross the middle of the screen.
    const observeSection = (node: HTMLElement, color: string) => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    activeColor = color;
                }
            });
        }, {
            // Triggers when the item hits the middle 40% of the viewport
            rootMargin: '-40% 0px -40% 0px' 
        });

        observer.observe(node);

        return {
            destroy() {
                observer.disconnect();
            }
        };
    };
</script>

<div 
    style="background-color: {activeColor}; transition: background-color 1s ease-out;" 
    class="min-h-screen w-full -mx-4 px-4 sm:-mx-8 sm:px-8 py-24 transition-colors duration-1000"
>
    <div itemscope itemtype="https://schema.org/Person" class="max-w-4xl mx-auto space-y-16">

        <header class="text-center md:text-left animate-reveal">
            <h2 class="text-5xl md:text-[5rem] font-bold text-white tracking-tighter leading-[0.9] mb-6">
                The Man Behind.
            </h2>
            <h3 class="text-2xl md:text-3xl font-light text-zinc-300 leading-snug text-balance">
                I don't just build things; <span class="font-bold text-white">I engineer high-performance solutions.</span>
            </h3>
        </header>

        <div class="border-t border-white/10 pt-16 grid grid-cols-1 md:grid-cols-12 gap-8 md:gap-16">
            
            <aside class="md:col-span-4 h-max md:sticky md:top-32 space-y-6 z-10">
                <div class="aspect-square rounded-3xl bg-zinc-900 border border-white/10 flex items-center justify-center overflow-hidden relative group shadow-2xl">
                    <div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500 z-10 pointer-events-none"></div>
                    
                    {#if imageUrl}
                        <img src={imageUrl} alt="Freelance Full-Stack Developer and AI-Engineer" itemprop="image" loading="lazy" decoding="async" class="w-full h-full object-cover object-top group-hover:scale-105 transition-transform duration-700"/>
                    {:else}
                        <User size={64} class="text-zinc-600 group-hover:scale-110 transition-transform duration-700"/>
                    {/if}
                </div>
                <div class="space-y-1">
                    <h3 class="text-white font-bold text-lg" itemprop="name">The Developer</h3>
                    <p class="text-zinc-400 font-mono text-xs uppercase tracking-widest" itemprop="jobTitle">Web | Software | AI Developer</p>
                </div>
            </aside>
            
            <div class="md:col-span-8 relative">
                <div class="absolute left-0 top-0 bottom-0 w-px bg-white/10 ml-[11px] md:ml-0 hidden sm:block"></div>

                <div class="space-y-24 pt-4 sm:pl-12">
                    {#each timelineEvents as event}
                        <section 
                            use:observeSection={event.color} 
                            class="relative group"
                        >
                            <div class="absolute -left-[41px] top-2 w-6 h-6 rounded-full bg-zinc-900 border-2 border-white/20 group-hover:border-white transition-colors duration-500 hidden sm:block"></div>
                            
                            <div class="space-y-4">
                                <span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block">
                                    {event.period}
                                </span>
                                <h4 class="text-3xl font-bold text-white tracking-tighter">
                                    {event.title}
                                </h4>
                                <p class="text-zinc-400 text-lg font-light leading-relaxed" itemprop="description">
                                    {event.content}
                                </p>
                            </div>
                        </section>
                    {/each}

                    <section class="pt-8 border-t border-white/10">
                        <p class="text-zinc-300 text-lg font-light italic leading-relaxed">
                            And if you're looking for a developer who doesn’t just deliver features — but <strong class="text-white font-semibold not-italic">delivers results</strong> — I’m here. <br /><br />
                            Because I am me. And I can help turn your vision into a reality — even if it takes a while to get there.
                        </p>
                    </section>
                </div>
            </div>
        </div>
    </div>
</div>