<script>
    import SectionTitle from "./Title.svelte";
    import Expense from "./Expense.svelte";

    export let expenses = [];
</script>

<section>
    <SectionTitle title="Expense list" />
    <ul>
        {#each expenses as expense, index}
            <Expense {...expense} />
        {:else}
            <h3>No expenses added to the list</h3>
        {/each}
    </ul>
</section>

<style>
    h3 {
        text-transform: uppercase;
    }
</style>
