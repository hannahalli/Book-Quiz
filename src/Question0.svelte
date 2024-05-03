<script>
    import QuestionSparklingForest from './QuestionSparklingForest.svelte';
    import QuestionCloudKingdom from './QuestionCloudKingdom.svelte';
    import QuestionHiddenLibrary from './QuestionHiddenLibrary.svelte'; // Add component for the third option

    let forestSelected = false;
    let kingdomSelected = false;
    let librarySelected = false;
    let showNextButton = false;
    let goNextButton = false;

    const handleForestSelect = () => {
        forestSelected = true;
        kingdomSelected = false;
        librarySelected = false;
        showNextButton = true;
    };

    const handleKingdomSelect = () => {
        forestSelected = false;
        kingdomSelected = true;
        librarySelected = false;
        showNextButton = true;
    };

    const handleLibrarySelect = () => {
        forestSelected = false;
        kingdomSelected = false;
        librarySelected = true;
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        // Emit event with details on the chosen path ("forest", "kingdom", or "library")
        goNextButton = true;
    };
</script>

{#if !goNextButton}
<h2>What magical place would you explore?</h2>
<div>
    <button class:selected={forestSelected} on:click={handleForestSelect}>A sparkling forest with talking animals ✨</button>
</div>
<div>
    <button class:selected={kingdomSelected} on:click={handleKingdomSelect}>A cloud kingdom filled with candy rain ☁️</button>
</div>
<div>
    <button class:selected={librarySelected} on:click={handleLibrarySelect}>A hidden library with endless magical books 📖</button>
</div>
{/if}

{#if showNextButton && !goNextButton}
<button class="next"on:click={goToNextQuestion}>Next</button>
{/if}

{#if forestSelected && goNextButton}
    <QuestionSparklingForest />
{:else if kingdomSelected && goNextButton}
    <QuestionCloudKingdom />
{:else if librarySelected && goNextButton}
    <QuestionHiddenLibrary />
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
