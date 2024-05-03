<script>
    import BookDetails from './BookDetails.svelte'; // Import component for book details

    let chosenBook = ""; // Track chosen book for reference (optional)
    let goNextButton = false; // Flag for displaying book details
    let animalTalesChoice = ""; // Track chosen animal tale category (optional)
    let choiceMade = false;

    const handleBookClick = (book) => {
        chosenBook = book; // Store chosen book (optional)
        choiceMade = true;

    };

    const goToNextQuestion = () => {
        goNextButton = true; // Flag for displaying book details
    };

    const handleAnimalTaleChoice = (choice) => {
        animalTalesChoice = choice;
    };
</script>

{#if !goNextButton}

    <h2>Based on your choices, it seems like animal tales are right for you! Here are some exciting books:</h2>

        <div>
            <button class:selected={chosenBook === "Aesop’s Fables"} on:click={() => handleBookClick("Aesop’s Fables")}>
                Learn timeless wisdom with Aesop's Fables!
            </button>
        </div>
        <div>
            <button class:selected={chosenBook === "Tales From Beatrix Potter"} on:click={() => handleBookClick("Tales From Beatrix Potter")}>
                Explore Beatrix Potter's charming animal tales!
            </button>
        </div>
        <div>
            <button class:selected={chosenBook === "White Tail: King of the Forest"} on:click={() => handleBookClick("White Tail: King of the Forest")}>
                Follow the journey of White Tail, the king of the forest!
            </button>
        </div>
        <div>
            <button class:selected={chosenBook === "The Boy, The Mole, The Fox and The Horse"} on:click={() => handleBookClick("The Boy, The Mole, The Fox and The Horse")}>
                Discover heartwarming friendship in "The Boy, The Mole, The Fox and The Horse".
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

