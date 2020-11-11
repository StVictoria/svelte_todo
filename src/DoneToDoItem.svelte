<script>
  export let doneItem;
  export let deleteDoneItem;
</script>

<style>
  li {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }

  button {
    background-color: inherit;
    border: none;
    outline: none;
    margin: 0;
    cursor: pointer;
  }

  img {
    width: 20px;
  }

  p {
    display: flex;
    align-items: center;
    width: 310px;
    height: 40px;
    padding: 5px;
    margin: 0;
    margin-bottom: 10px;
    box-sizing: border-box;
    background-color: grey;
    border-radius: 2px;
  }
</style>

<li>
  <p>{doneItem.todo}</p>
  <button on:click={deleteDoneItem(doneItem.id)}>
    <img src="/assets/rubbish.svg" alt="Remove" />
  </button>
</li>
