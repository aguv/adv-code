<script>
  import Icon from 'svelte-icons-pack/Icon.svelte';
  import AiTwotoneGift from 'svelte-icons-pack/ai/AiTwotoneGift';
  import RiSystemDeleteBin5Line from 'svelte-icons-pack/ri/RiSystemDeleteBin5Line';

  import uuid4 from 'uuid4';

  let gifts = [
    { name: 'Play 5', id: uuid4() },
    { name: 'Vapo Mighty+', id: uuid4() },
  ];
  let newGift = '';

  const addGift = () => {
    if (newGift) {
      gifts = [...gifts, { name: newGift, id: uuid4() }];
      newGift = '';
    }
  };

  const deleteGift = (id) => {
    console.log('zxczxc');
    gifts = gifts.filter((gift) => gift.id !== id);
  };
</script>

<div class="container">
  <main class="gifts">
    <header>
      <Icon src={AiTwotoneGift} />
      <span>Regalos</span>
    </header>
    <div>
      {#each gifts as gift, i (gift.id)}
        <div class="gift">
          <span>{i + 1}. {gift.name}</span>
          <button on:click={() => deleteGift(gift.id)}>
            <Icon src={RiSystemDeleteBin5Line} color="#ffffff" />
          </button>
        </div>
      {:else}
        <span>No tem regalitos :)</span>
      {/each}
    </div>
    <footer>
      <input bind:value={newGift} />
      <button on:click={addGift}>Agregar</button>
    </footer>
  </main>
</div>

<style lang="scss">
  .container {
    height: 100vh;
    background: rgb(165, 69, 69);
    display: grid;
    place-content: center;
  }

  .gifts {
    background-color: rgb(43, 133, 106);
    padding: 1rem;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;

    header {
      display: flex;
      gap: 0.5rem;
      align-items: center;
      font-size: 30px;
      text-decoration: underline;

      span {
        color: #ffffff;
      }
    }

    > div {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      color: #ffffff;
    }
  }

  .gift {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;

    button {
      padding: 0.25rem;
      background: rgb(89, 95, 94);
      cursor: pointer;
    }
  }
</style>
