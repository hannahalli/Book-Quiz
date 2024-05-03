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
<h2>It looks like the  world of Children's Classics is right for you! Which story would you like to delve into?</h2>

<div>
    <button class:selected={chosenBook === "Anne of Green Gables"} on:click={() => handleBookClick("Anne of Green Gables")}>
        Meet a spirited redhead with a thirst for adventure in a small Canadian town.
    </button>
</div>
<div>
    <button class:selected={chosenBook === "The Little Prince"} on:click={() => handleBookClick("The Little Prince")}>
        Join a tiny prince on a journey from his tiny asteroid to explore the universe.
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Pippi Longstocking"} on:click={() => handleBookClick("Pippi Longstocking")}>
        Embark on wacky adventures with a strong, girl who lives with her horse and monkey. 
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Alice’s Adventures in Wonderland and Through the Looking-Glass"} on:click={() => handleBookClick("Alice’s Adventures in Wonderland and Through the Looking-Glass")}>
        Fall down the rabbit hole with Alice and encounter a cast of quirky characters in Wonderland.
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
        padding: 6px 16px;
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
