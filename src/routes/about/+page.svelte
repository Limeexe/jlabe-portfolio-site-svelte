<script lang="ts">
    import { User, Download, Terminal, Server, Database, Wrench } from 'lucide-svelte';
    import Icon from '@iconify/svelte';
    import profilePic from '$lib/assets/developer-profile.jpg';

    let imageUrl: string = profilePic;

    // --- 1. Original Narrative Content Formatted as an Alternating Timeline ---
    const timelineEvents = [
        {
            period: "The Foundation",
            title: "Computer Science & Analytical Roots",
            subtitle: "From Nursing to Tech",
            content: "With a bachelors degree in Computer Science I initially wanted to study medicine, which led me to choosing nursing as my primary choice for a degree, but when COVID-19 hit. Things happened and due to some reasons I had to let go of my first choice of course and shifted to computer science. I've always been fascinated with how tech works so shifting worked for me in the end.",
            color: "#0c0a09" // Very subtle warm stone/black shift
        },
        {
            period: "The Engineering",
            title: "Performance & Scalability",
            subtitle: "Root Cause Resolution",
            content: "I my time learning and refining my ability to locate issues at the core of a system — not just on the surface, I like them fast that's why. Whether it’s optimizing a sluggish and bloated WordPress site or integrating AI into a user workflow, I focus on performance, scalability, and long-term stability. I’ve built custom AI models, refactored legacy code, and redesigned UIs with mobile-first thinking — because a well developed product must always serve its intended purpose.",
            color: "#0f172a" // Deep slate gradient drop
        },
        {
            period: "The Ethic",
            title: "Core Execution Principles",
            subtitle: "Deliver What Matters",
            content: "Driven by a simple ethic: deliver what matters. I work with focus, discipline, and a clear sense of purpose. I build systems that respect your time, budget, and users’ experience.",
            color: "#18181b" // Deep zinc accent
        },
        {
            period: "The Vision",
            title: "Global Impact Architecture",
            subtitle: "Sustainable Development Goals",
            content: "I believe technology should serve our needs — not the other way around. That’s why I’m committed to making a real impact, especially through the UN’s Sustainable Development Goals. I want to help organizations and individuals turn their visions into reality — even if it takes time, effort, and a little patience.",
            color: "#022c22" // Deep emerald undertone highlighting sustainability focus
        }
    ];

    // --- 2. High-Performance Categorized Tech Stack (O(1) Scale-Safe) ---
    const techCategories = [
        {
            id: "frontend",
            name: "Frontend Stack",
            icon: Terminal,
            items: [
                { name: "SvelteKit", iconifyTag: "logos:svelte-icon" },
                { name: "TypeScript", iconifyTag: "vscode-icons:file-type-typescript-official" },
                { name: "Tailwind CSS", iconifyTag: "logos:tailwindcss-icon" },
                { name: "HTML5", iconifyTag: "vscode-icons:file-type-html" }
            ]
        },
        {
            id: "backend",
            name: "Backend & Systems",
            icon: Server,
            items: [
                { name: "Node.js", iconifyTag: "logos:nodejs-icon" },
                { name: "Python", iconifyTag: "logos:python" },
                { name: "REST APIs", iconifyTag: "eos-icons:api" }
            ]
        },
        {
            id: "data",
            name: "Databases & Storage",
            icon: Database,
            items: [
                { name: "PostgreSQL", iconifyTag: "logos:postgresql" },
                { name: "MySQL", iconifyTag: "logos:mysql-icon" },
                { name: "Redis", iconifyTag: "logos:redis" }
            ]
        },
        {
            id: "tools",
            name: "Engineering Ecosystem",
            icon: Wrench,
            items: [
                { name: "WordPress", iconifyTag: "logos:wordpress-icon" },
                { name: "Yootheme Pro", iconifyTag: "tabler:brand-webflow" },
                { name: "Git", iconifyTag: "logos:git-icon" },
                { name: "Elementor", iconifyTag: "logos:elementor" }
            ]
        }
    ];

    // --- 3. Reactive State Management ---
    let scrolledPast100 = $state(false);
    let activeSectionColor = $state(timelineEvents[0].color);
    
    // Calculates the final dynamic background safely based on layout state
    let computedBackground = $derived(scrolledPast100 ? activeSectionColor : '#050505');

    // Action tracking the 100px mark down from top of layout
    const setupTopSentinel = (node: HTMLElement) => {
        const observer = new IntersectionObserver(([entry]) => {
            scrolledPast100 = !entry.isIntersecting && entry.boundingClientRect.top < 0;
        }, { root: null, threshold: 0 });

        observer.observe(node);
        return { destroy() { observer.disconnect(); } };
    };

    // Action tracking visual intersections inside the timeline track
    const observeTimelineColor = (node: HTMLElement, targetColor: string) => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    activeSectionColor = targetColor;
                }
            });
        }, { rootMargin: '-40% 0px -40% 0px' });

        observer.observe(node);
        return { destroy() { observer.disconnect(); } };
    };

    // --- 4. Flattening Tech Stack dynamically for structural Schema markup ---
    const structuralSkillsList = techCategories.flatMap(cat => cat.items.map(i => i.name));
    
    const schemaData = {
        "@context": "https://schema.org",
        "@type": "AboutPage",
        "mainEntity": {
            "@type": "Person",
            "name": "JLAbe",
            "image": imageUrl,
            "jobTitle": "Freelance Full-Stack Developer & AI-Engineer",
            "nationality": { "@type": "Country", "name": "Philippines" },
            "description": "Specializing in zero-cost edge architectures, high-performance data refactoring, and custom NLP implementations.",
            "knowsAbout": structuralSkillsList
        }
    };
</script>

