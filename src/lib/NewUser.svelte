<script>
  import { createEventDispatcher } from "svelte";
  import Modal from "./Modal.svelte";
  const dispatch = createEventDispatcher();
  let showModal = false;
  let newUser = {}

  function handleForm(){
    dispatch('newUser', newUser)
    showModal= false
  }

</script>
<div class="mt-4">
    <button 
    on:click={()=> (showModal = true)}
    class="px-2 py-2 bg-blue-800 text-white rounded-lg cursor-pointer">
        New User
    </button>

    {#if showModal}
    <Modal on:close={ () => (showModal=false)}
        on:submit={handleForm}>
        <h1 class="text-2xl text-center">Insert form here</h1>
        <div class="py-1 px-2 my-4">
            <label for="">Name</label>
            <input bind:value={newUser.name}
            type="text" class="px-2 py-1 w-full rounded border"/>
        </div>
        <div class="py-1 px-2 my-4">
            <label for="">Email</label>
            <input bind:value={newUser.email}
            type="email" class="px-2 py-1 w-full rounded border"/>
        </div>
        

        <div class="py-1 px-2 my-4 flex justify-between">
            <p class="mx-4">Active</p>

            <div class="flex">
                
                <label for="true">Yes</label>

                <input bind:group={newUser.active}
                name="active" type="radio" id="true" value={true}
                class="px-2 py-1 w-full rounded border mx-5"/>

                <label for="false">No</label>
                <input bind:group={newUser.active}
                name="active" type="radio" id="false" value={false} 
                class="px-2 py-1 w-full rounded border mx-5"/>
            </div>
        </div>
        
        <button 
            type="submit"
            slot="right-button" 
            class="px-2 py-1 bg-blue-800 text-white rounded">
            Create
        </button>
    </Modal>
    {/if}
</div>
