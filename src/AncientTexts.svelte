<script>
    import Question1 from './Question1.svelte'; // Import Question1 component

    let chosenAnswer = ""; // Track chosen answer for reference (optional)
    let goNextButton = false;
    let showNextButton = false;

    const handleAnswerClick = (answer) => {
        chosenAnswer = answer; // Store chosen answer (optional)
        showNextButton = true;

    };

    const goToQuestion1 = () => {
        // No need to emit an event in this case
        goNextButton = true;
    };
</script>
{#if !goNextButton}

    <h2>Which subject would you like to learn more about?</h2>

    <div>
        <button class:selected={chosenAnswer === "Forgotten Magic"} on:click={() => handleAnswerClick("Forgotten Magic")}>Unearth the secrets of lost magical traditions!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Ancient History"} on:click={() => handleAnswerClick("Ancient History")}>Delve into the forgotten stories of civilizations past!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Mythical Creatures"} on:click={() => handleAnswerClick("Mythical Creatures")}>Discover the legends surrounding fantastical beings!</button>
    </div>

    {#if showNextButton}
    <button class="next" on:click={goToQuestion1}>Next</button>
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
