<script>
    import SectionTitle from "./Title.svelte";
    import Expense from "./Expense.svelte";

    export let expenses = [];
    export let removeExpense;
</script>

<section>
    <SectionTitle title="Expense list" />
    <ul>
        {#each expenses as expense, index}
            <Expense {...expense} {removeExpense} />
        {:else}
            <h3>Currently you have no expenses</h3>
        {/each}
    </ul>
</section>

<style>
    h3 {
        text-transform: uppercase;
    }
</style>
