# Task-3-Java
import java.util.Scanner; 

  

class BankAccount { 

    private double balance; 

  

    public BankAccount(double initial_balance) { 

        this.balance = initial_balance; 

    } 

  

    public boolean deposit(double amount) { 

        if (amount > 0) { 

            this.balance += amount; 

            return true; 

        } else { 

            return false; 

        } 

    } 

  

    public boolean withdraw(double amount) { 

        if (0 < amount && amount <= this.balance) { 

            this.balance -= amount; 

            return true; 

        } else { 

            return false; 

        } 

    } 

  

    public double check_balance() { 

        return this.balance; 

    } 

} 

  

class ATM { 

    private BankAccount bank_account; 

  

    public ATM(BankAccount bank_account) { 

        this.bank_account = bank_account; 

    } 

  

    public void withdraw(double amount) { 

        if (this.bank_account.withdraw(amount)) { 

            System.out.println("Withdrawal successful. Current balance: " + this.bank_account.check_balance()); 

        } else { 

            System.out.println("Insufficient funds or invalid amount."); 

        } 

    } 

  

    public void deposit(double amount) { 

        if (this.bank_account.deposit(amount)) { 

            System.out.println("Deposit successful. Current balance: " + this.bank_account.check_balance()); 

        } else { 

            System.out.println("Invalid amount for deposit."); 

        } 

    } 

  

    public void check_balance() { 

        System.out.println("Current balance: " + this.bank_account.check_balance()); 

    } 

} 

  

public class Main { 

    public static void main(String[] args) { 

        Scanner scanner = new Scanner(System.in); 

        System.out.print("Enter initial balance: "); 

        double initial_balance = scanner.nextDouble(); 

        BankAccount account = new BankAccount(initial_balance); 

        ATM atm = new ATM(account); 

        while (true) { 

            System.out.println("\nATM Menu:"); 

            System.out.println("1. Withdraw"); 

            System.out.println("2. Deposit"); 

            System.out.println("3. Check Balance"); 

            System.out.println("4. Exit"); 

            System.out.print("Enter choice (1/2/3/4): "); 

            String choice = scanner.next(); 

            if (choice.equals("1")) { 

                System.out.print("Enter amount to withdraw: "); 

                double amount = scanner.nextDouble(); 

                atm.withdraw(amount); 

            } else if (choice.equals("2")) { 

                System.out.print("Enter amount to deposit: "); 

                double amount = scanner.nextDouble(); 

                atm.deposit(amount); 

            } else if (choice.equals("3")) { 

                atm.check_balance(); 

            } else if (choice.equals("4")) { 

                System.out.println("Thank you for using our ATM. Goodbye!"); 

                break; 

            } else { 

                System.out.println("Invalid choice. Please select again."); 

            } 

        } 

        scanner.close(); 

    } 

} 

 

 
