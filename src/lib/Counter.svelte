<div>
  {#if loop || decrementable}
    <button on:click={decrement}> - </button>
  {/if}

  <span> {count} </span>

  {#if loop || incrementable}
    <button on:click={increment}> + </button>
  {/if}
</div>

<div>
  {#each Array.from(new Array(count).keys()) as i}
    _
  {/each}
</div>

<script>
  export let min = 0;
  export let max = 100;
  export let loop = true;

  let incrementable = true;
  let decrementable = false;

  $: count = min;

  $: increment = () => {
    if (count >= max) {
      count = min;
    } else {
      count += 1;
    }

    incrementable = !(count >= max);
    decrementable = (count >= max);
  };
  $: decrement = () => {
    if (count <= min) {
      count = max;
    } else {
      count -= 1;
    }

    decrementable = !(count <= min);
    incrementable = (count <= min);
  };
</script>