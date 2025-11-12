import java.util.Scanner;

class ATM {
    private int pin = 1214;
    private int balance;
    

    public void pincheck() {
   Scanner sc = new Scanner ( System.in);
        System.out.println("Enter Your pin: ");
        int enteredpin = sc.nextInt();
        if (enteredpin != pin) {
            System.out.println("Invalid pin");
            pincheck();
        } else {
            menu();
        }
    }

    public void menu() {
        System.out.println("Enter your option " +
                "1: Check Amount " +
                "2: Amount Deposit " +
                "3: Amount Withdraw " +
                "4: Exit ");
                Scanner sc = new Scanner ( System.in); 
        int opt = sc.nextInt();
        switch (opt) {
            case 1:
                amountCheck();
                break;
            case 2:
                amountDeposit();
                break;
            case 3:
                withdraw();
                break;
            case 4:
                System.exit(0);
                break;
            default:
                System.out.println("Enter valid option");
                menu();
        }
    }

    public void amountCheck() {
        System.out.println("Balance: " + balance);
        menu();
    }

    public void amountDeposit() {
        Scanner sc = new Scanner (System.in );
        System.out.println("Enter Amount to deposit: ");
        int dept = sc.nextInt();
        balance = balance + dept;
        menu();
    }

    public void withdraw() {
        Scanner sc = new Scanner ( System.in );
        System.out.println("Enter amount to withdraw: ");
        int amount = sc.nextInt();
        if (amount > balance) {
            System.out.println("Insufficient balance");
            menu();
        } else {
            balance = balance - amount;
            menu();
        }
    }
}

public class ATMmachine {
    public static void main(String[] args) {
        ATM atm = new ATM();
        atm.pincheck();
}
}
