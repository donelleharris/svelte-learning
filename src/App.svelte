<script>
import ContactCard from "./ContactCard.svelte";

	let name = "Donelle";
	let age = 52;
	function incrementAge(){
		age += 1;
	}
	function changeName(){
		name = "Marie";
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<button on:click="{changeName}">Change Name</button>
<input type="text" bind:value="{name}">

<ContactCard />