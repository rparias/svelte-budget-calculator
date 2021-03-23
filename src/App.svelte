<script>
	import Navbar from './Navbar.svelte';
	import ExpenseList from './ExpenseList.svelte';

	import expensesData from './expenses';

	let expenses = [...expensesData];
</script>

<Navbar />
<main class="content">
	<ExpenseList {expenses}/>
</main>