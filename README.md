- 👋 Hi, I’m @ErickGrundir
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
ErickGrundir/ErickGrundir is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import random

class Player:
    def __init__(self, name):
        self.name = name
        self.resources = 100
        self.army_size = 0

    def attack(self, opponent):
        if self.army_size > opponent.army_size:
            victory = True
            loot = min(opponent.resources, random.randint(10, 30))
            self.resources += loot
            opponent.resources -= loot
        else:
            victory = False
            loss = min(self.resources, random.randint(10, 30))
            self.resources -= loss
            opponent.resources += loss

        return victory

def print_status(player1, player2):
    print(f"{player1.name}: Resources={player1.resources}, Army Size={player1.army_size}")
    print(f"{player2.name}: Resources={player2.resources}, Army Size={player2.army_size}")
    print()

def main():
    player1 = Player("Player 1")
    player2 = Player("Player 2")

    rounds = 5

    for round_num in range(1, rounds + 1):
        print(f"Round {round_num}")
        print_status(player1, player2)

        # Simulate player actions (for simplicity, random decisions)
        player1.army_size = random.randint(1, 20)
        player2.army_size = random.randint(1, 20)

        # Players attack each other
        result1 = player1.attack(player2)
        result2 = player2.attack(player1)

        if result1 and result2:
            print("Both players win!")
        elif result1:
            print(f"{player1.name} wins the round!")
        elif result2:
            print(f"{player2.name} wins the round!")
        else:
            print("No winner in this round.")

    print("\nFinal Results:")
    print_status(player1, player2)

if __name__ == "__main__":
    main()
