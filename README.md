# clicer.game
// Clicker Game Mechanics

// Character Selection
const characters = [{ name: 'Warrior', power: 1 }, { name: 'Mage', power: 2 }];
let selectedCharacter = characters[0];

function selectCharacter(index) {
    if(index >= 0 && index < characters.length) {
        selectedCharacter = characters[index];
        console.log(`Character selected: ${selectedCharacter.name}`);
    }
}

// Shop System
const shopItems = [
    { name: 'Power Upgrade', cost: 10 },
    { name: 'Speed Upgrade', cost: 20 }
];

let playerMoney = 50;

function buyItem(index) {
    if(index >= 0 && index < shopItems.length && playerMoney >= shopItems[index].cost) {
        playerMoney -= shopItems[index].cost;
        console.log(`Purchased: ${shopItems[index].name}`);
    } else {
        console.log('Not enough money or invalid item.');
    }
}

// Upgrades
let powerLevel = 1;

function upgradePower() {
    powerLevel += 1;
    console.log(`Power Level upgraded to: ${powerLevel}`);
}

// Statistics
let clicks = 0;

function clickButton() {
    clicks += selectedCharacter.power;
    console.log(`Total clicks: ${clicks}`);
}

// Sound Effects
const clickSound = new Audio('click.mp3');

function playClickSound() {
    clickSound.play();
}

// Save to LocalStorage
function saveGame() {
    localStorage.setItem('clicks', clicks);
    localStorage.setItem('money', playerMoney);
    localStorage.setItem('character', selectedCharacter.name);
}

function loadGame() {
    clicks = parseInt(localStorage.getItem('clicks')) || 0;
    playerMoney = parseInt(localStorage.getItem('money')) || 50;
    const characterName = localStorage.getItem('character');
    selectedCharacter = characters.find(c => c.name === characterName) || characters[0];
}

loadGame();

