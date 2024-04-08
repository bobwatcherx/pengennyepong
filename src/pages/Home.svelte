<script>
  import { onMount } from 'svelte';
  import {template_iframe} from '../base/dataconfig.js'
    import Swal from 'sweetalert2';
  let showAlert = true;

  let selectedTemplate = null;

  function handleRadioChange(event) {
    selectedTemplate = event.target.value;
     showAlert = true;
  }

  let modalopen = false;
  function selectRandomTemplate() {
    const randomIndex = Math.floor(Math.random() * template_iframe.length);
    selectedTemplate = template_iframe[randomIndex].url;
  }
  
  onMount(selectRandomTemplate);

function iframeload(){
  showAlert = false;
}
</script>



<style>
  .horizontalbox {
    display: flex;
    flex-direction: row;
    overflow-x: auto;
    white-space: nowrap /* Menghindari wrap teks */
  }

  label {
    margin-right: 10px; 
    color: #e91e63 ; 
    font-weight: bold; 
  }

  .with-gap[type="radio"]:checked+span:after {
    background-color: red;
    border-color: red; 
  }
  .btnfloat{
    position: fixed;
    bottom: 30px;
    right: 10px;
    overflow-x: hidden; /* Mencegah scroll horizontal */
  }
</style>



<div class="btnfloat">
  <button
  style="border-radius: 30px"
  on:click={()=>modalopen =  true}
  class="btn waves waves-effect orange darken-2"
  >Chat Admin</button>
</div>


  <div class="card">
    <div class="container">
    <h6 style="font-weight: bold">Pilih genre Bokep</h6>
    <div class="horizontalbox">
      {#each template_iframe as {label, url}}
        <label>
          <input class="with-gap" type="radio" name="template" bind:group={selectedTemplate} value={url} on:change={handleRadioChange}>
          <span>{label}</span>
        </label>
      {/each}
    </div>
  </div>
  </div>

{#if modalopen}
  <div class="card z-depth-5" style="margin:10px;z-index: 10">
    <div class="container">
      <div style="display: flex;justify-content: space-between;">
        <h5>Request Bokep</h5>
        <button  
          on:click={()=>modalopen = false}
          class="btn-floating btn-large waves-effect waves-light red"><i class="material-icons">close</i></button>
      </div>
    </div>
    <iframe src="https://bobwatcherx.github.io/chatbokep" style="width: 100%; height: 500px;" frameborder="0"></iframe>
  </div>
{:else}

{#if showAlert}
<div class="card  waves waves-effect  pink darken-2 z-depth-5" style="padding: 5px;width: 100%">
  <div style="display: flex;justify-content: center">
     <div class="preloader-wrapper big active">
    <div class="spinner-layer spinner-white-only" >
      <div class="circle-clipper left">
        <div class="circle"></div>
      </div><div class="gap-patch">
        <div class="circle"></div>
      </div><div class="circle-clipper right">
        <div class="circle"></div>
      </div>
    </div>
  </div>
  </div>
  <h5 style="color: white;font-weight: bold">Sedang mengganti Genre Bokep...</h5>
</div>
{/if}


  {#if selectedTemplate }
  <iframe src={selectedTemplate}
  on:load={iframeload}
     style="width: 100vw; height: 100vh; overflow-x: hidden;" frameborder="0"></iframe>
  {/if}
{/if}
