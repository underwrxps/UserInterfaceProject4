<script>
  let toggleState = true;
  let locationSet = false;
  let buttonText = "Sharer";
  let currentlyText = "Seeking";

  function getLocation() {
    locationSet = true;
  }

  function switchState() {
    toggleState = !toggleState;
    if (buttonText == "Sharer"){
      buttonText = "Seeker";
      currentlyText = "Sharing";
    }
    else {
      buttonText = "Sharer";
      currentlyText = "Seeking";
    }
  }

  function addShelter () {
    window.alert("Congratulations, you added your shelter to the list for your community. Thank you!");
  }
</script>

<main>
  <div class="mainContainer">
    <h2>ShelterSharer</h2>
    <b>Currently {currentlyText}</b>
    <div class="stateButton">
      <button on:click={switchState}>Switch to {buttonText}</button>
    </div>
    <br>
    <!-- for when you are seeking housing -->
    {#if toggleState == true}
      <button on:click={getLocation}>Get My Location</button>
      <br>
      {#if locationSet == true}
        <div class="addressDropdown">
          <b>Shelter: </b>
          <select name="locations" id="locations">
            <option value="Addr1">Shelterhouse</option>
            <option value="Addr2">Talbert House</option>
            <option value="Addr3">Bethany House Services</option>
            <option value="Addr4">City Gospel Mission</option>
          </select>
        </div>
      {/if}
      <br>
      <iframe
        title="map"
        src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d164388.20990939497!2d-84.52020278550863!3d39.13106191862196!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8841b38acb65ec25%3A0x4249b42781c0c5fc!2sUniversity%20of%20Cincinnati!5e1!3m2!1sen!2sus!4v1731696240570!5m2!1sen!2sus"
        width="280"
        height="280"
        style="border:0;"
        allow=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    <!-- for when you are sharing housing -->
    {:else}
      <div class="inputContainer">
        <b>Title of Business:</b>
        <input type="text">
        <br>
        <b>Address:</b>
        <input type="text" placeholder="Street Address">
        <input type="text" placeholder="City">
        <input type="text" placeholder="State">
        <input type="text" placeholder="Zip Code">
        <br>
        <b>Max Occupancy:</b>
        <input type="text">
        <br>
        <b>Time Available:</b>
        <input type="text">
        <br>
        <br>
        <button on:click={addShelter}>Add Shelter</button>
      </div>
    {/if}
  </div>
</main>

<style>
  h2 {
    margin-top: 0.75em 0;
    margin-bottom: 0;
    padding: 0;
  }

  .mainContainer {
    height: 600px;
    width: 300px;
    border-style: solid;
    border-color: black;
    border-radius: 15px;
  }

  .mainContainer button {
    border-style: solid;
    border-color: black;
    border-radius: 8px;
  }
  
  .inputContainer {
    width: 280;
    clear: both;
  }

  .inputContainer input {
    width: 80%;
    clear: both;
  }

  .addressDropdown select {
    width: 80%;
    clear: both;
  }
</style>
