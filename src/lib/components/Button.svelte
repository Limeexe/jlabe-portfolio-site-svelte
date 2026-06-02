<script lang="ts">
    import type {Snippet} from 'svelte';
    import type {MouseEventHandler} from 'svelte/elements';

    //Interface for props
    interface ButtonProps {
        variant?: 'primary'|'secondary';
        className?: string;
        type?: 'button'|'submit'|'reset';
        disabled?: boolean;
        children?: Snippet;
        onclick?: MouseEventHandler<HTMLButtonElement>;
    }

    let {
        variant = 'primary',
        className = '',
        type = 'button',
        disabled = false,
        children,
        onclick
    }: ButtonProps = $props();

    const baseStyle = "group relative inline-flex items-center justify-center px-7 py-3.5 rounded-full font-medium transition-all duration-400 ease-out overflow-hidden disabled:opacity-50 disabled:cursor-not-allowed disabled:pointer-events-none";

    let variantStyle = $derived(
        variant === 'primary'
                ? "text-black bg-white hover:scale-[1.02] active:scale-[0.98]"
                : "text-white bg-transparent border border-white/20 hover:border-white/5 active:scale-[0.98]"
    );
</script>

<button {type} {onclick} class="{baseStyle} {variantStyle} {className}">
    <span class="relative z-10 flex items-center justify-center gap-2">
        {#if children}
            {@render children()}
        {/if}
    </span>
</button>