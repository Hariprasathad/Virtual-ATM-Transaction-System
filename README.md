# Virtual-ATM-Transaction-System
A secure web-based ATM simulation system that allows users to perform banking operations such as deposit, withdrawal, balance check, PIN change, and view transaction history. The system ensures authentication via PIN and stores data securely using a Flask backend and MySQL database.
in db
CREATE DATABASE atm_system;
USE atm_system;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    account_number VARCHAR(255) NOT NULL,
    pin VARCHAR(64) NOT NULL,
    balance FLOAT NOT NULL,
    email VARCHAR(255),
    transaction_history JSON,
    account_status ENUM('Active', 'Frozen', 'Closed') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    INDEX idx_account_number (account_number) -- Add this line to create an index
);
CREATE TABLE transactions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    account_number VARCHAR(255),
    type VARCHAR(255),
    amount DECIMAL(10, 2),
    time DATETIME,
    FOREIGN KEY (account_number) REFERENCES users(account_number)
);
