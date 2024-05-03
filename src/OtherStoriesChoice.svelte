<script>
    import GrimmFairyTales from './GrimmFairyTales.svelte';
    import HansChristianAndersen from './HansChristianAndersen.svelte';

    let selectedChoice = "";
    let showNextButton = false; // Flag for displaying the Next button
    let goNextButton = false;

    const handleChoiceClick = (choiceType) => {
        selectedChoice = choiceType;
        showNextButton = true;
    };
    const goToNextQuestion = () => {
        goNextButton = true; // Flag for displaying book details
    };
</script>
    {#if !goNextButton}
    <h2>Let's explore beyond the classics! Which story world would you like to visit?</h2>

    <div>
        <button class:selected={selectedChoice === "grimmBrothers"} on:click={() => handleChoiceClick("grimmBrothers")}>
            Help a brave princess outwit a cunning villain! 
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "hca"} on:click={() => handleChoiceClick("hca")}>
            Join a mermaid on her journey to the human world! 
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "grimmFairyTale"} on:click={() => handleChoiceClick("grimmFairyTale")}>
            Find a clever way to outsmart a sly fox! 
        </button>
    </div>
    <div>
        <button class:selected={selectedChoice === "hcaFairyTale"} on:click={() => handleChoiceClick("hcaFairyTale")}>
            Make a wish with a magical flying trunk! 
        </button>
    </div>

    {#if showNextButton}
        <button class="next" on:click={() => goToNextQuestion()}>Next</button>
    {/if}
{:else}
    {#if selectedChoice === "grimmBrothers"}
        <GrimmFairyTales />
    {/if}
    {#if selectedChoice === "hca"}
        <HansChristianAndersen />
    {/if}
    {#if selectedChoice === "grimmFairyTale"}
        <GrimmFairyTales />
    {/if}
    {#if selectedChoice === "hcaFairyTale"}
        <HansChristianAndersen />
    {/if}
{/if}

<style>
    /* Same styles as provided previously */
    h2 {
        font-size: 18px;
    }
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
