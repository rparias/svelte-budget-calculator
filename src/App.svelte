<script>
	import { setContext, onMount, afterUpdate } from "svelte";
	import Navbar from "./Navbar.svelte";
	import Button from "./Button.svelte";
	import Totals from "./Totals.svelte";
	import ExpenseList from "./ExpenseList.svelte";
	import ExpenseForm from "./ExpenseForm.svelte";

	import expensesData from "./expenses";

	// let expenses = [...expensesData];
	let expenses = [];

	let setId = null;
	let setName = '';
	let setAmount = null;

	let isFormOpen = false;
	
	$: isEditing = setId ? true : false;
	$: total = expenses.reduce((accumulator, currentExpense) => {
		return accumulator + currentExpense.amount;
	}, 0);

	function removeExpense(id) {
		expenses = expenses.filter(item => item.id !== id);
	}

	function clearExpenses() {
		expenses = [];
	}

	function addExpense({name, amount}) {
		let expense = {
            id: Math.random() * Date.now(),
            name,
            amount,
        };
		expenses.unshift(expense);
		expenses = expenses;
	}

	function setModifiedExpense(id) {
		let expense = expenses.find(item => item.id === id);
		setId = expense.id;
		setName = expense.name;
		setAmount = expense.amount;
		showForm();
	}

	function editExpense ({name, amount}) {
		expenses = expenses.map(item => item.id === setId ? {...item, name, amount} : {...item});
		clearForm();
	}

	function showForm() {
		isFormOpen = true;
	}

	function hideForm() {
		isFormOpen = false;
		clearForm();
	}

	function clearForm() {
		setId = null;
		setName = '';
		setAmount = null;
	}

	setContext('remove', removeExpense);
	setContext('modify', setModifiedExpense);

	function setLocalStorage() {
		localStorage.setItem('expenses', JSON.stringify(expenses));
	}

	onMount(() => {
		expenses = localStorage.getItem('expenses')
		? JSON.parse(localStorage.getItem('expenses'))
		: [];
	});

	afterUpdate(() => {
		//This will be executed after each update on the App, needed to be careful
		setLocalStorage();
	});
</script>

<Navbar {showForm} />
<main class="content">
	{#if isFormOpen}
		<ExpenseForm {addExpense} name={setName} amount={setAmount} {isEditing} {editExpense} {hideForm}/>	
	{/if}
	<Totals total={total.toFixed(2)} />
	<ExpenseList {expenses} />
	{#if expenses.length > 0}
		<Button title="Clear Expenses" onClick={clearExpenses} />
    {/if}
</main>
