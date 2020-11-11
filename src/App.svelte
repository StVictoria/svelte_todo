<script>
  import ToDoItem from "./ToDoItem.svelte";
  import DoneToDoItem from "./DoneToDoItem.svelte";

  $: inputValue = "";
  let list = [{ id: Date.now(), todo: "Сделать To Do" }];
  let doneItemsList = [];

  let handleSubmit = () => {
    list = [...list, { id: Date.now(), todo: inputValue }];
    inputValue = "";
  };

  let doneItem = id => {
    let checkedItem = list.filter(item => item.id === id);
    doneItemsList = [...doneItemsList, checkedItem[0]];
    list = list.filter(item => item.id !== id);
    console.log("doneItemsList", doneItemsList);
  };
  let deleteItem = id => {
    list = list.filter(item => item.id !== id);
  };
  let deleteDoneItem = id => {
    doneItemsList = doneItemsList.filter(item => item.id !== id);
  };
</script>

<style>
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100vh;
    background: linear-gradient(45deg, #ff3e00, #40b3ff, #676778);
  }

  .todoBlock {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 40%;
    background-color: #f9fffa;
    padding: 20px;
    border-radius: 5px;
    box-shadow: -5px 5px 40px #757575;
  }

  h1 {
    width: 100%;
    text-align: center;
    margin-bottom: 20px;
  }

  form {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 60%;
  }

  input {
    width: 310px;
    margin-bottom: 0;
  }

  button {
    background-color: inherit;
    border: none;
    outline: none;
    margin: 0;
    cursor: pointer;
    margin-right: -5px;
  }

  img {
    width: 30px;
  }

  ul {
    width: 60%;
    padding: 0;
  }
</style>

<main>
  <section class="todoBlock">
    <h1>To Do List</h1>
    <form on:submit|preventDefault={handleSubmit}>
      <input
        type="text"
        bind:value={inputValue}
        on:input={event => (inputValue = event.target.value)} />
      <button type="submit">
        <img src="/assets/more.svg" alt="Add" />
      </button>
    </form>
    {#if list.length !== 0}
      <ul>
        {#each list as listItem, i (listItem.id)}
          <ToDoItem {listItem} {deleteItem} {doneItem} />
        {/each}
      </ul>
    {:else}
      <p>No tasks yet</p>
    {/if}
    {#if doneItemsList.length !== 0}
      <ul>
        {#each doneItemsList as doneItem, i (doneItem.id)}
          <DoneToDoItem {doneItem} {deleteDoneItem} />
        {/each}
      </ul>
    {:else}{''}{/if}
  </section>

</main>
