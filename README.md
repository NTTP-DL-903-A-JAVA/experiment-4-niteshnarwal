[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/0KLyNTCy)
import java.util.*;

// Class to represent a card with symbol and number
class Card {
    private char symbol;
    private int number;
    
    public Card(char symbol, int number) {
        this.symbol = symbol;
        this.number = number;
    }
    
    public char getSymbol() {
        return symbol;
    }
    
    public int getNumber() {
        return number;
    }
    
    @Override
    public String toString() {
        return symbol + " " + number;
    }
}

// Main class - ensure the filename matches this class name (CardCollection.java)
public class CardCollection {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Get number of cards from user
        System.out.print("Enter Number of Cards : ");
        int n = scanner.nextInt();
        
        // Map to store cards grouped by symbol
        Map<Character, List<Card>> cardMap = new TreeMap<>();
        
        // Collect card details from user
        for (int i = 1; i <= n; i++) {
            System.out.print("Enter card " + i + ": ");
            char symbol = scanner.next().charAt(0);
            int number = scanner.nextInt();
            
            Card card = new Card(symbol, number);
            
            // Add card to appropriate list in the map
            if (!cardMap.containsKey(symbol)) {
                cardMap.put(symbol, new ArrayList<>());
            }
            cardMap.get(symbol).add(card);
        }
        
        // Print distinct symbols in alphabetical order
        System.out.print("Distinct Symbols are : ");
        for (char symbol : cardMap.keySet()) {
            System.out.print(symbol + " ");
        }
        System.out.println();
        
        // Print details for each symbol
        for (char symbol : cardMap.keySet()) {
            System.out.println("Cards in " + symbol + " Symbol");
            
            List<Card> cards = cardMap.get(symbol);
            int sum = 0;
            
            // Print each card and calculate sum
            for (Card card : cards) {
                System.out.println(card);
                sum += card.getNumber();
            }
            
            // Print number of cards and sum
            System.out.println("Number of cards : " + cards.size());
            System.out.println("Sum of Numbers : " + sum);
        }
        
        scanner.close();
    }
}
