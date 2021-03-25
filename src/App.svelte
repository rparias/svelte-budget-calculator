<script>
	import Navbar from './Navbar.svelte';
	import ExpenseList from './ExpenseList.svelte';

	import expensesData from './expenses';

	let expenses = [...expensesData];

	function removeExpense(id) {
		expenses = expenses.filter(item => item.id !== id);
	}
</script>

<Navbar />
<main class="content">
	<ExpenseList {expenses} {removeExpense}/>
</main>