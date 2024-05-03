<script>
    import CandyLand from './CandyLand.svelte'; // Import CandyLand component
    import RainbowRiver from './RainbowRiver.svelte'; // Import RainbowRiver component

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
<h2>You enter Cloud Kingdom! How would you like to spend your time here?</h2>


<div>
    <button class:selected={chosenAnswer === "CandyLand"} on:click={() => handleAnswerClick("CandyLand")}>Explore the mountains of candy and sweets!</button>
</div>
<div>
    <button class:selected={chosenAnswer === "RainbowRiver"} on:click={() => handleAnswerClick("RainbowRiver")}>Take a ride on the rainbow river that flows through the clouds!</button>
</div>

{#if choiceMade}
<button class="next" on:click={goToNextQuestion}>Next</button>
{/if}
{/if}

{#if goNextButton}
    {#if chosenAnswer === "RainbowRiver"}
        <RainbowRiver />
    {/if}
    {#if chosenAnswer === "CandyLand"}
        <CandyLand />
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

