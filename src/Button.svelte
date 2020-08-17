<svelte:options tag="button-component" />

<script>
  import { createEventDispatcher } from 'svelte';
  export let disabled = false;
  export let type = '';
  const dispatch = createEventDispatcher();
  const typeHash = {
    primary: 'btn-primary'
  }
	function handleClick(event) {
    this.dispatchEvent(new CustomEvent('zpClick', { composed: true }))
  }
  $: buttonType = typeHash[type] || '';
</script>

<button
  class="btn { buttonType }"
  on:click={handleClick}
  {disabled} 
>
	<slot />
</button>

<style>
	.btn {
    margin: 20px;
    width: 130px;
    height: 40px;
    color: #fff;
    padding: 10px 25px;
    font-family: 'Lato', sans-serif;
    font-weight: 500;
    border-radius: 7px;
    outline: none;
  }
  .btn[disabled]{
    opacity: 0.5;
  }
  .btn-primary {
    background: rgb(9, 20, 172);
  }
  .btn-primary:hover {
    cursor: pointer;
    background: rgb(0,3,255);
  }
</style>