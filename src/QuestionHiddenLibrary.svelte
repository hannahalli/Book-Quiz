<script>
    import AncientTexts from './AncientTexts.svelte'; // Import AncientTexts component
    import TalkingBooks from './TalkingBooks.svelte'; // Import TalkingBooks component

    let chosenAnswer = ""; // Track chosen answer for reference (optional)
    let goNextButton = false;
    let choiceMade = false;

    const handleAnswerClick = (answer) => {
        chosenAnswer = answer; // Store chosen answer (optional)
        choiceMade = true;
    };

    const goToNextQuestion = () => {
        // Implement logic based on chosen answer
        goNextButton = true;
    };
</script>
    {#if !goNextButton}
    <h2>How would you like to explore the library?</h2>

    <div>
        <button class:selected={chosenAnswer === "Ancient Texts"} on:click={() => handleAnswerClick("Ancient Texts")}>Browse the ancient texts filled with forgotten knowledge!</button>
    </div>
    <div>
        <button class:selected={chosenAnswer === "Talking Books"} on:click={() => handleAnswerClick("Talking Books")}>Listen to the talking books whisper their secrets!</button>
    </div>

    {#if choiceMade && !goNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}
    {/if}

{#if goNextButton}
    {#if chosenAnswer === "Ancient Texts"}
        <AncientTexts />
    {:else if chosenAnswer === "Talking Books"}
        <TalkingBooks />
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
