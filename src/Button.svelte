<script>
    export let title = "default title";
    export let onClick;
</script>

<button type="button" class="btn btn-primary btn-block" on:click={onClick}>
    {title}
</button>