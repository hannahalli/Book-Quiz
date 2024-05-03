<script>
    import WinnieThePoohChoice from './WinnieThePoohChoice.svelte';
    import AnimalTalesChoice from './AnimalTalesChoice.svelte';

    let selectedChoice = "";
    let showNextButton = false;

    // Combine 'choiceMade' and 'nextButtonClicked' into a single boolean for simplicity
    let nextQuestionDisplayed = false;

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
    <h2>What kind of animal adventure would you like to have?</h2>

    <div>
        <button class:selected={selectedChoice === "winnieThePooh1"} on:click={() => handleChoiceClick("winnieThePooh1")}>
            Help a bear find some honey!
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "animalTales1"} on:click={() => handleChoiceClick("animalTales1")}>
            Join a race with a tortoise and a hare!
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "animalTales"} on:click={() => handleChoiceClick("animalTales")}>
            Outsmart a cunning fox in the forest!
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "winnieThePooh"} on:click={() => handleChoiceClick("winnieThePooh")}>
            Sing songs with friends in the Hundred Acre Wood!
        </button>
    </div>

    {#if showNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}

{:else}
    {#if selectedChoice === "winnieThePooh"}
        <WinnieThePoohChoice />
    {/if}
    {#if selectedChoice === "animalTales"}
        <AnimalTalesChoice />
    {/if}
    {#if selectedChoice === "winnieThePooh1"}
        <WinnieThePoohChoice />
    {/if}
    {#if selectedChoice === "animalTales1"}
        <AnimalTalesChoice />
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

