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
<h2>Based on your choices, the Brothers Grimm seem like a great fit! Pick a story to learn more:</h2>

<div>
    <button class:selected={chosenBook === "The Complete Brothers Grimm Fairy Tales"} on:click={() => handleBookClick("The Complete Brothers Grimm Fairy Tales")}>
        The Complete Brothers Grimm Fairy Tales: Dive into a collection of classic tales, from Rapunzel and Cinderella to Hansel and Gretel.
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Snow White or The House In The Wood"} on:click={() => handleBookClick("Snow White or The House In The Wood")}>
        Snow White or The House In The Wood: Discover the tale of a beautiful princess, a jealous stepmother, and seven dwarfs in this story.
    </button>
</div>
<div>
    <button class:selected={chosenBook === "The Sleeping Beauty"} on:click={() => handleBookClick("The Sleeping Beauty")}>
        The Sleeping Beauty: Unravel the mystery of a princess cursed to sleep for a hundred years.
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
