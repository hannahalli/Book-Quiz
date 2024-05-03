<script>
    import AnimalsPath from './AnimalsPath.svelte'; // Renamed WinnieThePoohPath to AnimalsPath
    import NurseryRhymePath from './NurseryRhymePath.svelte';

    let selectedPath = ""; // String to store the chosen path ("animals" or "nurseryRhyme")
    let showNextButton = false; // Flag to control "Next" button visibility
    let goNextButton = false;

    const handlePathClick = (path) => {
        selectedPath = path;
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        // Emit event based on the chosen path (e.g., "animals", "nurseryRhyme")
        goNextButton = true;
    };
</script>

{#if !goNextButton}
    <h2>Would you rather:</h2>
    <div>
        <button class:selected={selectedPath === "animals"} on:click={() => handlePathClick("animals")}>
            Have a picnic with a talking bear and his friends!
        </button>
    </div>
    <div>
        <button class:selected={selectedPath === "nurseryRhyme"} on:click={() => handlePathClick("nurseryRhyme")}>
            Skip rope with Humpty Dumpty (be careful not to knock him down!)
        </button>
    </div>

    {#if showNextButton}
    <button class="next"  on:click={goToNextQuestion}>Next</button>
    {/if}

{/if}


{#if goNextButton}
    {#if selectedPath === "animals"}
        <AnimalsPath />
    {:else if selectedPath === "nurseryRhyme"}
        <NurseryRhymePath />
    {/if}
{/if}

<style>
    /* Same styles as provided previously */
    button {
     font-size: 16px;
     padding: 10px 20px;
     border: 5px solid brown;
     border-radius: 10px;
     margin: 5px;
     cursor: pointer;
     width: 220px;
     background-color: darkgreen;
     color: white;
   }
   button.selected {
        background-color: lightgreen;
    }
   button.next {
     background-color: lightgreen;
     width: auto;
   }
</style>
