<script>
    import { getContext } from "svelte";
    export let id;
    export let name = "";
    export let amount = 0;

    let displayAmount = false;

    function toggleAmount () {
        displayAmount = !displayAmount;
    }

    const removeExpense = getContext('remove');
    const setModifiedExpense = getContext('modify');
</script>

<article class="single-expense">
    <div class="expense-info">
        <h3>
            {name}
            <button class="amount-btn" on:click={toggleAmount}><i class="fas fa-caret-down" /></button>
        </h3>
        {#if displayAmount}
            <h4>amount: ${amount}</h4>
        {/if}
    </div>
    <div class="expense-buttons">
        <!-- arrow function to execute the method only once -->
        <button class="expense-btn edit-btn" on:click={() => setModifiedExpense(id)}>
            <i class="fas fa-pen" />
        </button>
        <button class="expense-btn delete-btn" on:click={() => removeExpense(id)}>
            <i class="fas fa-trash" />
        </button>
    </div>
</article>
