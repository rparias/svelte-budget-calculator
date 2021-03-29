<script>
    import Title from './Title.svelte';
    import Button from './Button.svelte';
</script>

<section class="form">
    <Title title="Add Expense" />
    <form class="expense-form">
        <div class="form-control">
            <label for="name">Name</label>
            <input id="name" type="text">
        </div>
        <div class="form-control">
            <label for="amount">Amount</label>
            <input id="amount" type="number">
        </div>
        <p class="form-empty">Please fill out all form fields</p>
        <Button title="Add Expense" styleClass="btn btn-block" typeButton="submit" />
        <Button title="Close" styleClass="close-btn" iconClass="fas fa-times" />
    </form>
</section>