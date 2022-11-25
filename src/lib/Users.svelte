<script>
  import user1 from '../assets/images/vite.svg';
  import user2 from '../assets/images/group.png';
  import user3 from '../assets/images/man.png';
  import User from './User.svelte';
  import FilterUser from './FilterUser.svelte';
  import NewUser from './NewUser.svelte';
  
  let users = [
    {
    id: 1,
    name : "John doe",
    icon : user1,
    email: "john.doe@example.com",
    active: true,
  },
  {
    id: 2,
    name : "Muhammad doe",
    icon : user2,
    email: "Muhammad.doe@example.com",
    active: true,
  },
  {
    id: 3,
    name : "Hacker doe",
    icon : user3,
    email: "Hacker.doe@example.com",
    active: false,
  }
];

// reactivly update the variable
$: filteredUser = users;

const filter = (value) => {
  if(value.detail === 'null'){
      return filteredUser = users;
  }
  return filteredUser = users.filter((user)=> user.active === JSON.parse(value.detail.toLowerCase()))
  
}

const remove = ({detail}) => {
  users = users.filter((user) => user.id !== detail)
}
    
</script>
<div class="flex justify-between mx-4">
  <FilterUser on:filter={filter}/>

  <NewUser />
</div>

<div>
  <h1 class="text-2xl text-center mt-10">List of all users</h1>
  {#each filteredUser as user, i (user.id)}
  <User on:remove={remove} {user} i={i}/>
  {:else}
  <p>No User Found!!!</p>
  {/each}
</div>
    