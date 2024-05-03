<script>
    import Question2a from './Question2a.svelte'; 
    import Question2b from './Question2b.svelte'; 
    import Question2c from './Question2c.svelte'; 

    let selectedAdventure = ""; 
    let showNextButton = false; 
    let goNextButton = false;

    const handleAdventureClick = (adventureType) => {
        selectedAdventure = adventureType;
        showNextButton = true;
    };

    const goToNextQuestion = () => {
        // Emit event based on selected adventure type
        goNextButton = true;
    };
</script>

{#if !goNextButton}
    <h2>What kind of adventure would you most like to have?</h2>

    <div>
        <button class:selected={selectedAdventure === "question2a"} on:click={() => handleAdventureClick("question2a")}>
            A silly and lighthearted journey!
        </button>
    </div>
    <div>
        <button class:selected={selectedAdventure === "question2b"} on:click={() => handleAdventureClick("question2b")}>
            A magical quest with fantastical creatures!
        </button>
    </div>
    <div>
        <button class:selected={selectedAdventure === "question2c"} on:click={() => handleAdventureClick("question2c")}>
            An exciting exploration of a new world!
        </button>
    </div>

    {#if showNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}

    {/if}
    {#if goNextButton}
        {#if selectedAdventure === "question2a"}
            <Question2a />
        {:else if selectedAdventure === "question2b"}
            <Question2b />
        {:else if selectedAdventure === "question2c"}
            <Question2c />
        {/if}
    {/if}

<style>
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
