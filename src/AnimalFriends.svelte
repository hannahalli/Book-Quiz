<script>
    import Question1 from './Question1.svelte'; // Import Question0 component (optional for future use)

    let chosenAnswer = ""; // Track chosen answer for reference (optional)
    let goNextButton = false;
    let choiceMade = false;

    const handleAnswerClick = (answer) => {
        chosenAnswer = answer; // Store chosen answer (optional)
        choiceMade = true;
    };

    const goNextButton1 = () => {
        // No need to emit an event in this case
        goNextButton = true;
    };
</script>
    {#if !goNextButton}
    <h2>Who would you most like to befriend in the forest?</h2>

    <div>
        <button class:selected={chosenAnswer === "Wise Owl"} on:click={() => handleAnswerClick("Wise Owl")}>The wise old owl with endless stories</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Playful Squirrel"} on:click={() => handleAnswerClick("Playful Squirrel")}>The playful squirrel who knows all the secret hiding places</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Strong Bear"} on:click={() => handleAnswerClick("Strong Bear")}>The strong bear who can teach you to defend yourself</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Singing Bird"} on:click={() => handleAnswerClick("Singing Bird")}>The singing bird who knows the language of the forest</button>
    </div>
  
    
    {#if choiceMade && !goNextButton}
        <button class="next"  on:click={goNextButton1}>Next</button>
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
