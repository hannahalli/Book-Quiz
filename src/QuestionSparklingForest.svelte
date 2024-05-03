<script>
    import AnimalFriends from './AnimalFriends.svelte'; // Import component for animal friends path
    import WiseTree from './WiseTree.svelte'; // Import component for wise tree path

    let animalFriendsSelected = false;
    let wiseTreeSelected = false;
    let showNextButton = false; // Flag to control "Next" button visibility
    let goNextButton = false;

    const handleAnimalFriendsClick = () => {
        animalFriendsSelected = true;
        wiseTreeSelected = false;
        showNextButton = true;
    };

    const handleWiseTreeClick = () => {
        animalFriendsSelected = false;
        wiseTreeSelected = true;
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        // Emit event based on selected path ("animalFriends" or "wiseTree")
        goNextButton = true;
    };
</script>

    {#if !goNextButton}
    <h2>What would you love to do most in the sparkling forest?</h2>

    <div>
        <button class:selected={animalFriendsSelected} on:click={handleAnimalFriendsClick}>
            Make friends with the talking animals! 
        </button>
    </div>
    <div>
        <button class:selected={wiseTreeSelected} on:click={handleWiseTreeClick}>
            Seek advice from the wise old tree. 
        </button>
    </div>
    {/if}

    {#if showNextButton && !goNextButton}
    <button class="next" disabled={!animalFriendsSelected && !wiseTreeSelected} on:click={goToNextQuestion}>Next</button>
    {/if}

    {#if animalFriendsSelected && goNextButton}
        <AnimalFriends />
    {:else if wiseTreeSelected && goNextButton}
        <WiseTree />

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
