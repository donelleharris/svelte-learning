<script>
	import ContactCard from "./ContactCard.svelte";
	import Goal from "./Goal.svelte";

	let userName = "";
	let jobTitle = "";
    let userBio = ""
    let userImage = "";
	let password = "";
	
	let createdContacts = [];

	let formState = 'empty';
	let pwMessage = 'Passwords must be between 5 & 10 characters';
	function pwCheck(){
		
	}
	function addContact(){
		if(userName.trim().length == 0 || 
		password.trim().length == 0 ||
		jobTitle.trim().length == 0 || 
		userImage.trim().length == 0 || 
		userBio.trim().length == 0 ) {
			formState = 'invalid';
			return;
		}
		if (password != '' && password.length < 5){
			pwMessage = 'Password too short';
			formState = 'invalid';
			return;
		}else if (password.length > 10){
			pwMessage = 'Password too long';
			formState = 'invalid';
			return;
		}
		createdContacts = [
			...createdContacts, 
			{
			id: Math.random(),
			name: userName,
			password: password, 
			title: jobTitle, 
			image: userImage, 
			bio: userBio
			}
		];
		formState = 'done';
	}
	function deleteFirst(){
		createdContacts = createdContacts.slice(1);
	}
	function deleteLast(){
		createdContacts = createdContacts.slice(0, -1);
	}
</script>

<style>
	#form {
		width: 30rem;
		max-width: 100%;
  	}
</style>

<div id="form">
	<div class="form-control">
	  <label for="userName">User Name: </label>
	  <input type="text" bind:value={userName} id="userName" />
	</div>
	<div class="form-control">
		<label for="password">Password: </label>
		<input type="text" bind:value={password} id="password" />
	  </div>
	<div class="form-control">
	  <label for="jobTitle">Job Title: </label>
	  <input type="text" bind:value={jobTitle} id="jobTitle" />
	</div>
	<div class="form-control">
	  <label for="image">Image URL: </label>
	  <input type="text" bind:value={userImage} id="image" />
	</div>
	<div class="form-control">
	  <label for="desc">Description: </label>
	  <textarea rows="3" bind:value={userBio} id="desc" />
	</div>
  </div>

<button on:click="{addContact}">Add Contact Card</button>
<button on:click="{deleteFirst}">Delete First</button>
<button on:click="{deleteLast}">Delete Last</button>


{#if formState === 'invalid'}
  <p>Invalid input. </p>
  <p> {pwMessage}</p>
{:else}
  <p>Please enter your information in the form above.</p>
{/if}
{#each createdContacts as contact, i (contact.id)}
  <h2># {i + 1}</h2>
  <ContactCard
  	userImage={contact.image}
	userName={contact.name}
	password={contact.password}
	jobTitle={contact.title}
  	userBio={contact.bio}
  />
{/each}
