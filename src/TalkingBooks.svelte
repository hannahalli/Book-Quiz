<script>
    import Question1 from './Question1.svelte'; // Import Question1 component

    let chosenAnswer = ""; // Track chosen answer for reference (optional)
    let goNextButton = false;
    let choiceMade = false;

    const handleAnswerClick = (answer) => {
        chosenAnswer = answer; // Store chosen answer (optional)
        choiceMade = true;
    };

    const goToNextQuestion = () => {
        // No need to emit an event in this case
        goNextButton = true;
    };
</script>

{#if !goNextButton}
    <h2>Which story would you like to hear first?</h2>

    <div>
        <button class:selected={chosenAnswer === "The Lost City"} on:click={() => handleAnswerClick("The Lost City")}>A tale of a hidden city shrouded in mystery!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "The Talking Beasts"} on:click={() => handleAnswerClick("The Talking Beasts")}>A fable of animals who speak the language of the forest!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "The Bravest Hero"} on:click={() => handleAnswerClick("The Bravest Hero")}>A legend of a hero who faced unimaginable dangers!</button>
    </div>

    {#if choiceMade && !goNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}
{/if}

{#if goNextButton}
    <Question1 />
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
