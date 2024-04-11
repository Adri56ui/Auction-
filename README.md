
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Football Player Auction</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="app">
        <!-- UI elements will be dynamically generated here -->
    </div>
    <script src="script.js"></script>
</body>
</html>
/* Styles for UI elements */
// Define player data with fake prices
const players = [
    { id: 1, name: "Player 1", price: 1000000 },
    { id: 2, name: "Player 2", price: 2000000 },
    { id: 3, name: "Player 3", price: 3000000 },
    // Add more players as needed
];

// Initialize user's budget
let userBudget = 900000000; // 900 million

// Function to render player list
function renderPlayers() {
    const app = document.getElementById('app');
    app.innerHTML = ''; // Clear previous content

    players.forEach(player => {
        const playerElement = document.createElement('div');
        playerElement.innerHTML = `
            <div>${player.name}</div>
            <div>Price: ${player.price}</div>
            <button onclick="buyPlayer(${player.id}, ${player.price})">Buy</button>
        `;
        app.appendChild(playerElement);
    });
}

// Function to buy a player
function buyPlayer(playerId, playerPrice) {
    if (userBudget >= playerPrice) {
        // Deduct player price from user's budget
        userBudget -= playerPrice;
        alert(`You bought Player ${playerId} for ${playerPrice}. Your remaining budget: ${userBudget}`);
        renderPlayers(); // Re-render player list
    } else {
        alert("You don't have enough money to buy this player.");
    }
}

// Initialize the game
renderPlayers();
