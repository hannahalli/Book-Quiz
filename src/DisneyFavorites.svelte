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
<h2>It looks like the magical world of Disney is right for you! Which story will you pick?</h2>

<div>
    <button class:selected={chosenBook === "Walt Disney’s Story Land 55 Favorite Stories"} on:click={() => handleBookClick("Walt Disney’s Story Land 55 Favorite Stories")}>
        Explore a collection of 55 beloved Disney stories
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Donald Duck Sees South America"} on:click={() => handleBookClick("Donald Duck Sees South America")}>
        Join Donald Duck on a wacky adventure 
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Walt Disney’s Peter Pan"} on:click={() => handleBookClick("Walt Disney’s Peter Pan")}>
        Never grow up with Peter Pan as he whisks Wendy and her brothers to Neverland 
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Mickey See The U.S.A."} on:click={() => handleBookClick("Mickey See The U.S.A.")}>
        Travel across the USA with Mickey Mouse as he explores iconic landmarks 
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Everything I Need to Know I Learned From a Disney Little Golden Book"} on:click={() => handleBookClick("Everything I Need to Know I Learned From a Disney Little Golden Book")}>
        Discover life lessons through the stories of Disney Little Golden Books
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
