<script>
    import FrenchFairyTalesChoice from './FrenchFairyTalesChoice.svelte';
    import OtherStoriesChoice from './OtherStoriesChoice.svelte';

    let selectedChoice = "";
    let showNextButton = false; // Flag for displaying the Next button
    let nextQuestionDisplayed = false; // Flag for displaying the selected component
    let goNextButton = false;

    const handleChoiceClick = (choiceType) => {
        selectedChoice = choiceType;
        nextQuestionDisplayed = false; // Reset to display the main question
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        nextQuestionDisplayed = true;
        goNextButton = true;
    };
</script>

{#if !goNextButton}

<h2>Let's choose a story adventure!</h2>


<div>
    <button class:selected={selectedChoice === "frenchFairyTales"} on:click={() => handleChoiceClick("frenchFairyTales")}>
        Embark on a French story adventure filled with magic and brave heroes
    </button>
</div>
<div>
    <button class:selected={selectedChoice === "otherStories"} on:click={() => handleChoiceClick("otherStories")}>
        Explore a world of exciting adventures and timeless classics!
    </button>
</div>

{#if showNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
{/if}
{/if}

{#if nextQuestionDisplayed}
    {#if selectedChoice === "frenchFairyTales"}
        <FrenchFairyTalesChoice />
    {:else}
        <OtherStoriesChoice />
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

