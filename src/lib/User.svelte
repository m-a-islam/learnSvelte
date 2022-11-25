<script>
  import { createEventDispatcher } from "svelte";


    export let user;
    export let i;
    const dispatch = createEventDispatcher();
    
    const remove = () => {
        dispatch('remove', user.id)
    }
</script>



<div class="flex m-5 bg-black border p-2 
rounded-lg shadow-md hover:shadow-lg 
cursor-pointer items-center relative">
    <button
    on:click={remove}
    class="absolute right-0 top-0 -mt-3 rounded-full w-5 h-5 text-center 
    bg-red-300 text-white text-sm hover:bg-red-700">X</button>
    <p class="px-10">{i + 1}</p>
    <img class="rounded-full w-20 h-14 bg-white" src={user.icon} alt={user.name}>
    <p class="mx-4 w-25">{user.name}</p>
    <p class="mx-4 w-25">{user.email}</p>
</div>