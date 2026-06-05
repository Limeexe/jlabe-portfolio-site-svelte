<script lang="ts">
	import {Brain,Zap,Smartphone,Globe,Code,Wrench,ArrowRight,Layers,Database,ShoppingCart,Network,Cpu,ChevronLeft,ChevronRight} from 'lucide-svelte';

	interface ServiceProps{
		navigate: (page:string)=>void;
	}

	let {navigate}:ServiceProps=$props();

	const services=[
		{
            title: "SvelteKit Migration Architecture",
            description: "Seamless migration from heavy React monolithic applications to blazing-fast, Server-Side Rendered (SSR) SvelteKit architectures.",
            icon: Layers,
            category: "Architecture",
            basePriceUsd: 399
        },
		{
			title:"Custom WordPress Development",
			description:"Delivering fast, bespoke WordPress solutions. I combine deep expertise in Elementor and Yootheme Pro with custom coding to build high-performing websites that are powerful on the front-end and incredibly easy for your team to manage.",
			icon:Globe,
			category:"Web Dev",
			basePriceUsd: 199
		},
		{
			title:"Front-End Architecture & Optimization",
			description:"Website feeling sluggish? I untangle complex codebases and fix performance bottlenecks so your site loads instantly and runs flawlessly.",
			icon:Zap,
			category:"Performance",
			basePriceUsd: 149
		},
		{
			title:"Conversational AI & NLP Engineering",
			description:"Smart, fast, and private AI solutions. I train custom text-analysis models and deploy them directly into your users' browsers—cutting your server costs and delivering instant, privacy-first results.",
			icon:Brain,
			category:"Machine Learning",
			basePriceUsd: 499
		},
		{
			title:"Digital Experience Design",
			description:"Stop losing mobile users to clunky layouts. I execute complete architectural redesigns focused on mobile usability, ensuring your digital experience is intuitive, engaging, and highly converting on any screen.",
			icon:Smartphone,
			category:"Design",
			basePriceUsd: 299
		},
		{
			title:"Legacy System Modernization",
			description:"Stabilizing and modernizing heavy legacy web applications. I dive into the core code to optimize time complexity and eliminate bottlenecks, transforming fragile, slow-performing systems into robust, scalable assets.",
			icon:Code,
			category:"Engineering",
			basePriceUsd: 249
		},
		{
			title:"Site Reliability & Support (SRE)",
			description:"Enterprise-grade site reliability for local businesses. Through ongoing technical retainers, I actively monitor, debug, and maintain your digital infrastructure to guarantee continuous high-availability and zero downtime.",
			icon:Wrench,
			category:"Support",
			basePriceUsd: 49
		},
		{
            title:"Proprietary LLM Fine-Tuning",
            description:"Fine-tuning open-source LLMs on your proprietary data. Delivering highly accurate, domain-specific AI models deployed securely on your infrastructure.",
            icon:Brain,
            category:"Machine Learning",
            basePriceUsd: 899
        },
		{
            title:"Automated Data Pipelines",
            description:"Designing robust ETL pipelines. Automating the flow of unstructured business data into clean, structured databases ready for machine learning.",
            icon: Database,
            category:"Data Engineering",
            basePriceUsd: 349
        },
        {
            title:"Headless Checkout Optimization",
            description:"Decoupling traditional e-commerce backends to build ultra-fast, custom checkout experiences to drastically reduce cart abandonment.",
            icon:ShoppingCart,
            category:"E-Commerce",
            basePriceUsd: 449
        },
        {
            title:"Intelligent API Microservices",
            description:"Architecting secure REST and GraphQL APIs. Breaking down fragile monoliths into resilient microservices to integrate with modern AI toolchains.",
            icon:Network,
            category:"Backend Systems",
            basePriceUsd: 299
        },
        {
            title:"Edge-Native Personalization",
            description:"Implementing edge-computed middleware to deliver real-time, personalized web experiences without sacrificing Lighthouse performance.",
            icon:Cpu,
            category:"Edge Computing",
            basePriceUsd: 249
        }
	];

	// Pagination State & Logic
	let currentPage=$state(1);
	const itemsPerPage=6;

	let totalPages=$derived(Math.ceil(services.length/itemsPerPage));

	let visibleServices=$derived(services.slice((currentPage-1)*itemsPerPage, currentPage*itemsPerPage));

	const nextPage=()=>{
		if(currentPage<totalPages) currentPage++;
	};

	const prevPage=()=>{
		if(currentPage>1) currentPage--;
	};

	// Localization of currency & Logic
	let userCurrency=$state('USD');
	let exchangeRate=$state(1);
	let isLoadingPricing=$state(true);
	let priceFormatter=$derived(
		new Intl.NumberFormat(undefined,{
			style:'currency',
			currency:userCurrency,
			maximumFractionDigits:0
		})
	);

	$effect(()=>{
		const fetchPricingData=async()=>{
			try{
				const geoRes=await fetch('https://ipapi.co/json/');
				const geoData=await geoRes.json();

				if(geoData.currency){
					userCurrency=geoData.currency;
				}

				if(userCurrency!=='USD'){
					const rateRes=await fetch('https://open.er-api.com/v6/latest/USD');
					const rateData=await rateRes.json();
					if(rateData.rates[userCurrency]){
						exchangeRate=rateData.rates[userCurrency];
					}
				}
			}catch(error){
				console.error("Localization failed. Defaulting to USD.", error);
			}finally{
				isLoadingPricing=false;
			}
		};
		fetchPricingData();
	});

	const formatPrice=(baseUsd:number)=>{
		const converted = baseUsd*exchangeRate;
		return priceFormatter.format(converted);
	};

	// SEO

	const schemaData={
		"@context": "https://schema.org",
        "@type": "Service",
		"name": "JLAbe's Digital Essential",
		"description":"Enterprise-grade web application development, AI integration, software architecture, and technical consulting services.",
        "serviceType": "Enterprise Web Engineering and AI Integration",
        "provider": {
            "@type": "Person",
            "name": "John Louie Abenir",
			"jobTitle": "Freelance Software Engineer",
			"url":"https://jlabe-ph-freelance-developer.pages.dev",
			"sameAs": [
				"http://www.linkedin.com/in/john-louie-abenir-921883176",
				"https://github.com/Limeexe"
			],
            "address": {
                "@type": "PostalAddress",
                "addressRegion": "Bicol",
                "addressCountry": "Philippines"
            }
        },
        "hasOfferCatalog": {
            "@type": "OfferCatalog",
            "name": "Technical Services 2026",
            "itemListElement": services.map((service) => ({
                "@type": "Offer",
                "itemOffered": {
                    "@type": "Service",
                    "name": service.title,
                    "description": service.description
                },
                "priceCurrency": "USD",
                "price": service.basePriceUsd
            }))
        }
	};
