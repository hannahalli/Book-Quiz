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
<h2>What sweet treat would you like to try first?</h2>

<div>
    <button class:selected={chosenAnswer === "Chocolate River"} on:click={() => handleAnswerClick("Chocolate River")}>Dive into a river of melted chocolate!</button>
</div>
<div>
    <button class:selected={chosenAnswer === "Gummy Bear Forest"} on:click={() => handleAnswerClick("Gummy Bear Forest")}>Explore a forest made entirely of gummy bears!</button>
</div>
<div>
    <button class:selected={chosenAnswer === "Lollipop Lane"} on:click={() => handleAnswerClick("Lollipop Lane")}>Stroll down a lane lined with giant lollipops!</button>
</div>
<div>
    <button class:selected={chosenAnswer === "Marshmallow Mountain"} on:click={() => handleAnswerClick("Marshmallow Mountain")}>Climb a mountain made of fluffy marshmallows!</button>
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

