<script>
  export let listItem = "";
  export let deleteItem;
  export let doneItem;
</script>

<style>
  li {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }

  .actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-right: -20px;
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
    background: linear-gradient(
      180deg,
      rgba(64, 179, 255, 0.16862745098039217),
      rgba(0, 133, 221, 0.4117647058823529)
    );
    border-radius: 2px;
  }
</style>

<li>
  <p>{listItem.todo}</p>
  <div class="actions">
    <button on:click={doneItem(listItem.id)}>
      <img src="/assets/tick.svg" alt="Tick" />
    </button>
    <button on:click={deleteItem(listItem.id)}>
      <img src="/assets/rubbish.svg" alt="Remove" />
    </button>
  </div>
</li>
