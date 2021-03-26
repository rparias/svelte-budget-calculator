<script>
    import TotalsTitle from "./Title.svelte";

    export let total = 0;
</script>

<section>
    <TotalsTitle title={`Total expenses: $${total}`} />
</section>