<svelte:head>
    {@html `<script type="application/ld+json">${JSON.stringify(schemaData)}</script>`}
</svelte:head>

<div use:setupTopSentinel class="absolute top-[100px] left-0 right-0 h-px pointer-events-none z-0"></div>

<div 
    style="background-color: {computedBackground};" 
    class="relative min-h-screen w-full -mx-4 px-4 sm:-mx-8 sm:px-8 pb-24 pt-12 transition-colors duration-1000 ease-out overflow-hidden"
>
    <div class="fixed inset-0 bg-[linear-gradient(to_bottom,rgba(5,5,5,0.8),transparent)] pointer-events-none z-0"></div>

    <div itemscope itemtype="https://schema.org/Person" class="relative z-10 max-w-4xl mx-auto space-y-24">
        
        <header class="text-center md:text-left space-y-6">
            <h2 class="text-5xl md:text-[5rem] font-bold text-white tracking-tighter leading-[0.9]">The Man Behind.</h2>
        </header>

        <div class="border-t border-white/10 pt-12">
            <div class="grid grid-cols-1 md:grid-cols-12 gap-12 md:gap-16 items-start">
                
                <aside class="md:col-span-4 space-y-6 md:sticky md:top-28 z-10">
                    <div class="aspect-square rounded-3xl bg-zinc-900 border border-white/10 flex items-center justify-center overflow-hidden relative group shadow-2xl">
                        <div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500 z-10 pointer-events-none"></div>
                        
                        {#if imageUrl}
                            <img src={imageUrl} alt="Freelance Full-Stack Developer and AI-Engineer" itemprop="image" loading="lazy" decoding="async" class="w-full h-full object-cover object-top group-hover:scale-105 transition-transform duration-700"/>
                        {:else}
                            <User size={64} class="text-zinc-600" />
                        {/if}
                    </div>
                    <div class="space-y-1 text-center md:text-left">
                        <h3 class="text-white font-bold text-lg" itemprop="name">JLAbe</h3>
                        <p class="text-zinc-500 font-mono text-xs uppercase tracking-widest" itemprop="jobTitle">Web | Software | AI Developer</p>
                    </div>
                </aside>
                
                <div class="md:col-span-8 relative">
                    <div class="absolute left-4 md:left-6 top-0 bottom-0 w-px bg-white/10 hidden sm:block"></div>

                    <div class="space-y-16 sm:pl-16">
                        <h3 class="text-2xl md:text-3xl font-light text-white leading-snug text-balance">
                            I don't just build things; <br/> <span class="font-bold text-emerald-400">I engineer high-performance solutions.</span>
                        </h3>

                        {#each timelineEvents as event (event.title)}
                            <section 
                                use:observeTimelineColor={event.color}
                                class="relative group space-y-3"
                            >
                                <div class="absolute -left-[53px] top-1.5 w-3 h-3 rounded-full bg-zinc-900 border border-white/30 group-hover:border-emerald-400 group-hover:bg-emerald-500 transition-all duration-500 hidden sm:block"></div>
                                
                                <header>
                                    <span class="text-xs font-mono text-zinc-500 uppercase tracking-widest block mb-1">{event.period}</span>
                                    <h4 class="text-xl font-bold text-white tracking-tight">{event.title}</h4>
                                    <span class="text-xs font-mono text-emerald-400/80 tracking-wide block">{event.subtitle}</span>
                                </header>
                                <p class="text-zinc-400 text-base font-light leading-relaxed" itemprop="description">
                                    {event.content}
                                </p>
                            </section>
                        {/each}

                        <section use:observeTimelineColor={'#050505'} class="pt-8 border-t border-white/5 space-y-4">
                            <p class="text-zinc-400 text-base font-light leading-relaxed">
                                And if you're looking for a developer who doesn’t just deliver features — but <strong class="text-white font-semibold">delivers results</strong> — I’m here.  
                            </p>
                            <p class="text-zinc-300 italic text-base font-light">
                                Because I am me. And I can help turn your vision into a reality — even if it takes a while to get there.
                            </p>
                        </section>
                    </div>
                </div>

            </div>
        </div>

        <section aria-label="Technical Ecosystem Matrix" class="border-t border-white/10 pt-20 space-y-16">
            <div class="max-w-xl">
                <h3 class="text-3xl font-bold text-white tracking-tight">Technical Architecture & Stack</h3>
                <p class="text-sm text-zinc-500 font-light mt-2">Highly responsive tools and frameworks compiled for low latency and zero resource waste.</p>
            </div>

            <div class="space-y-12">
                {#each techCategories as category (category.id)}
                    <div class="grid grid-cols-1 md:grid-cols-12 gap-4 md:gap-8 items-start group">
                        
                        <div class="md:col-span-3 flex items-center gap-3 py-2">
                            <svelte:component this={category.icon} size={16} class="text-zinc-600 group-hover:text-emerald-400 transition-colors duration-300" />
                            <h4 class="text-xs font-mono text-zinc-500 uppercase tracking-widest group-hover:text-zinc-300 transition-colors duration-300">{category.name}</h4>
                        </div>

                        <div class="md:col-span-9 grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-3">
                            {#each category.items as item (item.name)}
                                <div class="flex items-center gap-3 p-3 rounded-xl border border-white/5 bg-black/20 hover:border-white/10 hover:bg-white/5 transition-all duration-300">
                                    <div class="w-5 h-5 flex items-center justify-center text-lg filter drop-shadow">
                                        <Icon icon={item.iconifyTag} />
                                    </div>
                                    <span class="text-sm font-medium text-zinc-300 group-hover:text-white transition-colors">{item.name}</span>
                                </div>
                            {/each}
                        </div>

                    </div>
                {/each}
            </div>
        </section>

    </div>
</div>