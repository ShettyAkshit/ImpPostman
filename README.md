# Rust
// Import necessary modules from the standard library
use std::{io, path::Path};

// Import functions from the 'tasks' module
use crate::tasks::{add_task, done_task, list_task, remove_task};

// Main function, where the program starts
fn main() {
    // Define a mutable variable to store the user's command
    let mut command = String::new();
    
    // Prompt the user to enter a command
    println!("Enter command (add, list, done, remove)");
    
    // user ka input command from standard input dekhega
    io::stdin()
        .read_line(&mut command) // Read the input into 'command' variable
        .expect("Not able to read command"); // Handle any errors while reading input

    // File path to store tasks data
    let file_path = Path::new("tasks.json");

    // user ka dekhega to input command to perform corresponding action
    match command.trim() {
        "add" => add_task(file_path), // Call 'add_task' function if command is 'add'
        "list" => list_task(file_path), // Call 'list_task' function if command is 'list'
        "done" => done_task(file_path), // Call 'done_task' function if command is 'done'
        "remove" => remove_task(file_path), // Call 'remove_task' function if command is 'remove'
        _ => println!("unknown command"), // Print krega 'unknown command' if command is not recognized
    }
}


