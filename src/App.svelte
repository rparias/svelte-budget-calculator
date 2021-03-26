<script>
	import { setContext } from "svelte";
	import Navbar from "./Navbar.svelte";
	import Button from "./Button.svelte";
	import ExpenseList from "./ExpenseList.svelte";

	import expensesData from "./expenses";

	let expenses = [...expensesData];

	function removeExpense(id) {
		expenses = expenses.filter(item => item.id !== id);
	}

	function clearExpenses() {
		expenses = [];
	}

	setContext('remove', removeExpense);
</script>

<Navbar />
<main class="content">
	<ExpenseList {expenses} />
	{#if expenses.length > 0}
		<Button title="Clear Expenses" onClick={clearExpenses} />
    {/if}
</main>
