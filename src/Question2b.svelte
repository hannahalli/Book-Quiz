<script>
    import EnchantedForestChoice from './EnchantedForestChoice.svelte';
    import BeyondTheRainbowChoice from './BeyondTheRainbowChoice.svelte';

    let selectedChoice = "";
    let showNextButton = false; // Flag for displaying the Next button
    let nextQuestionDisplayed = false; // Flag for displaying the selected component

    const handleChoiceClick = (choiceType) => {
        selectedChoice = choiceType;
        nextQuestionDisplayed = false; // Reset to display the main question
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        nextQuestionDisplayed = true;
    };
</script>

{#if !nextQuestionDisplayed}
    <h2>Where does your imagination take you today?</h2>

    <div>
        <button class:selected={selectedChoice === "enchantedForest"} on:click={() => handleChoiceClick("enchantedForest")}>
            Into the Enchanted Forest
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "beyondTheRainbow"} on:click={() => handleChoiceClick("beyondTheRainbow")}>
            Beyond the Rainbow
        </button>
    </div>

    {#if showNextButton}
        <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}

{:else}
    {#if selectedChoice === "enchantedForest"}
        <EnchantedForestChoice />
    {:else}
        <BeyondTheRainbowChoice />
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
