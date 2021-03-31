<script>
    import Title from './Title.svelte';
    import Button from './Button.svelte';

    export let addExpense;

    export let name = '';
    export let amount = null;
    export let isEditing;
    export let editExpense;
    export let hideForm;

    $: isEmpty = !name || !amount;

    function handleSubmit() {
        if (isEditing) {
            editExpense({name, amount});
        } else {
            addExpense({name, amount});
        }
        name = '';
        amount = null;
    }
</script>

<section class="form">
    <Title title={isEditing ? 'Update Expense' : 'Add Expense'} />
    <form class="expense-form" on:submit|preventDefault={handleSubmit}>
        <div class="form-control">
            <label for="name">Name</label>
            <input id="name" type="text" bind:value={name}>
        </div>
        <div class="form-control">
            <label for="amount">Amount</label>
            <input id="amount" type="number" bind:value={amount}>
        </div>
        {#if isEmpty}
            <p class="form-empty">Please fill out all form fields</p>
        {/if}
        <Button title={isEditing ? 'Update Expense' : 'Add Expense'} styleClass="btn btn-block" typeButton="submit" isDisabled={isEmpty}/>
        <Button title="Close" styleClass="close-btn" iconClass="fas fa-times" onClick={hideForm} />
    </form>
</section>