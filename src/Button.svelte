<script>
    export let title = "default title";
    export let styleClass = "btn btn-primary btn-block"
    export let typeButton = "button";
    export let onClick;
    export let iconClass;
</script>

<button type={typeButton} class={styleClass} on:click={onClick}>
    {#if iconClass}
        <i class={iconClass}></i>
    {/if}
    {title}
</button>