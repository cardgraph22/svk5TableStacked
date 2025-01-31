<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<script>
  	import { onMount, onDestroy } from 'svelte';
    import { users } from '$lib/users.js'    

    let mqu = $state('dsk');
  
  onMount(() => {
		console.log('the component has mounted');
    const mediaQuery = window.matchMedia("(width > 768px)");
    // Run the function initially
    handleBreakpointChange(mediaQuery);
    // Add a listener to re-run the function when the breakpoint changes
    mediaQuery.addEventListener("change", handleBreakpointChange);
	});
  onDestroy(() => {
		console.log('the component is being destroyed');
    if(typeof mediaQuery !== 'undefined')mediaQuery.removeEventListener("change", handleBreakpointChange);
	});
  function handleBreakpointChange(mediaQuery) {
    if (mediaQuery.matches) {
      // The breakpoint matches, run your function here
      console.log("Breakpoint reached! width > 768px"); 
      mqu = 'dsk'
    } else {
      // The breakpoint does not match
      console.log("The breakpoint does not match width <= 768p"); 
      mqu = 'phn'
    }
  }
</script>

<div class="overflow-x-auto">
  <table class="table table-xs">
    <thead>
      {#if mqu === 'dsk'}
        <tr>
          <th>Name</th>
          <th>Username</th>
          <th>Email</th>
          <th>Website</th>
          <th>City</th>
          <th>Company</th>
        </tr>
      {:else if mqu === 'phn'}
        <tr>
          <th>Person</th>
          <th>City</th>
          <th>Company</th>
        </tr>
      {/if}
    </thead>
    <tbody>
      {#each users as user}
       {#if mqu === 'dsk'}
          <tr>
            <td>{user.name}</td>
            <td>{user.username}</td>
            <td>{user.email}</td>
            <td>{user.website}</td>
            <td>{user.address.city}</td>
            <td>{user.company.name}</td>
          </tr>
        {:else if mqu === 'phn'}
          <tr>
            <td>Nane: {user.name}<br>
                Username: {user.username}<br>
                Email: {user.email}<br>
                Website: {user.website}</td>
          <td>{user.address.city}</td>
          <td>{user.company.name}</td>
          </tr>
        {/if}
      {/each}
    </tbody>
  </table>
</div>