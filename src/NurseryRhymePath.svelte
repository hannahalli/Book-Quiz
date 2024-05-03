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
<h2>It seems like nursery rhymes is right for you! Which collection of rhymes would you like to explore?</h2>

<div>
    <button class:selected={chosenBook === "Book of Nursery and Mother Goose Rhymes"} on:click={() => handleBookClick("Book of Nursery and Mother Goose Rhymes")}>
        Discover classic rhymes from the "Book of Nursery and Mother Goose Rhymes".
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Nursery Friends From France"} on:click={() => handleBookClick("Nursery Friends From France")}>
        Join the fun with "Nursery Friends From France"!
    </button>
</div>
<div>
    <button class:selected={chosenBook === "The Annotated Mother Goose"} on:click={() => handleBookClick("The Annotated Mother Goose")}>
        Explore the rich history of rhymes with "The Annotated Mother Goose".
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