</script>

<svelte:head>
    <title>JLAbe High Performance Development & AI | Philippines</title>
	<meta name="description" content="Freelance Hybrid Developer and AI Engineer in the Philippines. Specializing in zero-cost edge architecture, mobile-first development, and Performance Optimization" />
	<meta name="robots" content="index, follow" />
	{@html `<script type="application/ld+json">${JSON.stringify(schemaData)}</script>`}
</svelte:head>

<section class="space-y-12 animate-reveal pb-24 pt-24" aria-label="Services and Capabilities">
    <div class="max-w-2xl">
        <h2 class="text-5xl md:text-6xl font-bold text-white tracking-tighter leading-[0.9] mb-6">Capabilities.</h2>
        <p class="text-xl text-zinc-400 font-light leading-relaxed">
            A hybrid offering of high-performance web engineering and applied artificial intelligence. Premium capabilities tailored at highly disruptive global rates.
        </p>
    </div>

    <!-- Active Page Roster -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 pt-8 min-h-[500px]">
        {#each visibleServices as service (service.title)}
            <article 
                class="bg-[#0a0a0a] border border-white/5 hover:border-white/20 rounded-3xl p-8 transition-all duration-500 group flex flex-col justify-between"
            >
                <div>
                    <header class="flex justify-between items-start mb-8">
                        <div class="w-12 h-12 rounded-full bg-white/5 border border-white/10 flex items-center justify-center group-hover:scale-110 group-hover:bg-white/10 transition-all duration-500">
                            <svelte:component this={service.icon} size={20} class="text-zinc-300 group-hover:text-white transition-colors" aria-hidden="true" />
                        </div>
                        <span class="text-[10px] font-mono text-zinc-600 uppercase tracking-widest">{service.category}</span>
                    </header>
                    
                    <h3 class="text-2xl font-bold text-white tracking-tighter mb-4">{service.title}</h3>
                    <p class="text-zinc-400 font-light leading-relaxed text-sm mb-6">
                        {service.description}
                    </p>
                </div>

                <div class="mt-auto pt-6 border-t border-white/5 flex items-center justify-between">
                    <div class="text-sm font-mono text-zinc-300">
                        {#if isLoadingPricing}
                            <span class="animate-pulse bg-white/10 text-transparent rounded px-2">Loading...</span>
                        {:else}
                            <span class="text-white font-medium">
                                Starts at {formatPrice(service.basePriceUsd)}
                            </span>
                        {/if}
                    </div>

                    <a
						href="/contact"
                        class="text-xs font-mono text-white flex items-center gap-2 uppercase tracking-widest hover:text-zinc-300 transition-colors opacity-0 group-hover:opacity-100 duration-500 focus:opacity-100"
                        aria-label="Initiate request for {service.title}"
                    >
                        Initiate <ArrowRight size={14} aria-hidden="true" />
                    </a>
                </div> 
            </article>
        {/each}
    </div> 

    <!-- Pagination Controls -->
    <nav class="flex items-center justify-between pt-8 border-t border-white/10" aria-label="Pagination Navigation">
        <span class="text-xs font-mono text-zinc-500 tracking-widest uppercase">
            Page {currentPage} of {totalPages}
        </span>
        
        <div class="flex items-center gap-4">
            <button 
                onclick={prevPage} 
                disabled={currentPage === 1}
                class="w-10 h-10 rounded-full border border-white/10 flex items-center justify-center text-zinc-400 hover:text-white hover:bg-white/5 transition-all disabled:opacity-30 disabled:cursor-not-allowed disabled:hover:bg-transparent"
                aria-label="Previous Page"
            >
                <ChevronLeft size={16} />
            </button>
            
            <button 
                onclick={nextPage} 
                disabled={currentPage === totalPages}
                class="w-10 h-10 rounded-full border border-white/10 flex items-center justify-center text-zinc-400 hover:text-white hover:bg-white/5 transition-all disabled:opacity-30 disabled:cursor-not-allowed disabled:hover:bg-transparent"
                aria-label="Next Page"
            >
                <ChevronRight size={16} />
            </button>
        </div>
    </nav>
</section>