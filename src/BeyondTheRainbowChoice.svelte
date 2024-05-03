<script>
    import ClassicStories from './ClassicStories.svelte'; // Import component for Classic Stories
    import DisneyFavorites from './DisneyFavorites.svelte'; // Import component for Disney stories

    let chosenPotion = ""; // Track chosen potion (optional)
    let showNextButton = false; // Flag for displaying the Next button
    let goNextButton = false;

    const handlePotionClick = (potion) => {
        chosenPotion = potion;
        showNextButton = true;
    };
    const goToNextQuestion = () => {
        goNextButton = true; // Flag for displaying book details
    };
</script>
{#if !goNextButton}
<h2>Uh oh! A bubbling cauldron awaits! Choose a potion to reveal your story world:</h2>

<div>
    <button class:selected={chosenPotion === "classic"} on:click={() => handlePotionClick("classic")}>
        The Golden Potion: Hints of timeless tales and enduring characters. Perhaps a journey down a rabbit hole or a mischievous puppet?
    </button>
</div>
<div>
    <button class:selected={chosenPotion === "disney"} on:click={() => handlePotionClick("disney")}>
        The Sapphire Potion: Sparkles with animation and a sprinkle of magic. Maybe a daring undersea adventure or a soaring flight with a magical friend?
    </button>
</div>

{#if showNextButton}
    <button class="next" on:click={() => goToNextQuestion()}>Next</button>
{/if}
{/if}
{#if goNextButton}
    {#if chosenPotion === "classic"}
        <ClassicStories />
    {:else}
        <DisneyFavorites />
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
