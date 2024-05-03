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
<h2>It looks like you are ready to prepare for thrilling adventures! Which story will you embark on?</h2>

<div>
  <button class:selected={chosenBook === "The Adventures of Robin Hood"} on:click={() => handleBookClick("The Adventures of Robin Hood")}>
      Join the legendary Robin Hood and his Merry Men in their fight for justice 
  </button>
</div>
<div>
  <button class:selected={chosenBook === "The Two Jungle Books"} on:click={() => handleBookClick("The Two Jungle Books")}>
      Swing through the jungle with Mowgli and encounter a cast of unforgettable animal
  </button>
</div>
<div>
  <button class:selected={chosenBook === "Peter Pan"} on:click={() => handleBookClick("Peter Pan")}>
      Fly away to Neverland with Peter Pan and the Lost Boys
  </button>
</div>
<div>
  <button class:selected={chosenBook === "The Story of King Arthur and His Knights"} on:click={() => handleBookClick("The Story of King Arthur and His Knights")}>
      Embark on a quest for honor and chivalry with King Arthur and his Knights of the Round Table
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
      font-size: 17px;
      
  }
  button {
      font-size: 16px;
      padding: 6px 15px;
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
