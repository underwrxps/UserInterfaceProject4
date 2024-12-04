<script>
  let toggleState = false;
  let locationSet = false;

  function getLocation() {
    locationSet = true;
  }
</script>

<main>
  <div class="topSlider">
      Seeking 
      <label class="switch">
        <input type="checkbox" bind:value={toggleState}>
        <span class="slider round"></span>
      </label>
       Sharing
  </div>
  <!-- for when you are seeking housing -->
  {#if toggleState == false}
    <button on:click={getLocation}>Get My Location</button>
    {#if locationSet == true}
      <div class="addressDropdown">
        <select name="locations" id="locations">
          <option value="Addr1">Addr1</option>
          <option value="Addr2">Addr2</option>
          <option value="Addr3">Addr3</option>
          <option value="Addr4">Addr4</option>
        </select>
      </div>
    {/if}
  <!-- for when you are sharing housing -->
  {:else}

  {/if}
</main>

<style>
  .topSlider {
   display: flex;
  }

  .switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 34px;
  }

  .switch input {
    opacity: 0px;
    width: 0px;
    height: 0px;
  }

  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: .4s;
    transition: .4s;
  }

  .slider:before {
    position: absolute;
    content: "";
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    -webkit-transition: .4s;
    transition: .4s;
  }

  input:checked + .slider {
    background-color: #2196F3;
  }

  input:focus + .slider {
    box-shadow: 0 0 1px #2196F3;
  }

  input:checked + .slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
  }

  /* Rounded sliders */
  .slider.round {
    border-radius: 34px;
  }

  .slider.round:before {
    border-radius: 50%;
  }
</style>
