# Guessing_number
use std::io;
use std::cmp::Ordering;
use rand::Rng;

// #function run

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess:");

        let mut guess = String::new();
        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read user input");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Invalid input, please enter a valid number.");
                continue;
            }
        };

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Small number!"),
            Ordering::Greater => println!("Big number!"),
            Ordering::Equal => {
                println!("Yes Right Number!");
                break;
            }
        }
    }
}
