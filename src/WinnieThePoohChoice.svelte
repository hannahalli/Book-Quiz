<script>
    import BookDetails from './BookDetails.svelte'; // Import Question1 component (optional for future use)

    let chosenBook = ""; // Track chosen book for reference (optional)
    let goNextButton = false;
    let choiceMade = false;

    const handleBookClick = (book) => {
        chosenBook = book; // Store chosen book (optional)
        choiceMade = true;
    };

    const goToQuestion= () => {
        // No need to emit an event in this case
        goNextButton = true;
    };
</script>
    {#if !goNextButton}
    <h2>Looks like Winnie-the-Pooh is the perfect fit! Which story catches your eye first?</h2>

    <div>
        <button class:selected={chosenBook === "Winnie-The-Pooh (1926)"} on:click={() => handleBookClick("Winnie-The-Pooh (1926)")}>
            Join Pooh on his first adventure in the original "Winnie-the-Pooh"!
        </button>
    </div>
    <div>
        <button class:selected={chosenBook === "The Little Things in Life: Simple Reflections from the Hundred-Acre Wood"} on:click={() => handleBookClick("The Little Things in Life: Simple Reflections from the Hundred-Acre Wood")}>
            Discover simple joys with Pooh in "The Little Things in Life".
        </button>
    </div>
    <div>
        <button class:selected={chosenBook === "The World of Christopher Robin"} on:click={() => handleBookClick("The World of Christopher Robin")}>
            Explore the world in "The World of Christopher Robin".
        </button>
    </div>
    <div>
        <button class:selected={chosenBook === "The Pooh Dictionary"} on:click={() => handleBookClick("The Pooh Dictionary: The Complete Guide to the Words of Pooh & All the Animals in the Forest")}>
            Learn the language of the Hundred Acre Wood with "The Pooh Dictionary".
        </button>
    </div>
    <div>
        <button class:selected={chosenBook === "When We Were Very Young"} on:click={() => handleBookClick("When We Were Very Young")}>
            Read poems about friendship and wonder in "When We Were Very Young".
        </button>
    </div>

    {#if choiceMade && !goNextButton}
        <button class="next" on:click={goToQuestion}>Next</button>
    {/if}
    {/if}



    {#if goNextButton}
        <BookDetails bookTitle={chosenBook} />
    {/if}


    <style>
        h2 {
            font-size: 18px;
        }
        /* Same styles as provided previously */
        button {
            font-size: 14px;
            padding: 8px 16px;
            border: 5px solid brown;
            border-radius: 10px;
            margin: 5px;
            cursor: pointer;
            width: 250px;
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