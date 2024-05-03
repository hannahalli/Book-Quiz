<script>
    import BookDetails from './BookDetails.svelte'; // Import component for book details

    let chosenBook = ""; // Track chosen book for reference (optional)
    let goNextButton = false; // Flag for displaying book details
    let choiceMade = false;

    const handleBookClick = (book) => {
        chosenBook = book; // Store chosen book (optional)
        choiceMade = true;
    };

    const goToNextQuestion = () => {
        goNextButton = true; // Flag for displaying book details
    };
</script>
{#if !goNextButton}
<h2>Based on your choices, Hans Christian Andersen seems like a great fit! Pick a story to learn more:</h2>

<div>
    <button class:selected={chosenBook === "The Snow Queen"} on:click={() => handleBookClick("The Snow Queen")}>
        The Snow Queen: Embark on a thrilling adventure with Gerda as she searches for her friend Kay, stolen by the Snow Queen to her icy palace.
    </button>
</div>
<div>
    <button class:selected={chosenBook === "The Complete Fairy Tales & Stories"} on:click={() => handleBookClick("The Complete Fairy Tales & Stories")}>
        The Complete Fairy Tales & Stories (Hans Christian Andersen): Dive into a vast collection of Hans Christian Andersen's beloved tales, including The Little Mermaid, The Ugly Duckling, and The Emperor's New Clothes.
    </button>
</div>

    {#if choiceMade && !goNextButton}
    <button class="next" on:click={goToNextQuestion}>Next</button>
    {/if}
{/if}

{#if goNextButton}
<BookDetails bookTitle={chosenBook} />
{/if}

<style>
    /* Same styles as provided previously */
    h2 {
        font-size: 18px;
    }
    button {
        font-size: 15px;
        padding: 8px 16px;
        border: 5px solid brown;
        border-radius: 10px;
        margin: 5px;
        cursor: pointer;
        width: 240px; /* Adjust width for longer titles */
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
