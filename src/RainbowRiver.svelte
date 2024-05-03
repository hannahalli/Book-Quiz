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

    <h2>What adventure would you like to try first?</h2>


    <div>
        <button class:selected={chosenAnswer === "Ride a Rainbow Unicorn"} on:click={() => handleAnswerClick("Ride a Rainbow Unicorn")}>Ride a magical rainbow unicorn down the river!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Swim with Colorful Fish"} on:click={() => handleAnswerClick("Swim with Colorful Fish")}>Swim with schools of dazzling, colorful fish!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Collect Sparkling Wishes"} on:click={() => handleAnswerClick("Collect Sparkling Wishes")}>Collect sparkling wishes floating on water bubbles!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Visit the Cloud Castle"} on:click={() => handleAnswerClick("Visit the Cloud Castle")}>Dock at a cloud castle for a magical feast!</button>
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
