<script>
    import { getContext } from "svelte";
    import SectionTitle from "./Title.svelte";
    import Expense from "./Expense.svelte";

    export let expenses = [];

    const clearExpenses = getContext('clear');
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
    {#if expenses.length > 0}
        <button type="button" class="btn btn-primary btn-block" on:click={clearExpenses}>
            Clear Expenses
        </button>
    {/if}
</section>

<style>
    h3 {
        text-transform: uppercase;
    }
</style>
