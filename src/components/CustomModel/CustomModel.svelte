<script>
  import { Button, Modal } from "flowbite-svelte";
  import { createEventDispatcher } from "svelte";
  import CustomSpinner from "../CustomSpinner/CustomSpinner.svelte";

  export let popupModal = true;
  export let spinnerLoading = false;
  export let outcome = "";

  const dispatch = createEventDispatcher();
</script>

<!-- <Button on:click={() => (popupModal = true)}>Pop-up modal</Button> -->

<Modal
  classHeader="my-custom-header-class"
  bind:open={popupModal}
  size="xs"
  autoclose
>
  <div class="text-center">
    {#if spinnerLoading}
      <div class="text-center">
        <CustomSpinner />
      </div>
    {:else if outcome === "1"}
      <h1>Good Wine</h1>
      <h1>Score returned: {outcome}</h1>
      <div style="margin-top: 10px;">
        <Button
          color="alternative"
          on:click={() => {
            dispatch("modalCLick");
          }}>Click to Close</Button
        >
      </div>
    {:else}
      <h1>Not Good Wine</h1>
      <h1>Score returned: {outcome}</h1>
      <Button
        color="alternative"
        on:click={() => {
          dispatch("modalCLick");
        }}>Click to Close</Button
      >
    {/if}
  </div>
</Modal>

<style>
  /* Hide the close icon */
  /* Define a custom class to hide the close button */
  .my-custom-header-class .modal__header-close {
    display: none;
  }
</style>
