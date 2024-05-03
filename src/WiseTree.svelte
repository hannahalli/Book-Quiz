<script>
    import Question1 from './Question1.svelte';
    
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
    <h2>The wise tree asks...</h2>

    <div>
        <button class:selected={chosenAnswer === "Strength"} on:click={() => handleAnswerClick("Strength")}>The path to become stronger</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Knowledge"} on:click={() => handleAnswerClick("Knowledge")}>Secrets of the hidden world</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Friendship"} on:click={() => handleAnswerClick("Friendship")}>Guidance on finding true friends</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Destiny"} on:click={() => handleAnswerClick("Destiny")}>Understanding my purpose</button>
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
