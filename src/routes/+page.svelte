<script>
  	//import { onMount, onDestroy } from 'svelte';
    import { users } from '$lib/users.js'    
</script>


  <table class="table table-xs">
    <thead>
      <tr class="hidden md:table-row">
        <th>Name</th>
        <th>Username</th>
        <th>Email</th>
        <th>Website</th>
        <th>City</th>
        <th>Company</th>
      </tr>
      <tr class="table-row md:hidden">
        <th>Name<br>
            Username</th>
         <th>
            Email<br>
            Website
        </th>
        <th>City<br>
            Company
        </th>
      </tr>
    </thead>
    <tbody>
      {#each users as user}
        <tr class="hidden md:table-row">
          <td>{user.name}</td>
          <td>{user.username}</td>
          <td>{user.email}</td>
          <td>{user.website}</td>
          <td>{user.address.city}</td>
          <td>{user.company.name}</td>
        </tr>
        <tr class="table-row md:hidden">
          <td>{user.name}<br>
              {user.username}
          </td>
          <td>
              {user.email}<br>
              {user.website}
          </td>
          <td>{user.address.city}<br>
              {user.company.name}
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
