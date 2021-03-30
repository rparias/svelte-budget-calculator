<script>
    export let title = "default title";
    export let styleClass = "btn btn-primary btn-block";
    export let typeButton = "button";
    export let isDisabled = false;
    export let onClick;
    export let iconClass;
</script>

<button
    type={typeButton}
    class={styleClass}
    on:click={onClick}
    class:disabled={isDisabled}
    disabled={isDisabled}
>
    {#if iconClass}
        <i class={iconClass} />
    {/if}
    {title}
</button>
