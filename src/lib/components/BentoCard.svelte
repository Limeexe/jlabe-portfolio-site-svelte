<script lang="ts">
    import type {Snippet} from 'svelte';
    interface BentoCardProps{
        className?: string;
        hover?: boolean;
        children?: Snippet;
    }
    let {
        className = '',
        hover = true,
        children
    }: BentoCardProps = $props();
</script>
<div class="bg-[#0d0d0d] border-white/5 rounded-3x1 p-8 md:p-10 transition-all duration-500 relative overflow-hidden group {hover? 'hover:bg-[#121212] hover:border-white/10':''} {className}">
    {#if hover}
        <div class="absolute inset-0 bg-linear-to-br from-white/3 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 rounded-3xl"></div>
    {/if}

    <div class="relative z-10 h-full flex flex-col">
        {#if children}
            {@render children()}
        {/if}
    </div>
</div>