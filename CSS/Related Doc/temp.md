```css
#MainContainer {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;  /* Allow the child containers to wrap */
    width: 100%;      /* Ensure it takes full width of the screen */
    height: auto;     /* Adjust height automatically */
    background-color: aqua;
}

.container {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    justify-items: center;
    background-color: rgb(39, 11, 224);
    width: 45%;       /* Default width for larger screens */
    height: auto;     /* Automatically adjust height based on content */
    gap: 2px;
    margin-bottom: 20px; /* Add some space between stacked containers */
}

.ToggleBtn {
    background-color: aliceblue;
    width: 100%; /* Make the toggle button take full width of the container */
    height: 100px;
    text-align: center;
    line-height: 100px; /* Center text vertically */
}

.topicCard {
    width: 100%;  /* Make topic cards take the full width of the container */
    height: 100px;
    margin: 10px 0;
    background-color: blueviolet;
    text-align: center;
    line-height: 100px; /* Center text vertically in topic cards */
}


```/* Adjust for smaller screens */
@media screen and (max-width: 1024px) {
    .container {
        width: 48%;  /* Make containers take up less space for medium screens */
    }
}

@media screen and (max-width: 768px) {
    .container {
        width: 100%; /* Stack containers on top of each other for small screens */
    }

    .ToggleBtn {
        width: 100%;  /* Ensure toggle button is responsive */
    }

    .topicCard {
        width: 100%;  /* Ensure topic cards are responsive */
    }
}
