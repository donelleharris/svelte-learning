<script>
	import ContactCard from "./ContactCard.svelte";
	import Goal from "./Goal.svelte";

	let userName = "Donelle Harris";
	let age = 52;
	let course = "Svelte Basics";
	let jobTitle = "";
    let userBio = ""
    let userImage = "";
	let goal = "";
	let color = "";
	
	// function color(){
	// 	if(goal.includes('!')){
	// 		color = "red";
	// 	}
	// }

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

<h1>Hello! Welcome to {course}!</h1>
<Goal {goal}/> 
<!-- <button on:click="{incrementAge}">Change Age</button> -->
<!-- <button on:click="{changeName}">Change Name</button> -->
<div>
	<label for="userName">User Name</label>
	<input id="userName" type="text" bind:value="{userName}">
</div>
<div>
	<label for="title">Job Title</label>
	<input id="title" type="text" bind:value="{jobTitle}">
</div>
<div>
	<label for="description">User Bio</label>
	<input id="title" type="text" bind:value="{userBio}">
</div>
<div>
	<label for="image">Imgage URL</label>
	<input id="image" type="text" bind:value="{userImage}">
</div>
<div>
	<label for="goal">Goal Statement</label>
	<input id="goal" type="text" bind:value="{goal}">
</div>

<ContactCard 
	{userImage}
	{userName} 
	{jobTitle}
	{userBio}/>