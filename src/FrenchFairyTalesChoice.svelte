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

<h2>Embark on a French story adventure! Choisissez un conte à explorer!:</h2>

<div>
    <button class:selected={chosenBook === "Hansel et Gretel"} on:click={() => handleBookClick("Hansel et Gretel")}>
        Hansel and Gretel (Hansel et Gretel)
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Jacques et le Haricot Magique"} on:click={() => handleBookClick("Jacques et le Haricot Magique")}>
        Jack and the Beanstalk (Jacques et le Haricot Magique)
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Les Trois Petits Cochons"} on:click={() => handleBookClick("Les Trois Petits Cochons")}>
        The Three Little Pigs (Les Trois Petits Cochons)
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Boucle d'Or et Les Trois Ours"} on:click={() => handleBookClick("Boucle d'Or et Les Trois Ours")}>
        Goldilocks and the Three Bears (Boucle d'Or et Les Trois Ours)
    </button>
</div>
<div>
    <button class:selected={chosenBook === "Le Petit Chaperon Rouge"} on:click={() => handleBookClick("Le Petit Chaperon Rouge")}>
        Little Red Riding Hood (Le Petit Chaperon Rouge)
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
        width: 240px;
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
