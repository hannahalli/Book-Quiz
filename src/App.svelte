<!-- App.svelte -->
<script>
    import { onMount } from 'svelte';
    import Question1 from './Question1.svelte'; // Import each question component
    import Question2 from './Question2.svelte';
    import Question0 from './Question0.svelte';
    // Import other question components here
  
    let currentQuestion = null;
    let recommendations = [];
  
    // Function to toggle between questions
    const toggleQuestion = () => {
      // Switch to the next question component
      if (currentQuestion === null) {
        currentQuestion = Question0;
      } else if (currentQuestion === Question1) {
        currentQuestion = Question2;
      } 
      // Add other cases for additional questions
  
      // If all questions are answered, calculate recommendations
      if (currentQuestion === null) {
        calculateRecommendations();
      }
    };
  
    // Function to calculate recommendations based on answers
    const calculateRecommendations = () => {
      // Add your logic to calculate recommendations based on answers
      recommendations = []; // Dummy array for now
    };
  </script>
  
  <div class="container">
    {#if !currentQuestion}
      <h1>Welcome to the Book Quiz!</h1>
      <p>Answer the questions to find your next great read.</p>
      <button on:click={toggleQuestion}>Start Quiz</button>
    {:else}
      <svelte:component this={currentQuestion} />
    {/if}
  </div>
  
  <style>
    /* Add your CSS styles here */
    .container {
        position: absolute;
        top: 100px; /* Adjust the top position as per your requirement */
        left: calc((1536px - 500px) / 2 + 270px); /* Adjust the left position as per your requirement */
        width: 270px; /* Increase width */
        height: 550px; /* Increase height */
        background-color: #FAEBD7; /* Set light brown background color */
        border: 8px solid #8B4513; /* Set dark brown border */
        padding: 20px;
        border-radius: 15px;
        /* overflow-y: auto; Enable scrolling if content overflows */
        z-index: 1; /* Ensure the container is above other elements */
        pointer-events: auto; /* Enable pointer events for the container */
        text-align: center; /* Center text horizontally */
        color: #8B4513; /* Set text color to dark brown */
        font-family: Chalkboard, sans-serif; /* Set font to Chalkduster */
    }
  
    h1 {
      font-size: 24px;
    }
  
    p {
      font-size: 18px;
      margin-bottom: 20px;
    }
  
    button {
      font-size: 18px;
      padding: 10px 20px;
      background-color: darkgreen;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  
    button:hover {
      background-color: green;
    }
  </style>
  
